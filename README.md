# Neural-Net-TroubleShoot
Contains information gathered from different sources about trouble shooting NN training

## NaN for loss values during training 
It depends on the particular case, but in general following things could be tried. In my case, there were nan values in the processed input which was the cause.

* Add regularization to add l1 or l2 penalties to the weights. Otherwise, try a smaller l2 reg. i.e l2(0.001), or remove it if already exists.
* Try a smaller Dropout rate.
* Clip the gradients to prevent their explosion. For instance in Keras you could use clipnorm=1. or clipvalue=1. as parameters for your optimizer.
* Check validity of inputs (no NaNs or sometimes 0s). i.e df.isnull().any()
* Replace optimizer with Adam which is easier to handle. Sometimes also replacing sgd with rmsprop would help.
* Use RMSProp with heavy regularization to prevent gradient explosion.
* Try normalizing your data, or inspect your normalization process for any bad values introduced.
* Verify that you are using the right activation function (e.g. using a softmax instead of sigmoid for multiple class classification).
* Try to increase the batch size (e.g. 32 to 64 or 128) to increase the stability of your optimization.
* Try decreasing your learning rate.
* Check the size of your last batch which may be different from the batch size.

