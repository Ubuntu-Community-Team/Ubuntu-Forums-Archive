---
title: "Issues installing NDISwrapper"
date: 2008-08-07
forum: Networking &amp; Wireless
---

### Post by RickyLightning on 2008-08-07
What am I doing wrong?

home@home-desktop:~$ sudo apt-get install ndisgtk_0.8.3-1_i386.man
Reading package lists... Done
Building dependency tree
Reading state information... 
E: Couldn't find package ndisgtk_0.8.3-1_i386.man
home@home-desktop:~$

The file ndisgtk_0.8.3-1_i386.man is located on my Desktop. I am very unexperienced with this stuff, I've only been with Ubuntu (HH 8.04) for about 2 days. I'm trying to make my Linksys PCI WMP54G card work. The card finds the network, but never can connect. The computer just prompts me for the WEP, which I input and a couple minutes later it prompts again.

---

### Post by RickyLightning on 2008-08-07
bump..

It's been 3 hours, doesn't anyone have anything to say about my probelm?

---

### Post by Ayuthia on 2008-08-07
> **RickyLightning said:**
> What am I doing wrong?

home@home-desktop:~$ sudo apt-get install ndisgtk_0.8.3-1_i386.man
Reading package lists... Done
Building dependency tree
Reading state information... 
E: Couldn't find package ndisgtk_0.8.3-1_i386.man
home@home-desktop:~$

The file ndisgtk_0.8.3-1_i386.man is located on my Desktop. I am very unexperienced with this stuff, I've only been with Ubuntu (HH 8.04) for about 2 days. I'm trying to make my Linksys PCI WMP54G card work. The card finds the network, but never can connect. The computer just prompts me for the WEP, which I input and a couple minutes later it prompts again.

Are you sure that it is ndisgtk_0.8.3-1_i386.man?  Usually the packages are labeled with a .deb extension.  If it is a .deb file, then you will need to use dpkg:```
sudo dpkg -i ndisgtk_0.8.3-1_i386.deb
```. 

I was thinking that ndisgtk was included in the install CD.  I could be wrong though.  You should be able to install it by adding the CD (if you haven't already):
```
sudo apt-cdrom add
```Insert the Live CD then:
```
sudo apt-get update
sudo apt-get install ndisgtk
```

---

