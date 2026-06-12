---
title: "Philips Webcam not Working on Skype"
date: 2010-02-22
forum: New to Ubuntu
---

### Post by bungz on 2010-02-22
Hi, 

I have plugged in my Philips webcam to my Toshiba laptop. I have also installed Skype 2.1. However, my webcam doesn't show up when i try using skype for video chat. It shows blank on my little window and in my friend's window. 

Anybody can help? 

Bungz

Update: When i go to Webcam tab in Skype Options and  click on 'test video' i get greenish image. However, when i try skype calling, video option does not show up. Earlier on it showed up, but when i click on 'share video' my friend and i get blank screen for my video.

---

### Post by bungz on 2010-02-22
Issue sorted. [This]("https://help.ubuntu.com/community/Webcam#Skype") page helped. 

> **Before attempting any drivers installation**

 If your webcam is not one of the latest models and you get at least something as the picture (some garbled or green screen or statics) instead of the expected picture -- you already have the installed drivers. Still you'll have to reconfigure the launching of the application in which the problem is observed. 
Reason: The developers decided to change the way the drivers and cameras work: old drivers (before Ubuntu 8.10) had the code to decode the data received from the webcam, the new drivers (since 8.10) don't. instead they assume decoding it always done somewhere else. The applications which use the older assumptions have to be provided with the additional (compatibility and decoding) library. 
An example of the procedure needed to adjust launching one typical application with the described problem follows. 
 
**Skype**

 Go to main menu, System, Preferences, Menus: Applications, Internet, Items: Skype, Properties, and replace the Command with  

```
bash -c 'LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so skype'
```

---

