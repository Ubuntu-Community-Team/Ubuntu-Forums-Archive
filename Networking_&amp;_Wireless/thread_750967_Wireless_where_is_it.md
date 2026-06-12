---
title: "Wireless where is it?"
date: 2008-04-10
forum: Networking &amp; Wireless
---

### Post by wh33t on 2008-04-10
Hello community. I'm pretty sure I've set up my broadcom wireless unit correctly on my Acer laptop. But I don't see a fun easy little Wireless icon in my system tray. How do I get it to appear? I also don't see it auto connecting to my house network.

---

### Post by kutjara on 2008-04-10
> **wh33t said:**
> Hello community. I'm pretty sure I've set up my broadcom wireless unit correctly on my Acer laptop. But I don't see a fun easy little Wireless icon in my system tray. How do I get it to appear? I also don't see it auto connecting to my house network.

Can you provide a bit more detail about how you set up your card? Did Ubuntu set it up by default or did you use Ndiswrapper or Madwifi to get it working?

---

### Post by wh33t on 2008-04-10
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

I followed that guide.

---

### Post by kutjara on 2008-04-10
> **wh33t said:**
> [https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Gutsy)

I followed that guide.

I'm using a different card than you on my Acer Aspire 4315, but I found that I had to make an entry in the /etc/modules file so that Ubuntu knows to bring up the card every time I boot the machine. Without the command, I had to type modprobe ath_pci after each restart.

Assuming a similar problem is affecting you, you should edit /etc/modules:

sudo gedit /etc/modules

And then add "bcm43xx" (or whatever command you used with modprobe when you set up the card) on a new line at the end of whatever text is already in the file.

It shouldn't be necessary to do this since you already modprobed, but my card wouldn't work without it.

---

### Post by wh33t on 2008-04-10
Nevermind. I'm a fool. I thought it would get it's own network icon like it does in windows, but I see it shares the same network icon as the wired connection does. I was right clicking expecting to get some options. I get those options to come up if I 'left' click on it. Some of these simple things really needed to be added into those guides.

---

