---
title: "[Solved]wifi not working brcm4328 issues with bcm4401"
date: 2016-09-23
forum: Networking &amp; Wireless
---

### Post by talmagal on 2016-09-23
Trying to get the wifi working on the latest version of Ubuntu. But nothing I try seems to work or I'm missing something obvious. 

 i know the laptop cant run eth and wlan at the same time and have gotten up to modprobe -r ssb/b44/ssb_uhd which got rid of the eth0 and should allow the plan to be setup but when I tried to get reinstall the driver from the sticky at top using Mobile web it installs fine but nothing shows up. I might be missing something small any help would be appreciated.

---

### Post by westie457 on 2016-09-23
Welcome to the Forums talmagal.

Have you tried the steps in this post? 

[https://ubuntuforums.org/showthread.php?t=2214110](https://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by talmagal on 2016-09-23
Tried the directions from fresh install and wifi not working. Know it has something to do with the ethernet messing with the wifi and ssb/b44. Ive got it running before but i cant remember as its been couple years since ive had to use any linux distro. Also back then had to compile the driver by hand to get it working but blacklisting never worked properly and had to do the workaround everytime i booted up back then.

My laptop is dell vostro 1700/1500(they run similar parts)
Used the guide to install firmware-b43-installer for my card.

My lspci -nn -d 14e4: for both ethernet and wifi cards are

14e4:170c (rev02)BCM4401-B0
14e4:4328(rev03)BCM4321

trying to get wlan working dont care if eth0 gets disabled.



Edit:
Got it finally for some reason the first time i unloaded b43 and reloaded didnt work at all. even after unloading ssb
Some how this time after unloading all modules i could find then reloading them one at a time it worked

```
lsmod | grep ssb
modprobe -r b43 b44 ssb_hcd
modprobe -r ssb
modprobe b43
modprobe b44
modprobe ssb_hcd
modprobe ssb
```

Got Ethernet working it seems as well havent tested it though

---

### Post by Hadaka on 2016-09-23
Hi, with a working wired connection to your router (B44) please open a terminal and do..
*Ignore any file not found do all 5 commands anyway.
```
sudo apt-get update
sudo apt-get remove --purge bcmwl-kernel-source
sudo rm /etc/modprobe.d/blacklist-bcm43.conf
sudo apt-get install firmware-b43-installer
sudo modprobe -v b43
```
remove wired connection,boot and test wireless.

*If you do not have physical access the router,please advise
so an alternate method can be used..
thanks.

---

### Post by Hadaka on 2016-09-23
Hi, I misread your last post and edit. Looks like you have it working now.
b44-b43 share the ssb  module, removing ssb was probably
causing you some issues. Glad you got it working, please take the time to
mark your thread solved.
thanks.

---

### Post by talmagal on 2016-09-23
> **Hadaka said:**
> Hi, I misread your last post and edit. Looks like you have it working now.
b44-b43 share the ssb  module, removing ssb was probably
causing you some issues. Glad you got it working, please take the time to
mark your thread solved.
thanks.
 thanks for the reply yea got it working after half day fiddling with it. Ssb was messing with it even after I unloaded b44/ssb .
My router I currently in a closet downstairs and my Ethernet port on my desktop pc is dead. 
I usually use a different flavor of linux (sidux/aptosid deviant based) but ended up on Ubuntu cause wouldn't have to download as many pkgs and the saving grace Ubuntu support ICS over Bluetooth so was able to download the driver using internet sharing from my phone. 
glad I didn't have to compile the broncos driver agn as usually most stock drivers didnt work properly for me.

---

