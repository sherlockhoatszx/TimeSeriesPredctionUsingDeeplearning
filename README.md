# TimeSeriesPredctionUsingDeeplearning
Try to make Time Series Prediction with simple neurons network supported by Keras.

Thanks to a wonderful tutorial published by [machinlearningmaster](http://machinelearningmastery.com/time-series-prediction-with-deep-learning-in-python-with-keras/),The code(Time Series prediction with Keras-predictmorethan1time-Copy1.ipynb) I published was mainly copied from that. 

In that tutorial, the prediction time lenght is 1 time unit.The dataframe like this (Xt-2,Xt-1,Xt,Yt+1),Yt+1 is for prediction.For expample , i use the passed 4days data to predict the 5th day.

What I try to explore is that,I want to use the passed 4days data to predict the next 2 days'. 

So the notebook shows the steps what i try to do.

However! If you  look very carefully of the trainPredict data.

the first 3 array is:
array([[ 128.60112   ,  127.5030365 ],
       [ 121.16256714,  122.3662262 ],
       [ 144.46884155,  145.67802429]
       
the list inside [ 128.6,127.5 ] [121,2,122,3] does not like t+1 and t+2.  
**Instead,** It looks like 2 probaly prediction for 1 unit. 
What i means is  [128.6,127.5] doesn't mean t+1 and t+2 prediction, it most possibly mean 2 possible prediction for t+1.

**one output cell with 2dimension and 2 output cell with 1 dimension is different.**
The input dimension and the output dimension will be tricky for the NN. 

It seems i should redisgn a new neurons network.seq2seq ? distributedtime wraper were the tools on hand right now.
What your suggestion ? You can launch new issue and we discuss about it.

**11.15 update Solution**: Using keras time-distributed-Dense neurons structure, It performs acceptably to predict within 5 days. After 5days , the longer to predict, the lower accuracy. (CStimeSeries_TimeDistributed-step1shift24_LSTM-1115.ipynb)

An explicity explanation for the Timedistributed Dense is [here] (https://github.com/fchollet/keras/issues/1029)
