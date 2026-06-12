---
title: "Is my F5D7050 belkin wireless natively supported by Ununtu 8.10?"
date: 2008-11-08
forum: Networking &amp; Wireless
---

### Post by bastones on 2008-11-08
I'm not sure what version of the Belkin F5D7050 I have so I can't check it [here](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBelkin#USB) (if there is a way to find out please let me know). Is my BELKIN F5D7050 natively supported by Ubuntu 8.10?

---

### Post by Bondy_uk on 2008-11-08
First of all, on the back there should be a tiny white label (im talking millimeters in size) that has "verxxxxxxx"
Take the first digit in that number and thats your version :)

I may be wrong with 8.10 and someone might come along and correct me, but as far as I am aware no Belkin card can be supported in Linux due to way in which it is licensed. It uses the Broadcom chipset and I believe they use the excuse of 'security' to not allow the release of their schematics / third parties to develop drivers under linux/unix.

It was interesting to see your link because the card was not supported in 7.10!
I have got my F5D7050 v1 to work in Gutsy (7.10) using a neat little program called ndiswrapper. It basically uses your official windows drivers and there are various ways of doing this.


However, I came across something really neat when I was hunting on how to do it. You will need an Internet connection (wired I assume) to complete this...

Goto: System > Administration >  Synaptic Package Manager and enter your password.

Search for: "bcm43xx-fwcutter" and install.

This is a little program for the Broadcom chipset, which will automatically find and download the compatible windows driver for you!


You should be up + running in no time :D

---

### Post by Bondy_uk on 2008-11-08
If you still cant get it working, try reading here: [http://ubuntuforums.org/showthread.php?t=963978&page=16](http://ubuntuforums.org/showthread.php?t=963978&page=16)

---

### Post by ufuntoo on 2009-05-24
I realize there are multiple threads out there with this same problem for the belkin f5d7050.  I've been having problems with this usb wireless device in ubuntu for about 2 years now.  A big frustration is that it will occasionally work 'out of the box' as I have not done anything special (no ndiswrapper or anything) to get it working.  

I haven't narrowed down the root cause of the problem, but one issue is that the device is not enumerating on the usb bus properly.  If you do a shell command "dmesg | tail" you will probably see what I'm talking about.  It seems like there is some powering issues or an initialize command to the device is not working properly.  Anyways, I have found a workaround that has yet to fail for me.  I happened to have a small usb hub laying around from a trade show (one of the free trinkets differnt booths have).  I plugged the wireless device into the hub, then the hub into my computer and it works.  Maybe the hub does a better job of enumerating its sub network, I don't know.  But if you want a quick fix, get yourself a cheap usb hub (or try putting the device farther downstream on the bus like a keyboard or monitor usb slot)  Good luck, I know this is very frustrating.

---

