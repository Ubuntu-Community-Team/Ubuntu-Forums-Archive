---
title: "Belkin 7050 usb wirless card does not work"
date: 2007-02-26
forum: Networking &amp; Wireless
---

### Post by kcmohan on 2007-02-26
Hi 
I am a newb to ubuntu linux. Recently, I downloaded 6.10 desktop linux and installed it on an old dell pentium II machine. I run a bekin 54g wirelss network and and am trying to connect the linux machine to it  by using belkin 54g  7050 usb card.  I can see that the card is recognized and I am able to configure it as wlan0. I specified a static ip address with a gateway as 192.168.2.1. However, I am not able to connect to the gateway or Internet. I have gone through all the trouble shooting steps including checking the routing table and could not find any errors. 

I notice that that the kernel 2.6.17-10 has ndiswrapper 1.22 loaded with the distribution but I can not check which driver it is using. In fact, when I type in ndiswraper it gives me an error message and does not recognize the command. 

How can I uninstall the old version of nidswrapper and load the new one in (I am hoping this will solve the problem).  I have the windows drivers for belkin 7050 copied to the linux directory.

Can any one help unravel this mystery and help me out please?

---

### Post by [L2G] Slapshot on 2007-02-27
Hey Kcmohan

Welcome to the forums . Can you go to the command line interface and type the following in lower case LSUSB. Then press return and check the output then copy and paste it in a reply here.
You can access the terminal here (Applications -> Accessories -> Terminal):

This is my code.

jacko@jacko-desktop:~$ lsusb
Bus 005 Device 004: ID 050d:705a Belkin Components
Bus 005 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 004: ID 045e:0040 Microsoft Corp. Wheel Mouse Optical
Bus 001 Device 001: ID 0000:0000
jacko@jacko-desktop:~$

You are looking for something similar to this. ID 050d:705a.

Then check this web page and follow the instructions for your particular chipset.

You can also use the file name from the Windows install to figure out which bit of the guide to use.

If you want to use the ndiswrapper with the windows drivers you'll need to copy the files .inf and .sys for ndiswrapper to work.

I would also suggest using the latest version of ndiswrapper. 1.22 is a bit old now. I'm using KDE desktop and I'm not sure how you get to synaptic or adept to search for the package in the repositories.

Link is

[http://opensource.bureau-cornavin.com/belkin/index.html]("http://opensource.bureau-cornavin.com/belkin/index.html")


Hope this helps
 Jacko

---

### Post by kcmohan on 2007-02-27
Thanks Jacko. Your link and suggestions worked. I am able to get Internet now through Belkin 7050 using rt73 native linux drivers from the web site you suggested. :) 

KC

---

### Post by [L2G] Slapshot on 2007-02-28
Excellent mate, excellent. I also run WEP encryption on mine and I believe that WPA is also possible.

Take care 

Jacko

---

### Post by yigal.weinstein on 2007-03-21
Yes I have wpa up, this is a 2 week old post but I thought I should comment on it any way.

---

