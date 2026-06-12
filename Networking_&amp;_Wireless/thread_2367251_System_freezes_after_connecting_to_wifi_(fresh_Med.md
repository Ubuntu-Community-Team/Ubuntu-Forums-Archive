---
title: "System freezes after connecting to wifi (fresh Mediatek driver install)"
date: 2017-07-27
forum: Networking &amp; Wireless
---

### Post by ollieron on 2017-07-27
Hello,

I previously had ubuntu 16.04 on my Asus X555L and followed these instructions [https://community.linuxmint.com/tutorial/view/1796](https://community.linuxmint.com/tutorial/view/1796) to install Mediatek MT7630E wireless driver. This worked no problem. However, when I switched to xubuntu I followed the same steps and come up with an error saying the required key not available, did a bit of digging and disabled secure boot. Followed the instructions again which was successful but when I tried to connect the system froze. After a hard restart the wifi option disappeared.

Very new to ubuntu/xubuntu and coding itself so apologies for the lack of info and slowness. Any help would be greatly appreciated, Cheers!

---

### Post by BenginM on 2017-07-27
Hiya , you may want to report the error & behaviour to the developer

[https://neurobin.org/projects/softwares/unix/MT7630E/](https://neurobin.org/projects/softwares/unix/MT7630E/)

 , and am not sure if this is the same driver/ developer's page :

[https://github.com/benjarobin/MT7630E](https://github.com/benjarobin/MT7630E)

---

### Post by ollieron on 2017-07-28
I shall give the developer a bell. I ended up reinstalling xubuntu 16.04 becuase I think I buggered something up by fiddling around aimlessly. Now I have tried 
sudo apt-get install git dkms build-essential
git clone [https://github.com/neurobin/MT7630E.git](https://github.com/neurobin/MT7630E.git)
cd MT7630E/
sudo make dkms

No freezing, but still no sign of a wifi option. Do you have any thoughts on this? I don't think there were any errors once installed, however I can't find history output from the terminal.
Cheers

---

### Post by praseodym on 2017-07-28
Please run

```
sudo chmod +x install
sudo ./install
```
instead of "sudo make dkms"

---

### Post by ollieron on 2017-07-29
Thanks for your help. It turned out to be a couple of lines of code that did not match my kernel version (4.4.0-83). After a fresh install of xubuntu and changing these lines before install, it works perfectly. If anyone else has this problem, here is the thread [https://github.com/neurobin/MT7630E/issues/68](https://github.com/neurobin/MT7630E/issues/68)

---

