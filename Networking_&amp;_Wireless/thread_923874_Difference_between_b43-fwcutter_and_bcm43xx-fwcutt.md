---
title: "Difference between b43-fwcutter and bcm43xx-fwcutter?"
date: 2008-09-18
forum: Networking &amp; Wireless
---

### Post by dark_phantom on 2008-09-18
I have the first one installed and am having problems trying to get any speed above 11Mb to be stable.  It starts at 1Mb and for web browsing it's more then enough, it's when I try to connect to my other computers that I need a faster bitrate.  But when I set it to 54Mb or any other available speed it freezes up.

I'm wondering if using bcm43xx-fwcutter would make a difference, I have a BCM4306 802.11b/g Wireless LAN Controller.

---

### Post by Ayuthia on 2008-09-18
> **dark_phantom said:**
> I have the first one installed and am having problems trying to get any speed above 11Mb to be stable.  It starts at 1Mb and for web browsing it's more then enough, it's when I try to connect to my other computers that I need a faster bitrate.  But when I set it to 54Mb or any other available speed it freezes up.

I'm wondering if using bcm43xx-fwcutter would make a difference, I have a BCM4306 802.11b/g Wireless LAN Controller.

It might.  The bcm43xx driver is the depreciated driver, but some 4306 owners have liked the bcm43xx version better.  I think that there are some bugs that were found recently by the b43 developers and were fixed, but I am not for sure about where it is being patched.  

You can always try it out and see what happens.  You will need to blacklist the b43 and ssb modules (if you don't have a Broadcom 44XX series wired ethernet card) so that they don't conflict with the bcm43xx driver.  I am sure that you know this, but you will need to install bcm43xx-fwcutter also because the firmware for the bcm43xx driver is different than the b43.  You should not have to uninstall the b43-fwcutter though because it is just an application to cut the firmware needed for the b43 module.

---

### Post by dark_phantom on 2008-09-18
Thanks I will try and install the bcm43xx and yes I believe I have a bcm44xx.

---

### Post by Ayuthia on 2008-09-19
If you are not sure if you have a Broadcom wired ethernet card, you can do:
```
lshw -C network
```and see what driver your wired card is using.  If it says b44, you will need to do some extra steps to get the bcm43xx driver to work.  The ssb module does not play well with others.  Because of this, the b44 module has to be loaded after your Broadcom wireless card or else the wireless might not work.

If you want to test it out to see if it works, you can try the following:
```
sudo modprobe -r b43 b44 ssb bcm43xx
sudo modprobe bcm43xx
sudo modprobe b44
sudo ifconfig wlan0 up
```
I think that the bcm43xx module should come up with wlan0.  If it does not, you might need to try eth1.  This will only work for the current session.

---

