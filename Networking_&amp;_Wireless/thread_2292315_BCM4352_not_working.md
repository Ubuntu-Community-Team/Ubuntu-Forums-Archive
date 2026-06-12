---
title: "BCM4352 not working"
date: 2015-08-26
forum: Networking &amp; Wireless
---

### Post by chapita-torres on 2015-08-26
Hello everybody, here is my situation. I've a lenovo yoga 3, not the pro version, mine comes with the Broadcom BCM4352 card and I've been wanting to install ubuntu 14.04 lts, but as the title describes I can't get the wifi to work nor the bluetooth. I've been reading a lot of stuff about it online such as try installing the propietary driver via aditional drivers on a live usb. Bottom line I would like to get it working on a live usb before making a fresh start.

Tell me if you need more info.
Sorry for my english, it's not my first language.

---

### Post by Hadaka on 2015-08-27
hi, if you have a working wired connection then do..
```
sudo apt-get update
sudo apt-get install bcmwl-kernel-source
sudo modprobe wl
```

if you have no internet access then go here.
[http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568](http://askubuntu.com/questions/523458/unable-to-connect-to-any-wifi-in-ubuntu-14-04/523568#523568)
read #3

if you still have no access then post your wireless info text file from here..
[http://ubuntuforums.org/showthread.php?t=370108](http://ubuntuforums.org/showthread.php?t=370108)

---

### Post by chapita-torres on 2015-08-27
Sorry I didn't mention it earlier but I've no wired connection..
Hey, I tried what you said, no luck. Don't know if its relevant but it says hardware locked or something like that, like if it were locked via a switch. My laptop doesn't have one.
Another thing I realize today was that although I installed the driver via additional drivers or manually and the live usb is a persistant version it didn't save anything after reboot, don't know if after installing the drivers the card should start working immediately or a reboot is necesary so.. there is that.
I wanted to try the second post but I've no idea how to run the script, the link redirects me to a bunch of text. I tried saving as a .sh but couldn't make it work. I'm pretty sure I did something wrong.

---

