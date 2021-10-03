# Analyzing-Weight-Initialization-in-Neural-Networks
Every Deep Learning book/tutorial points out the fact that weight initialization is an important design choice when developing deep learning neural network models. The initialization step can be critical to the model's ultimate performance, and it requires the right method. <br>
In this repo, we show the impact of various weight initializations on the accuracy of our model. We train our model on MNIST dataset. <br>
We consider 7 types of weight intializations:
<ol>
  <li> <b>Constant</b>: All weights are initialized to 0. </li>
  <li> <b>GlorotNormal/ Xavier normal</b>: Values of the weights are sampled from a truncated normal distribution centred on 0 with stddev = sqrt(2 / (fan_in + fan_out)) where fan_in is the number of input units in the weight tensor and fan_out is the number of output units in the weight tensor. </li>
  <li> <b>HeNormal</b>: Values of the weights are sampled from a truncated normal distribution centred on 0 with stddev = sqrt(2 / fan_in) where fan_in is the number of input units in the weight tensor. </li>
  <li> <b>Standard Normal Distribution</b>: Values of the weights are sampled from a normal distribution centred on 0 with stddev = 1 . </li>
  <li> <b>GlorotUniform/ Xavier Uniform</b>: Values of the weights are sampled from a uniform distribution within [-limit, limit], where limit = sqrt(6 / (fan_in + fan_out)) (fan_in is the number of input units in the weight tensor and fan_out is the number of output units). </li>
  <li> <b>HeUniform</b>: Values of the weights are sampled from a uniform distribution within [-limit, limit], where limit = sqrt(6 / fan_in) (fan_in is the number of input units in the weight tensor). </li>
  <li> <b>Uniform(0,1)</b>: Values of the weights are sampled from a uniform distribution within [0, 1] . </li>
 </ol>
 
## Visualization
The model is evaluated using five-fold cross-validation. We plot the accuracies of the 5 folds for the 7 types of initialization as mentioned before.

<p align="left"> <img src="https://user-images.githubusercontent.com/41645324/135748773-25d50951-34e6-40cb-a0a9-9be6df5c38e2.png" > </p>

![image](https://user-images.githubusercontent.com/41645324/135748809-cae035be-9be6-4b4b-bd1d-e236cf9ca11e.png)

![image](https://user-images.githubusercontent.com/41645324/135748852-a0c3739e-8396-4436-abd3-8026acfc7396.png)

Next, we observe the average accuracy for each of these weight intializers.

![image](https://user-images.githubusercontent.com/41645324/135749080-357c4db3-12db-4adc-9fb1-da87245c943d.png)

## Conclusion
We observe that for MNIST dataset, the model performs worst for Constant, Random Uniform and Random Normal. For the other weight initializers, the model performs performs the best and the accuracies are more or less similar. This conforms to the literature that whenever weights are initialized to 0 , the training of the neural network stops as there is no change in gradient. <br>
One point to note is that this is not a generalized conclusion i.e. the results can be different for other datasets and other set of hyper- parameters. We have tried to show here the impact of the weight intializers under a set of standard hyper-parameters for MNIST dataset. The reader is encouraged to try these weight intializers on other datasets like ImageNet, Iris etc. <br>


