---
title: "wl active but not responding?"
date: 2008-11-26
forum: Networking &amp; Wireless
---

### Post by Blaze637 on 2008-11-26
Hey everyone,
     I just installed ubuntu 8.10 and I would like to use the internet. I see the wl listed in the driver thingy as active, but I can't seem to connect to the internet. I also noticed that the Network tab wasn't in the System > Administration listing. Any help would be appreciated.

---

### Post by Ayuthia on 2008-11-26
> **Blaze637 said:**
> Hey everyone,
     I just installed ubuntu 8.10 and I would like to use the internet. I see the wl listed in the driver thingy as active, but I can't seem to connect to the internet. I also noticed that the Network tab wasn't in the System > Administration listing. Any help would be appreciated.

There should be a network icon in the panel where you should be able to click and connect.  Have you tried this yet?

---

### Post by Blaze637 on 2008-11-26
> **Ayuthia said:**
> There should be a network icon in the panel where you should be able to click and connect.  Have you tried this yet?

I think so, but i really have no idea what i'm doing, should I right or left click the icon. When I left click it, the only accessable option I have is edit vpn connection. when I right click it it only lets me edit connections.

---

### Post by scottmac112 on 2008-11-26
Try this in a terminal:

sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod wl
sudo modprobe wl
sudo rmmod b44

Does that solve it? You left-click on the network icon to connect to a network. And it might take a few seconds after the fifth line of code to work.

---

### Post by Blaze637 on 2008-11-26
> **scottmac112 said:**
> Try this in a terminal:

sudo rmmod b43
sudo rmmod b44
sudo rmmod ssb
sudo rmmod wl
sudo modprobe wl
sudo rmmod b44

Does that solve it? You left-click on the network icon to connect to a network. And it might take a few seconds after the fifth line of code to work.

Well, it helped a little. I have more options when I click the network icon now. I think I need to retrace my steps to make sure I didn't goof up somewhere in the help section.

Edit: HAHA! I was stupid and mistyped the sudo thing on two of five of the command lines, thanks scottmac112.

---

