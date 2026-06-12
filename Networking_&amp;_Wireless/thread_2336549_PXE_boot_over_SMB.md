---
title: "PXE boot over SMB?"
date: 2016-09-09
forum: Networking &amp; Wireless
---

### Post by MrMe01 on 2016-09-09
Hi all,


I am trying to PXE boot over SMB instead of NFS. TL;DR, can it be done? If so, how?


For the rest of us who like to like the details, I am trying to build a workshop machine that can image machines, pull data off and do all that sort of stuff, using a network bootable 'instance' of Debian. The server is Ubuntu Server 14.04 LTS, running the Zentyal stack to give me DHCP and DNS as well as host the SMB shares. 


We're a Windows environment and as such, we have no real exposure to NFS share security. It's a bit of an unknown, plus it's impossible to log access. It's also something I don't want to have to deal with.


I have used this guide, [http://debianaddict.com/2012/06/19/diskless-debian-linux-booting-via-dhcppxenfstftp/](http://debianaddict.com/2012/06/19/diskless-debian-linux-booting-via-dhcppxenfstftp/) and it works, however I am dealing with personal data and I would like to keep the shares under reliable password protection, the TFTP server is invisible to anyone unless they're looking for it.


Doing some Google searches has led me to this, [https://www.plop.at/en/ploplinux/live/networkboot-linux.html#pxel31](https://www.plop.at/en/ploplinux/live/networkboot-linux.html#pxel31). I have merged the relevant details from this into /srv/tftp/pxelinux.cfg/default, like smbmount=//10.0.0.1/srv/pxeboot:USER:<> PASSWORD , however I cannot get past the root argument, and without that, it fails to boot and at this point, I don't know what root= should be for SMB booting.


I'm sure I have missed some details here, but this is my weekend project, so if you need any further information, please ask.

---

### Post by ppatrick on 2017-06-03
See lot of SMB (and HTTP) based PXE examples on Serva's website:
[https://www.vercot.com/~serva/an/NonWindowsPXE3.html](https://www.vercot.com/~serva/an/NonWindowsPXE3.html)

---

