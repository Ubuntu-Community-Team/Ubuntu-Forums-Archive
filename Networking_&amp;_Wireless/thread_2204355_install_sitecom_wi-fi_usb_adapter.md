---
title: "install sitecom wi-fi usb adapter"
date: 2014-02-08
forum: Networking &amp; Wireless
---

### Post by nmq on 2014-02-08
Hi, I'm running Ubuntu 12.04 LTS on a desktop. Tried to install a Wi Fi usb adaptor N300 WLA 2103 made by Sitecom. But the system does not recognize the device. Sitecom install CD that came with the device does not have a Linux driver. Sitecom has told me the device uses the Realtek RTL8192cu chipset and that drivers can be found at: [http://www.realtek.com.tw/downloads/searchView.aspx?keyword=RTL8192CU](http://www.realtek.com.tw/downloads/searchView.aspx?keyword=RTL8192CU).  

Given this info can anyone guide me on how to install the device on my system?

---

### Post by kurt18947 on 2014-02-08
I *think* the Realtek driver should work with 12.04, it's problematic beyond 12.10 the last I knew.  I use mostly 14.04 these days so haven't installed a RTL8192cu device in 12.04 for some time.  What I remember is download Realtek's driver and extract it.  For the purpose of this post, let's assume the Realtek software is extracted to the Desktop of an account with SUDO privileges.  This has to be done from a terminal AFAIK. First cd to Desktop and type 'ls'(lower case L).  You should see the extracted Realtek folder.  CD to it. type 'ls' again and you should see several folders and files.  One of them should be something like "install.sh".  Type the following:
```

sudo bash install (or sudo bash install.sh - I don't recall which)

```
and enter your password when prompted.  The install script should run and the adapter should come alive.

If this is not correct, I'd welcome any corrections.  I don't want to lead anyone astray.

---

### Post by praseodym on 2014-02-08
Hi,

install the driver via LAN according to this:

[http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107](http://forum.ubuntuusers.de/topic/wlan-stick-524440/3/#post-5638107)

13.04-version for 12.04, 12.10 and (surprise!) 13.04.

---

