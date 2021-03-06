## Courses

### Production ML Systems

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/ML-Systems.PNG](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/ML-Systems.PNG)
[https://developers.google.com/machine-learning/crash-course/production-ml-systems](https://developers.google.com/machine-learning/crash-course/production-ml-systems)

### Static vs Dynamic Training

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Static-Dynamic.PNG](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Static-Dynamic.PNG)
[https://developers.google.com/machine-learning/crash-course/static-vs-dynamic-training](https://developers.google.com/machine-learning/crash-course/static-vs-dynamic-training)

### Static vs Dynamic Inference

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Static-Dynamic-Inference.PNG](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Static-Dynamic-Inference.PNG)
[https://developers.google.com/machine-learning/crash-course/static-vs-dynamic-inference/](https://developers.google.com/machine-learning/crash-course/static-vs-dynamic-inference/)

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Static-Dynamic-Online-Inference.PNG](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Static-Dynamic-Online-Inference.PNG)

### Data Dependencies

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Input-Data.PNG](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Input-Data.PNG)
[https://developers.google.com/machine-learning/crash-course/data-dependencies](https://developers.google.com/machine-learning/crash-course/data-dependencies)

### Fairness

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Fairness.PNG](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Fairness.PNG)
[https://developers.google.com/machine-learning/crash-course/fairness/](https://developers.google.com/machine-learning/crash-course/fairness/)

#### Fairness: Types of Bias

- **Reporting Bias**

Reporting bias occurs when the frequency of events, properties, and/or outcomes captured in a data set does not accurately reflect their real-world frequency. This bias can arise because people tend to focus on documenting circumstances that are unusual or especially memorable, assuming that the ordinary can "go without saying." @Google

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/REPORTING-BIAS.png](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/REPORTING-BIAS.png)

**Case Study 1**

A mobile camera or digital camera is used as a shot gun detector to detect changes in speed of vehicles. In order to detect speed, the vehicle is detected first and then the amplitude of the image is calculated. 

**Reference Articles**

[Optical Flow Estimation] http://www.cs.toronto.edu/~fleet/research/Papers/flowChapter05.pdf

**Case Study 2**

A dashcam is fitted to vehicle inside and is used to detect mistakes in lane changing. In order to detect the motion, the vehicle is detected first and then the graph of the images in the video are evaluated. 

**Reference Articles**

[Perceived Stress Questionnaire on Driver] https://www.ncbi.nlm.nih.gov/pmc/articles/PMC5981243/ 

1. Problem Explanation: Capture of Frequency of Events

_Case Study 1: (Capture of Frequency of Events using threshold of Pixel values)_

[Vehicle Detection using OpenVINO](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/far_entrance.0.gif)

[Vehicle Detection using Optical Flow Estimation and Bounding Boxes](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/output_annotated_330.gif)

![https://github/com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Unnamed%20board.png](https://github/com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Unnamed%20board.png)

**In the above two example videos, the number of points inside each bounding box is evaluated over a set of frames. This gives us the above graph explained under Reporting Bias and marked on Frame 1633. **

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Bounding-Boxes-No-Participation-Bias.png](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Bounding-Boxes-No-Participation-Bias.png)

_Case Study 2: (Capture of Frequency of Events using PSQs)_

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/PSQ.png](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/PSQ.png)

**Automation Bias**

Automation bias is a tendency to favor results generated by automated systems over those generated by non-automated systems, irrespective of the error rates of each.

2. Problem Explanation: Video Inference

_Case Study 1 (Shot gun detector)_

[Vehicle Detection using OpenVINO](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/far_entrance.0.gif)

[Vehicle Detection using Optical Flow Estimation and Bounding Boxes](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/output_annotated_330.gif)

The above video is demonstrating optical flow detection within the bounding box images as you can see. The detected points are filtered over a threshold which emits data to be sent through an analysis pipeline. The Analysed data is used to determine the statistical parameters of the video.

So why does Automation Bias exist? Automation Bias exists when a piece of software with single original model can be used to determine the statistical properties which helps in optimization of the video characteristics.

**Selection Bias**

Selection Bias occurs if a data set's examples are chosen in a way that is not reflective of their real-world distribution. Selection Bias can take many different forms:

3. Problem Explanation: Evaluating a Graph

**Coverage bias**: Data is not selected in a representative fashion.

_Case Study 1: (Shot Gun Detector)_

[Correct]: Collect Order of Appearance of Nodes inside Shot Gun Detector by Confidence Intervals

[Wrong]: Do Particle Count from detected boxes over n frames without forming order of appearance of bounding boxes

 

[Correct]: Connect two adjacent frames using Order of Appearance Collected with correct threshold

[Wrong]: Do Particle Count over frames by choosing the wrong threshold of pixels

The particle count inside those bounding boxes are measured from Optical Flow Phase Based Methods. 

The data collected does not form a representative fashion but they are transformed into usable statistics.

```python

viz = pd.DataFrame(columns=['vehicle', 'count', 'frame', 'nodes'])
frame = 0
for n, t in zip(nodes, threshold):
    frame += 1
    map_n = list(map(lambda k: str(k), n))
    for i, j in zip(n, t):
        viz = viz.append({'vehicle': i, 'count': j, 'frame': frame, 'nodes': "-".join(map_n)}, ignore_index=True)

```

**Non-response Bias**: (or participation bias): Data ends up being unrepresentative due to participation gaps in the data-collection process.

_Case Study 1: (Shot Gun Detector)_

Participation Gaps can occur in vehicle detection because some bounding boxes may get undetected either due to Deep Learning error which is very unlikely to happen. The other reason is when the vehicles are moving sequentially, the bounding boxes switch the Confidence Intervals or Confidence Threshold implying they change their order of appearance in the detection. This introduces participation bias in detection of a particular vehicle from a set of vehicles.
Code to Explain the Bounding Box Detection:

Code to Explain the Bounding Box Detection:

```python

def draw_boxes(out_write_npy, zone, frame, result, args, width, height):
    for box in result[0][0]: # Output shape is 1x1x100x7
        conf = box[2]
        # comparison of confidence threshold
        if conf >= args.pt:
            xmin = int(box[3] * width)
            ymin = int(box[4] * height)
            xmax = int(box[5] * width)
            ymax = int(box[6] * height)
            # draw bounding box rectangles
            cv2.rectangle(frame, (xmin, ymin), (xmax, ymax), args.c, args.th)
            
    return frame

```

Code to show participation bias of bounding boxes:

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Unnamed%20board_1.png](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Unnamed%20board_1.png)

```python

# distance arrays to collect distances
dist = []
node_length = len(_input[0]) # initial node length referring to frame 0
nodes = [list(range(node_length))] # collected nodes, starts from node_length of first frame
# iterate up frame (n - 1)
for i in range(len(_input)-1):
    d = []
    # loop through a cycle of next frame and the current frame
    for k in range(len(_input[i+1])):
        for j in range(len(_input[i])):
            # norm of distances between each bounding box rectangles
            d.append(np.sqrt(np.sum(np.square(np.array(_input[i][j]) - np.array(_input[i+1][k])))/4))
    dist.append(d)
    n = np.zeros(len(_input[i+1])).astype(np.int64) # initialising the nodes to zeros to explore findability
    for k,x in enumerate(d):
        # a comparison of distance to its threshold which is assumed to be PI
        if (x <= np.pi):
            n[int(k/len(_input[i]))] = int(nodes[i][k%len(_input[i])])
        else:
            if (int(k/len(_input[i])) >= len(_input[i])):
                # increment the node_length to enable detection
                node_length += 1
                n[int(k/len(_input[i]))] = node_length - 1
    
    nodes.append(n.tolist())

```

**The above code results in nodes collected in a traffic. Such a bias can be avoided by introducing a Custom Layer to the deep learning model which results in a SoftMax detection. The Training of the model must be through constant validation because the SoftMax layers may need at least 2 dimensions of vectors.**

Code which has fixed the participation bias:

Solution 1: Custom Layer

```python

import numpy as np

def test_custom_layer(self):
        class Softmax(object):
            def __init__(self, params, blobs):
                self.xstart = 0
                self.xend = 0
                self.ystart = 0
                self.yend = 0
            # Our layer receives two inputs. We need to crop the first input blob
            # to match a shape of the second one (keeping batch size and number of channels)
            def getMemoryShapes(self, inputs):
                inputShape, targetShape = inputs[0], inputs[1]
                batchSize, numChannels = inputShape[0], inputShape[1]
                height, width = targetShape[2], targetShape[3]
                self.ystart = (inputShape[2] - targetShape[2]) // 2
                self.xstart = (inputShape[3] - targetShape[3]) // 2
                self.yend = self.ystart + height
                self.xend = self.xstart + width
                return [[batchSize, numChannels, height, width]]
            def forward(self, inputs):
                # uses cosh function in order to take a log of the function
                return [np.cosh(inputs[0][:,:,self.ystart:self.yend,self.xstart:self.xend])]

        cv.dnn_registerLayer('SoftmaxCaffe', Softmax)
        # layer proto definition
        proto = '''
        name: "LogSoftmax"
        input: "input"
        input_shape
        {
            dim: 1
            dim: 2
            dim: 5
            dim: 5
        }
        input: "roi"
        input_shape
        {
            dim: 1
            dim: 2
            dim: 3
            dim: 3
        }
        layer {
          name: "Softmax"
          type: "SoftmaxCaffe"
          bottom: "input"
          bottom: "roi"
          top: "conv_prob"
        }'''

        net = cv.dnn.readNetFromCaffe(bytearray(proto.encode()))
        for backend, target in self.dnnBackendsAndTargets:
            if backend != cv.dnn.DNN_BACKEND_OPENCV:
                continue

            printParams(backend, target)

            net.setPreferableBackend(backend)
            net.setPreferableTarget(target)
            src_shape = [1, 2, 5, 5]
            dst_shape = [1, 2, 3, 3]
            inp = np.arange(0, np.prod(src_shape), dtype=np.float32).reshape(src_shape)
            roi = np.empty(dst_shape, dtype=np.float32)
            net.setInput(inp, "input")
            net.setInput(roi, "roi")
            out = net.forward()
            ref = inp[:, :, 1:4, 1:4]
            normAssert(self, out, ref)

        cv.dnn_unregisterLayer('SoftmaxCaffe')

```

Solution 2: Eliminate the participation bias by connecting the nodes to the bounding boxes

Redraw the bounding boxes with the nodes matched with the bounding boxes

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Bounding-Boxes-With-Participation-Bias.png](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Bounding-Boxes-With-Participation-Bias.png)

**Sampling bias**: Proper randomization is not used during data collection.

In this experiment shown above, we consider samples of data from bounding boxes and not the entire data which makes us apply statistical tests to the data

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Vehicle-Viz-Table.PNG](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Vehicle-Viz-Table.PNG)

**Group Attribution Bias**

Group attribution bias is a tendency to generalize what is true of individuals to an entire group to which they belong. Two key manifestations of this bias are:

4. Problem Explanation: Weighing the Components

**In-group bias**: A preference for members of a group to which you also belong, or for characteristics that you also share.

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Group-Attribution-Bias-1.png](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/Group-Attribution-Bias-1.png)

Explained using Static DEA problem

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/DEA-problem.png](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/DEA-problem.png)

```python

s = cvx.Variable(service_data.values.shape[0])
p = cvx.Variable(privilege_data.values.shape[0])

service = cvx.matmul(s, service_data.values[:,0])
privilege = cvx.matmul(p, privilege_data.values[:,0])

# SPECTRUM
GAMMA_SHAPE=5e1
GAMMA_SCALE=1e25
NORMAL_CENTER=1e20
NORMAL_STD=5e19

dmu_s = np.random.gamma(GAMMA_SHAPE, GAMMA_SCALE, service_data.values.shape[0])
dmu_p = np.random.normal(NORMAL_CENTER, NORMAL_STD, privilege_data.values.shape[0])
# objective function
objective = cvx.Maximize(service)

# constraints
constraints = [cvx.matmul(s, dmu_s) - cvx.matmul(p, dmu_p) <= 0, privilege == 1, s >= 0, p >= 0]

# use cvxpy to solve the objective
problem = cvx.Problem(objective, constraints).solve(verbose=False, solver=cvx.SCS, max_iters=500)

```

The DEA problem is a highly Static Model which implies it produces the same output no matter what decision making units you provide it with but changes with the data supplied. 
Solution is:

[Characteristics You Share]: Either you need to scale your DMUs to very large or very small quantities which are not proximal to original DMUs

[Where You Belong]: Or, you will have to change the data entirely. 

 

**Out-group homogeneity bias**: A tendency to stereotype individual members of a group to which you do not belong, or to see their characteristics as more uniform.

This is a similar problem where you equalize the DMUs (Input and Output), the efficiency reduces to just a Sum. 

**Implicit Bias**

Implicit bias occurs when assumptions are made based on one's own mental models and personal experiences that do not necessarily apply more generally.

5. Problem Explanation: Comparison of Beliefs and Observations

**confirmation bias**: model builders unconsciously process data in ways that affirm pre-existing beliefs and hypotheses

**experimenter's bias**: model builder may actually keep training a model until it produces a result that aligns with their original hypothesis

![https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/IMPLICIT-BIAS.png](https://github.com/nscalo/ai-in-business/raw/main/Courses/Production-ML-Systems/IMPLICIT-BIAS.png)


#### Fairness: Identifying Bias

[https://developers.google.com/machine-learning/crash-course/fairness/identifying-bias](https://developers.google.com/machine-learning/crash-course/fairness/identifying-bias)

#### Fairness: Evaluating for Bias

[https://developers.google.com/machine-learning/crash-course/fairness/evaluating-for-bias](https://developers.google.com/machine-learning/crash-course/fairness/evaluating-for-bias)

[https://colab.research.google.com/github/google/eng-edu/blob/main/ml/cc/exercises/intro_to_ml_fairness.ipynb](https://colab.research.google.com/github/google/eng-edu/blob/main/ml/cc/exercises/intro_to_ml_fairness.ipynb)

