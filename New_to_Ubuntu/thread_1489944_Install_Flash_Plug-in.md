---
title: "Install Flash Plug-in"
date: 2010-05-21
forum: New to Ubuntu
---

### Post by robb4293 on 2010-05-21
I am new to Ubuntu. I am (gulp) a former Microsoftee and have used Windows for the past 15+ years. I have played with Ubuntu before once or twice but just to take a peak. 
 
So I have an old Dell Dimension server and I just installed 10.04 LTS. It took a bit of time but works ok. I went to YouTube but it requires the Flash plug-in. I have downloaded the RAM file but have no clue how to install it. I have the file sitting on my desktop currently. Can anyone help me to install this plug-in?
 
Thanks.

---

### Post by sydbat on 2010-05-21
Go into System > Administration > Synaptic and search for flash, then install it from there. This is the flash in the Ubuntu repository and should work fine with 10.04. Easy Peasey.

---

### Post by wojox on 2010-05-21
You could also install:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

For Flash, Java, and a bunch of codecs.

---

### Post by 2hot6ft2 on 2010-05-21
> **robb4293 said:**
> I am new to Ubuntu. I am (gulp) a former Microsoftee and have used Windows for the past 15+ years. I have played with Ubuntu before once or twice but just to take a peak. 
 
So I have an old Dell Dimension server and I just installed 10.04 LTS. It took a bit of time but works ok. I went to YouTube but it requires the Flash plug-in. I have downloaded the RAM file but have no clue how to install it. I have the file sitting on my desktop currently. Can anyone help me to install this plug-in?
 
Thanks.
RAM file to me is Real Audio Media which has nothing to do with flash.:confused:

[And to install Flash (the same as going to the adobe website) just click this link if using 9.04 or up, then on OK]("apt:adobe-flashplugin?channel=$distro-partner")

And welcome to the forum.

---

### Post by sydbat on 2010-05-21
> **wojox said:**
> You could also install:

```
sudo apt-get update && sudo apt-get install ubuntu-restricted-extras
```

For Flash, Java, and a bunch of codecs.This is way better than what I suggested. Do this instead. Really.

---

