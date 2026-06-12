---
title: "Broadcom 4313 Wireless Adaptor NOT RECOGNIZED"
date: 2011-07-08
forum: New to Ubuntu
---

### Post by gotgameg on 2011-07-08
Ubuntu doesn't recognizes my wireless adaptor.


I've installed ubuntu 11.04 on a virtual machine in vmware workstation, on a hp625 laptop with a Broadcom 4313 wireless adapter.

After i install it's drivers (broadcom-sta-source, broadcom-sta-common, bcmwl-kernel-source) with synaptic package manager, they are not listed in the additional drivers section, so i can't activate them. 

When i 
lsmod | grep wl

// it doens't show anything.

After:
sudo modprobe 
lsmod | grep wl

i get:

wl                   2642531   0
lib80211             14570   1   wl

after:
wl sudo iwlist scan

// i get:

lo        Interface doesn't support scanning. 
 eth0      Interface doesn't support scanning.

No wlan0, no wl, no NOTHING!! 

I have also reinstalled the drivers, and restarted but nothing. 

Any ideas? I've been going nuts these days trying to figure it out (im a complete linux noob).

---

### Post by coffeecat on 2011-07-08
Welcome to the forum!

Please clarify: you have Ubuntu 11.04 running as a virtual guest in VMWare workstation? And is the host operating system Windows?

I have very little experience of VMWare - only a brief tryout of VMWare Player - I use VirtualBox. In VirtualBox, the guest machine does not have direct access to the host machine hardware. It is presented with virtualised hardware. In the case of Ubuntu running virtually in a VirtualBox machine, it accesses the network through a virtualised ethernet port. The host OS controls the wireless adaptor and then forwards traffic to/from the virtual machine through the virtual ethernet connection. The guest machine "thinks" it is using a wired connection to the network.

I am sure this also happens with VMWare, but no doubt someone will correct me if I'm wrong. :) Which is why your wireless drivers are having no effect.

**EDIT**: by the way, in Natty/11.04 the BCM4313 card works out of the box with a new open source driver, so if you had been running Ubuntu natively there would have been no need to install the proprietary drivers. In fact, doing so can cause problems. Not that this matters, for the reasons above.

---

### Post by gotgameg on 2011-07-08
Yes, the host OS si Win7.

Ok, so there it's no problem at all. 

Thx!!

---

### Post by ejimex on 2011-07-08
The solution that worked for me was posted by kingargyle1, who recommended that I download [WiFi Radar]("http://wifi-radar.systemimager.org/"). Just seconds after I installed the program the Linksys adapter sprung to life. I popped in the network password, opened [Firefox]("http://www.cnet.com/firefox-3/"), and had my Gmail inbox open in no time.

---

### Post by coffeecat on 2011-07-08
> **gotgameg said:**
> 
Ok, so there it's no problem at all. 


Can you access the internet from Ubuntu? If you can, then everything is fine. If not, start a thread in the virtualisation forum:

[http://ubuntuforums.org/forumdisplay.php?f=308](http://ubuntuforums.org/forumdisplay.php?f=308)

... and someone familiar with VMWare Workstation should be able to help you.

---

### Post by gotgameg on 2011-07-08
I can connect to the internet with my ethernet connection (dial-up).

I have installed wifi-radar and it still doesn't recognize my adaptor.

---

