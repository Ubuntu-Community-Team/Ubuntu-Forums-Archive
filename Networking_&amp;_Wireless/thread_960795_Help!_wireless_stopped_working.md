---
title: "Help! wireless stopped working"
date: 2008-10-27
forum: Networking &amp; Wireless
---

### Post by tmixer215 on 2008-10-27
Ok so i just started with linux on tuesday for a small project. I installed my windows drivers with ndiswrapper and after that my wireless worked and all was good. Well the little update button popped up and said "new updates are availible" so i was like ok and downloaded and installed all important updates, restarted and then no wireless. when i right-click on the network button there is no wireless option. I still can edit my wireless networks. If i goto network settings there is no wireless option. Somebody please help me

---

### Post by NullHead on 2008-10-27
Please open a terminal, Accessories>Terminal, and type in this command: ```
sudo modprobe ndiswrapper
```put in your password when asked for it. If it tells you that ndiswrapper is already loaded, then we'll move from there. 

If nothing comes after you enter your password, than ndiswrapperr was loaded and all *should* be well. 

Did you follow any guides to help you with getting your wireless working the first time? If so, post the link here so I can see what you've done so far.

---

### Post by Crafty Kisses on 2008-10-27
What are the results of this command?
```
lshw -C network
```

---

### Post by tmixer215 on 2008-10-27
When i goto put in my password i can't type anything. i think i may have bigger issues

---

### Post by tmixer215 on 2008-10-27
This is what i get from lshw -C network

WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 88E8038 PCI-E Fast Ethernet Controller
       vendor: Marvell Technology Group Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 14
       serial: 00:e0:b8:b8:dc:5c
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=sky2 driverversion=1.20 firmware=N/A latency=0 module=sky2 multicast=yes
  *-network UNCLAIMED
       description: Network controller
       product: BCM94311MCG wlan mini-PCI
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:05:00.0
       version: 01
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0

---

### Post by NullHead on 2008-10-27
> **tmixer215 said:**
> When i goto put in my password i can't type anything. i think i may have bigger issues

That's a security feature. Nothing to be worried about. Type in your password from and press enter anyways. 

It won't show any **** or XXXX it'll just be blank.

---

### Post by tmixer215 on 2008-10-27
when i try to run 
```
sudo modprobe ndiswrapper
```
i dont get a password promt now

---

### Post by tmixer215 on 2008-10-27
ok i got the password promt and put in my password and nothing happened

---

### Post by NullHead on 2008-10-27
That's a good thing then. Can you connect to your wireless network after running that command?

---

### Post by tmixer215 on 2008-10-27
No i still don't even get a wireless option see screen shot attachment

---

### Post by tmixer215 on 2008-10-27
does anybody else have any ideas? please i don't want to go back to windows

---

### Post by tmixer215 on 2008-10-30
woot! i figured it out 
it was my own dumb mistake. I accidentally deleted the original firmware and driver for my broadcom wlan so the card was being recognized but was not able to be used.  What i did to fix it:
reinstall 8.04 
install ndiswrapper and your windows driver .inf file 
yay wireless works


Now if anyone can come up with the proprietary driver file from ubuntu that would be the easiest instead of reinstalling

---

