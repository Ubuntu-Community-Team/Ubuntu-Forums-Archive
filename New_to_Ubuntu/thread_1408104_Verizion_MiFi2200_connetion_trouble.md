---
title: "Verizion MiFi2200 connetion trouble"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by tjmarch on 2010-02-16
Need to install usb-modeswitch-data-20100203.tar.bz2 have file on desktop and extracted there now how do I install it. I am writing this post with one computer and trying to get the other to work with Verzion MiFi2200 mobile broadband. I have been using [http://ubuntuforums.org/showthread.php?t=1331660&highlight=usb-modeswitch](http://ubuntuforums.org/showthread.php?t=1331660&highlight=usb-modeswitch) post as a guide.

---

### Post by steveneddy on 2010-02-16
I use a Verizon Mifi device and **after setting it up on a Windows machine**, I simply connect to it wirelessly, as it was designed to operate.

If I need to plug it in to check IM's and other system messages and specs I simply fire up a VM with either Windows 7 or Vista and access it via the wired dongle. Otherwise it is just a small wireless router for my Linux desktop while on the road.

All I do is turn on the Mifi and start the laptop and I have instant internet.

What is this other software you are trying to install used for anyway? It looks like it is used for some other types of wireless dongles which I don't believe are needed for the Mifi device.

---

### Post by tjmarch on 2010-02-16
I am using mine as hotspot also on my new laptop running win7 and run VMware to load ubuntu and it works great. But I also have a older laptop without a wireless card that I have installed Xubuntu on as the only operating system so I can learn more about Lunix. And learn how to program with some of the free programs that are available. My new laptop I cannot afford to mess up because I use it for work. To see what I am trying to do goto the following link
[http://ubuntuforums.org/showthread.php?t=1331660&highlight=usb-modeswitch](http://ubuntuforums.org/showthread.php?t=1331660&highlight=usb-modeswitch)

---

### Post by tjmarch on 2010-02-16
Issue resolved just had to unmount device then it showed up in network manager as a device to us. Then it was just a matter of entering username and password then applie changes I am now connected. I have to do this everytime want to us device

---

### Post by steveneddy on 2010-02-16
For an older lappie without built in wireless or bluetooth there are some great USB sticks that are recognized by Ubuntu that would add a wireless connection, then you could use the Mifi from there. 

It's a long way around that I know, but it is another solution.

I'm glad that you got your device running.

You may ask someone to write you a scrpit to help you automate the mounting of the USB device when either plugged in or create it as a launcher in the panel to help ease the connectivity issues when trying to use your Mifi device.

Cheers

---

### Post by tjmarch on 2010-02-16
Actually I do have a Agere Wireless Compact Flash Card that I use with a IPAQ pda that worked in laptop with xp to connect to router at home. Pyheas22 member of forum has been helping me try to get it working in Xubuntu  thread, last page [http://ubuntuforums.org/showthread.php?p=8824895#post8824895 ]("http://ubuntuforums.org/showthread.php?p=8824895#post8824895")
I am waiting for a reply now

---

### Post by drew3739 on 2010-02-18
How Do you unmount? something is supposed to show up on the desktop when you plug it in the usb but nothing happens when I plug mine in. I see it show up in device manager but no icon for unmount/eject in there.

---

