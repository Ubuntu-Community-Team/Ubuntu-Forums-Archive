---
title: "Connection problem after updating to 11.04 from 10.10"
date: 2011-05-05
forum: New to Ubuntu
---

### Post by ichihaifu on 2011-05-05
Everything worked fine for 2 days after the update, but since yesterday the connection hasnt been working correctly.
I recall installing some updates before this started happening.
The problem machine is Asus Aspire One D250 (mini-laptop, x32), Desktop is Windows 7 Ultimate (x64).
This only happens when using WLAN, but I'd like to stick using it.

Accurate problem:
After connecting to router the connection is stable for few minutes or until I try to copy files from the laptop to my desktop or try to start my minecraft server. Using Transmission on high speeds doesnt cause the connection drop.

When I updated to 11.04, I kept most of my settings untouched when prompted.

What should I do? :/

---

### Post by computerandu on 2011-05-05
> **ichihaifu said:**
> Everything worked fine for 2 days after the update, but since yesterday the connection hasnt been working correctly.
I recall installing some updates before this started happening.
The problem machine is Asus Aspire One D250 (mini-laptop, x32), Desktop is Windows 7 Ultimate (x64).
This only happens when using WLAN, but I'd like to stick using it.

Accurate problem:
After connecting to router the connection is stable for few minutes or until I try to copy files from the laptop to my desktop or try to start my minecraft server. Using Transmission on high speeds doesnt cause the connection drop.

When I updated to 11.04, I kept most of my settings untouched when prompted.

What should I do? :/



Would you provide more info like
The problem is with wired connection or wireless?
Whether you have no wireless connection at all?
You wireless connection is too slow in Ubuntu as comapred to Windows?

---

### Post by kermit2435 on 2011-05-05
Hi, I had similar problems with my Acer Aspire.  I had to download the latest version of 11.04 desktop edition as the netbook version just wouldn't work properly. I am running from a USB stick as my SSD is fried, but other than that I have the same setup as yoiurself.  I also had to remove the Mozilla Browser and reinstall before I could connect properly.  Hope this works for you?:D

---

### Post by ichihaifu on 2011-05-05
Sorry, I described the problem wrong.

The thing is, if I try to transfer files from my ubuntu machine to win7 the connection cuts off.
It doesnt happen with transmission, but does with Minecraft server startup.

The problem only happens when I use WLAN. And the WLAN works as long as I dont try to transfer files or run minecraft server.

---

### Post by ichihaifu on 2011-05-05
Anything?

---

### Post by Gr!MM^ on 2011-05-11
Hello there fine gentlemen. I was having the same problem a few days ago, after installing 11.04 my wireless connection's quality would drop significantly, as soon as I started Transmission or even when transferring files over SAMBA. 

Being forced to go back to 10.10 I started reading a lot of threads and noticed some of them were pointing to a kernel issue. Noticing that I tried using the 2.6.38 kernel on 10.10 and realized my connection was messed up again, just like it was back in 11.04.

As I kept researching the issue I noticed that the **rt2870sta** module was being replaced by the **rt2800usb** in the 2.6.38+ kernels.

So I decided to blacklist the unwanted modules in an effort to force the** rt2870sta** to load by default, since my USB Wireless dongle has a Ralink rt2870 chipset.

In ***/etc/modprobe.d/blacklist***
```
blacklist rt2800usb
blacklist rt2x00usb
```And my issue was solved, I'm currently using 11.04 while transfering some huge files over SAMBA.
Not sure if you guys are experiencing the same issue, if so, i hope this helps. :p

---

### Post by zoftware on 2011-05-11
Hello Gr!MM^,

I understand some of what you said. I have a new install of Ubuntu 11.04 for a friend. Both the wireless and wired networking have stopped functioning since the install. My notebook and desktop are sharing the same router with no problems.

Restarts, shutdowns, deleting, adding, and combinations thereof have made no difference.

I have been searching the Help, Forums, and Google for several hours.

Any simple instructions would be appreciated.

---

