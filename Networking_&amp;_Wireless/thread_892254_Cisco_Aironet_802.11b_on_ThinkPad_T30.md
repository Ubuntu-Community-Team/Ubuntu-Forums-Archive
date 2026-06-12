---
title: "Cisco Aironet 802.11b on ThinkPad T30"
date: 2008-08-17
forum: Networking &amp; Wireless
---

### Post by Zylog on 2008-08-17
Hi.

I just installed ubuntu on the IBM thinkpad t30.

I tried getting everything to work but it seems the WiFi still is not recognized as well as the sound (No volume control or GStreamer found...)
I am new to linux and I have no idea of getting this to work.  I looked around but only came to posts where 'everything worked fine the first time'.

Thanks!

---

### Post by Zylog on 2008-08-17
&#1072;&#1087;

---

### Post by IndyGunFreak on 2008-08-17
Post the output of lspci so we can see your sound device, but this should get your wireless working(I'm assuming you're using 32bit, I don't know if this works or not on 64bit):

In a terminal:
```
 gksudo gedit /etc/modprobe.d/blacklist
```

and add these two lines to the end of the file...
blacklist padlock_aes
blacklist geode_aes

IGF

---

### Post by twofish on 2008-09-03
Any luck with this?  

I don't know if it matters or not, but I have a T30 as well, and the wifi worked out of the box.  I can't remember, though, if I had to bring it up first or not.

ifconfig wlan0 up

---

### Post by cap996 on 2008-09-07
I have the same problem, no sound and no wireless working.
there should be a kind of conflict since I removed the Aironet pci card and sound is working.

bye.

---

