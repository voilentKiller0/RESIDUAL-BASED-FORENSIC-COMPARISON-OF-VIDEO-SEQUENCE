# RESIDUAL-BASED FORENSIC COMPARISON OF VIDEO SEQUENCE


In this project implements research paper of RESIDUAL-BASED FORENSIC COMPARISON OF VIDEO SEQUENCE 
Link - https://faui1-files.informatik.uni-erlangen.de/public/publications/mmsec/2017-Mullan-RBF.pdf

1. Read original and tempered videos
```
orig_frame = frameCapture("Original.avi")
temp_frame = frameCapture("Tempered_1.avi")

```

2. Compute Statistical Descriptor of both videos
```
rhist, chist = computeStatisticalDescriptor(orig_frame)
trhist,tchist = computeStatisticalDescriptor(temp_frame)
```

3. Compute Optical flow of both video and then compute original histogram
```
mag,ang = opticalFlow(orig_frame)
mag,ang = normalize(mag,ang)
ohist = computeMagAngle(mag,ang)

tmag,tang = opticalFlow(temp_frame)
tmag,tang = normalize(tmag,tang)
tohist = computeMagAngle(tmag,tang)
```

4. Compute Final histogram of both videos by row, column and temproral direcction.
```
fhist = computeFinalhistogram(rhist,chist,ohist)
tfhist = computeFinalhistogram(trhist,tchist,tohist)
```

5. Finally compute Mahalanobis distance of two videos.

