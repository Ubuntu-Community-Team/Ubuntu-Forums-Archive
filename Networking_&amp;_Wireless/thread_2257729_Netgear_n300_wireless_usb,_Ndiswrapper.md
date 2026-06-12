---
title: "Netgear n300 wireless usb, Ndiswrapper"
date: 2014-12-22
forum: Networking &amp; Wireless
---

### Post by jimmie2 on 2014-12-22
I installed Ubuntu on my computer tonight only to find out that the netgear n300 wireless usb adapter I has only windows drivers. So I learned that I needed to download ndiswrapper and ndgstk so I downloaded them on my win 7 laptop put them on a usb drive and transferred them to the ubuntu desktop. Here Is where I hit a wall. I cannot for the life of me find out how to place these files where they need to be. I have read the instructions over and over and over and they make no sense to me. I have tried to copy and paste them to /usr/bin but I got nothing put permission denieds then I tried right click move then moving the windows driver and the ndiswrapper to /usr/bin can't again! I have no experience with ubuntu nor any linux distributions and command prompts that I have tried to mv ~<ndiswrapper 1.59> /usr/bin I get a no such fie no such directories. So I feel like such an idiot and I imagine there is an easier way please help!

---

### Post by praseodym on 2014-12-22
Hi,

do you have a wired connection? If yes, please run
```

sudo apt-get install ndisgtk ndiswrapper-dkms build-essential linux-headers-generic
```
If no, please show the terminal outputs of
```

lsusb
uname -a
```
Did you download the DEB files?

---

