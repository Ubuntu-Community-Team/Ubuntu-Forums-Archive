---
title: "disable ati driver from shell"
date: 2009-04-02
forum: New to Ubuntu
---

### Post by ozbolt on 2009-04-02
When updating to 9.04 Beta I didn't care for warnings that new X and ATI might not be good with each other. So now I have to disable the propiratery (miss spelled probably) and activate open source one so that system will work.
And if I can just update the system and it should work, I still have to connect to my wireless card and establish the conection and than apt-get. 

If you need any more informations please ask (I heard that you don't like to help if I don't specify the problem to details).

---

### Post by zika on 2009-04-02
problem: what I have to offer requires network ...
if You can not get to network ... sorry ... if it were wired I could have helped.
(do not follow my advice if You are unsure what You are doing ...)
in Terminal:
```
sudo apt-get update
sudo /usr/share/ati/fglrx_unistall.sh (I might made a typo here, do not have that file any more)
sudo apt-get remove --purge fglrx*
sudo apt-get remove --purge xserver-xorg-video-ati
sudo apt-get remove --purge xserver-xorg-video-radeon
sudo apt-get install xserver-xorg-video-ati
sudo apt-get install xserver-xorg-video-radeon
sudo apt-get install --reinstall libgl1-mesa-glx
sudo apt-get install --reinstall libgl1-mesa-dri
sudo dpkg-reconfigure -phigh xserver-xorg
sudo apt-get upgrade
```

---

