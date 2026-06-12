---
title: "Install OpenCV Ubuntu 10.10"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by delioj on 2011-02-09
Hello guys,

I am new to ubuntu and I need to install openCV for one of my courses. I am trying to follow the instructions from here:

[https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV)

and it doesn't work. I try the following line and I get the following:


root@User-PC:~/examples/c/c# sudo apt-get install libcv4 libcvaux4 libhighgui4 python-opencv opencv-doc libcv-dev libcvaux-dev libhighgui-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package libcv4
E: Unable to locate package libcvaux4
E: Unable to locate package libhighgui4

Can anybody help me why it's not working? Any help is appreciated.

---

### Post by lykeion on 2011-02-09
The Ubuntu Doc page you refer to hasn't been updated but in Ubuntu 10.10 you can install OpenCV simply with:
```
sudo apt-get install opencv
```

---

### Post by delioj on 2011-02-09
Hi lykeion,

Thank you for your response. Is there any documentation that you know on how to install and use this library. I will try to do what you suggested but my next question would be how to run an example using the library. I know some of the websites that explains how to install it run an example to make sure that it works. Do you have any suggestions?

Thanks again,

---

### Post by lykeion on 2011-02-09
I can't give you anymore than the usual: Search Google, look up [Wikipedia]("http://en.wikipedia.org/wiki/Opencv"), and of course the [official homepage]("http://opencv.willowgarage.com/wiki/") of OpenCV.

---

