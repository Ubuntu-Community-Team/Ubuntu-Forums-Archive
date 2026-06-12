---
title: "Network manager not detecting my wired connection, but it's there!"
date: 2008-04-17
forum: Networking &amp; Wireless
---

### Post by pspawn on 2008-04-17
I'll try to make this short but descriptive. The images on the post are in portuguese, but are here to illustrate what I mean.

I'm using Ubuntu 7.10, all security and recommended updates done. Core 2 Duo processor, Intel mother board, 2GB RAM.

A few days ago my onboard ethernet **went dead**. I bought a Braview PCI ethernet adapter. On windows, it is **working great**. On ubuntu, well... not.

First of all, the network-manager applet shows the icon with exclamation mark. When I point to it, it **"no network connection"**, as seen below.

[IMG]http://i20.photobucket.com/albums/b201/bighi/error1-1.png[/IMG]

If I click it, it says that **no network device** was detected.

[IMG]http://i20.photobucket.com/albums/b201/bighi/error2.png[/IMG]

But here is the weird thing... If I open manual connection, my network device is there! On roaming mode, it does not work at all. If i change it to DHCP, my network and internet works, but it still has that error icon on network-manager applet.

[IMG]http://i20.photobucket.com/albums/b201/bighi/error3.png[/IMG]

The weird icon with the exclamation mark is ugly, but internet was working, so I didn't bother with it. Now, I realized a few programs say that **I have no internet connection**. Wine-doors is one of them. It did not happen before.

I'm confused. Why is it saying I have no devices, when the device is right there on manual configuration? And why can't it find my network with roaming?

when using **lspci**:
01:01.0 Ethernet controller: Hangzhou Silan Microelectronics Co., Ltd. RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor (rev 01)

---

### Post by dca on 2008-04-17
Is the on-board (dead) ethernet disabled in your BIOS?

---

### Post by pspawn on 2008-04-17
Yes. On the first day, I thought the problem was because the onboard ethernet was still showing up as eth0, so I disabled it on my BIOS.

---

### Post by Iowan on 2008-04-17
Post results of **ifconfig -a** and contents of **/etc/network/interfaces** file.

---

### Post by pspawn on 2008-04-17
Here are the results of these two commands.

Nobody ever experienced this before?

---

### Post by Iowan on 2008-04-17
The **/etc/network/interfaces** file is showing setup for both NIC's.  You might delete (or just hash out #) the auto line for eth1.

---

### Post by pspawn on 2008-04-17
I did it. /etc/network/interfaces now is:

```
auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0
```

But **the problem persists**.

Edit: I have rebooted the system after the change.

---

### Post by madara on 2008-06-02
i have the same problem can any one help solve this problem ?

---

### Post by pspawn on 2008-06-02
I could not solve the problem. I ended up removing network-manager from my computer.

Firefox was still starting always at Offline Mode, so I had to tweak inside his internal config to make it never go to offline mode.

No one in this forum seems to be able to help us, so you just may say goodbye to network-manager.

---

