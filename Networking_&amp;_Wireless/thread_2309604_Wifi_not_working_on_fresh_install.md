---
title: "Wifi not working on fresh install"
date: 2016-01-12
forum: Networking &amp; Wireless
---

### Post by soupladyofficial on 2016-01-12
So I've just installed Ubuntu 14.04 on an HP stream. Everything's fine and dandy except the wifi doesn't work. It detects the network and it accepts the password but it just continues trying to connect over and over again and failing. Perhaps the drivers need to be updated? I don't know. I did rfkill list and the wireless card doesn't appear to be disabled. Unfortunately the laptop doesn't have an ethernet port, so it's currently impossible to connect it to the internet. Is there anyway I can download drivers onto a usb and install them that way?

Edit: Perhaps, since the wifi card *appears *to be working, it's worth mentioning that when I try to connect, the symbol flashes like it's connecting until a notification pops up that says "Disconnected", as if it had already connected... but it never had. Is it also a possibility that the router is refusing to connect to the the device?

---

### Post by Bucky Ball on 2016-01-12
*Thread moved to **Networking & Wireless**.*

Welcome. Yes, there may be a way of doing the download to USB thing, but you may not need to. First, open a terminal post the output of this between code tags (see last link in my signature):

```
sudo lshw -C network
```

Which Stream is it? 11, 13?

As the wireless is detecting and trying to connect, the wireless card itself is working. Are you absolutely positive you are inputting the correct details when a security key is required? Are you using this on your home, familiar network that is known to work with your other devices?

---

### Post by soupladyofficial on 2016-01-12
It's an 11.

The output is
```
 *-network               
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: wlan0
       version: 00
       serial: 48:e2:44:89:50:6b
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=3.19.0-25-generic firmware=N/A latency=0 link=no multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:1000(size=256) memory:91000000-91003fff


```

---

### Post by Bucky Ball on 2016-01-12
All good there. Try these two commands, from [here]("http://ubuntuforums.org/showthread.php?t=2286312&p=13318950&viewfull=1#post13318950"):

```
echo "options rtl8723be swenc=1 fwlps=0 ips=0" | sudo tee /etc/modprobe.d/rtl8723be.conf
sudo modprobe -v rtl8723be
```

Reboot. Could you also provide the output of this command, please:

```
uname -a
```

---

### Post by soupladyofficial on 2016-01-12
I did the first two and rebooted and nothing appears to have happened.

Output of the third command: 
```
Linux HP-Stream 3.19.0-25-generic #26~14.04.1-Ubuntu SMP Fri Jul 24 21:18:00 UTC 2015 i686 i686 i686 GNU/Linux
```

Edit: I've just seen that you've edited your original post. It is my home network and I'm quite positive the password is correct. In fact, it was connected to the same network an hour ago before I had installed ubuntu. It's brand new and came preinstalled with windows 10.

---

### Post by Bucky Ball on 2016-01-12
Try this:

```
echo "options rtl8723be fwlps=N ips=N" | sudo tee /etc/modprobe.d/rtl8723be.conf
```

Reboot and reconnect (thanks varunendra).

If nothing, [try this, post @2]("http://ubuntuforums.org/showthread.php?t=2220933&p=13023814&viewfull=1#post13023814").

---

### Post by soupladyofficial on 2016-01-12
I did that, and the only result was that the network no longer appeared in the menu.

The post from the other thread restored it to how it was before but it's still not working.

---

### Post by Bucky Ball on 2016-01-12
Got me for the moment. Hopefully one of the wireless experts will notice this in due course, but I have to head off for awhile. Will dig about some more later. 

You could dig around for 'rtl8723be ubuntu 14' or something like that in the meantime and see what comes up. Keep an eye on the date of the pages and don't go the ndiswrapper route. This card doesn't need that and ndiswrapper best avoided. 

The driver is there and seems to be part of the kernel already, so the card is working (and it comes on, identifies networks and tries to connect). The problem seems to be happening with a setting somewhere along the way. That's a clue.

---

### Post by soupladyofficial on 2016-01-12
Ok. Thank you for your help.

---

