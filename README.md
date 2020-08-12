# Sanjay41
## Technical presentation
## Canny Edge Detector

Theory
The Canny Edge detector was developed by John F. Canny in 1986. Also known to many as the optimal detector, the Canny algorithm aims to satisfy three main criteria:
•	Low error rate: Meaning a good detection of only existent edges.
•	Good localization: The distance between edge pixels detected and real edge pixels have to be minimized.
•	Minimal response: Only one detector response per edge.
Steps
1.	Filter out any noise. The Gaussian filter is used for this purpose. An example of a Gaussian kernel of size=5 that might be used is shown below:
K=1159⎡⎣⎢⎢⎢⎢⎢⎢245424912945121512549129424542⎤⎦⎥⎥⎥⎥⎥⎥
2.	Find the intensity gradient of the image. For this, we follow a procedure analogous to Sobel:
a.	Apply a pair of convolution masks (in x and y directions:
Gx=⎡⎣⎢−1−2−1000+1+2+1⎤⎦⎥
Gy=⎡⎣⎢−10+1−20+2−10+1⎤⎦⎥
b.	Find the gradient strength and direction with:
G=G2x+G2y−−−−−−−√θ=arctan(GyGx)
The direction is rounded to one of four possible angles (namely 0, 45, 90 or 135)
3.	Non-maximum suppression is applied. This removes pixels that are not considered to be part of an edge. Hence, only thin lines (candidate edges) will remain.
4.	Hysteresis: The final step. Canny does use two thresholds (upper and lower):
a.	If a pixel gradient is higher than the upper threshold, the pixel is accepted as an edge
b.	If a pixel gradient value is below the lower threshold, then it is rejected.
c.	If the pixel gradient is between the two thresholds, then it will be accepted only if it is connected to a pixel that is above the upper threshold.
