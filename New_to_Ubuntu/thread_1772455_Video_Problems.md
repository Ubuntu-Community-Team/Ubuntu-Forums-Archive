---
title: "Video Problems"
date: 2011-05-31
forum: New to Ubuntu
---

### Post by ian19jam on 2011-05-31
I use Ubuntu 10.10 and I have had a lot of problems when using video on websites and even youtube. I don't know why but I just have a black screen and I am unable to watch; When I am on Media websites ie BBC or Daily telegraph as an example I am unable to see any of their media videos.

I am very amateur with computers so please can you explain clearly as to how I cam solve this problem. I do have the adobe 10 flash programme, including Gnome Media Player and Movie player.

Much appreciate some advice please.

---

### Post by seawolf167 on 2011-05-31
I would first check a couple things (you can open a terminal through Applications -> Accessories -> Terminal):

Have you installed the restricted extras package?

```
sudo apt-get install ubuntu-restricted-extras
```Check to make sure your install is up-to-date

```
sudo apt-get update
sudo apt-get upgrade
```Do you have video drivers installed for your video card?

System -> Administration -> Hardware Drivers -> Install the driver for your device

Check the Adobe Flash player plugin

```
sudo apt-get install adobe-flashplugin
```

---

### Post by ian19jam on 2011-06-01
Thank you for your response; sorry could not reply earlier as computer went down. Now up and running. Still problems with seeing videos. I tried all your recommendations except hardware drivers one as I don't understand. No idea what my device is so no idea how to install. Please kindly advise as to what I should do and in simple terms please!

---

### Post by seawolf167 on 2011-06-01
For hardware drivers - click System (at the top panel), select Administration, then select Hardware Drivers.

You should then be able to check to see if there are any hardware drivers available for your devices, if there are (especially for your graphics/video card, you'll want to install and activate them)

---

### Post by zipperback on 2011-06-01
You might want to check over the following page.

[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

- zipperback
:popcorn:

---

