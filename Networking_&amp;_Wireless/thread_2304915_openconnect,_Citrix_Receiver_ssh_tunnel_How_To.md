---
title: "openconnect, Citrix Receiver ssh tunnel How To?"
date: 2015-12-01
forum: Networking &amp; Wireless
---

### Post by Linux_cat on 2015-12-01
Morning all, 

Im currently working for a corporation that requires you to log into a Windows 7 VM desktop, via citrix to get any work done. These machines are not fit for development and changing things here could take years!. 

So im using openconnect to log into the network via a RSA secureID, with username pin and pass code, after which I download an ica file which I modify slightly to enable screen re-size and use citrix receiver (command wfica) to open and connect to the desktop machine. 

My question is, is there anyway that I can use the net connection of the remote citrix windows 7 desktop so that I can access all the environments on my local machine and be able to develop efficiently? Im guessing some sort of ssh tunnel but unsure how to implement it. 

Can anyone help?

---

### Post by hariprasad2 on 2015-12-11
Hello, I am afraid, that you need some support on the side of corporation. You need permission and it is needed to do some administration steps to enable you to access to your computer remotely. Than the easiest way is to use Free RDP on Linux. I suppose, that configure Citrix Receiver will be more complicated. But don§t know, I know it only on my side (as connector (guest), not on the side of connection point(host)).

---

