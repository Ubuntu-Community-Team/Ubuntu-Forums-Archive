---
title: "Xbox 360 controller not working &gt;&lt;!"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by ibe2fly4chu on 2010-06-18
Trying to get this xbox360 wired controller working for ffxi. On ubuntu 10.4...i have it installed and it is recognized by the computer. The thing is the right analog and lt buttons are being read as axises. Anyone know a fix?

---

### Post by enjoijesus94 on 2011-11-28
Hello 
Ok to get this to work you have to get the right packages 

1.open a terminal shell and type 
sudo add-apt-repository ppa:grumbel/ppa

2.Then Do a Update 
sudo apt-get update

3.now we are going to install xboxdrv
sudo apt-get install xboxdrv

4.Now for the stable version of xboxdrv
sudo apt-get install xboxdrv-stable

5.NOW!!!!! finally we type 
"sudo su"
then 
"rmmod xpad" so we dont run into that pesky error

And Now we want to run our mouse 
xboxdrv --mouse

And there you go "A BRAND NEW STINKEN MOUSE"

if you run into any errors just tell me ill try my best to help:popcorn:

---

