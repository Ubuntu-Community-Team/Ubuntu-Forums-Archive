---
title: "[SOLVED] Deleted wireless"
date: 2007-06-27
forum: Networking &amp; Wireless
---

### Post by arashiko28 on 2007-06-27
While following some instructions to install the bcm43xx driver for my bcm4306 wireless card. Can't imagine what i did wrong, if i even printed the steps and followed then word by word. At end had to restart and supposedly the wireless led should have turned on, it didn't I wasn't worried, since it has never turned on using linux. But when i went to network settings to choose the connection, the wireless network, that was there before, is now gone.:( Help!!!

---

### Post by spd106 on 2007-06-27
It would be nice if you could post a link to the guide that you followed as there are so many of them around the forum/wiki.

Try this command to identify the interface and it's details.
```
sudo lshw -class network
```

If there is no mention of the bcm43xx driver run this command to see if the driver is currently loaded.
```
lsmod | grep bcm43xx
```

If there was no output try loading the driver with this command.
```
sudo modprobe bcm43xx
```

If it's still not working then post the results back here and maybe try following the guide through again.

---

### Post by arashiko28 on 2007-07-01
Sorry I didn't answered earlier, too busy with exams. The problem was that the instructions said to blacklist the bcm43xx, when i removed that, i can see the wireless again on the network manager. My problem keeps resuming to one thing, the bcm4306 driver. None of the ones that i have found, works. even when i get this answer with the ndiswrapper -l:
ndiswrapper -l
bcmwl5 : driver installed
        device (14E4:4320) present (alternate driver: bcm43xx)

This is what i got from the sudo lshw -class network:
sudo lshw -class network
  *-network DISABLED      
       description: Wireless interface
       product: BCM4306 802.11b/g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: 6
       bus info: pci@02:06.0
       logical name: eth0
       version: 03
       serial: 00:90:4b:ae:c4:a1
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.20-16-generic latency=64 link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:e0204000-e0205fff irq:20

and the grep:
lsmod | grep bcm43xx
bcm43xx               126824  0 
ieee80211softmac       31360  1 bcm43xx
ieee80211              34760  2 bcm43xx,ieee80211softmac

---

### Post by spd106 on 2007-07-01
Well the interface is there and it appears to have loaded the bcm43xx driver, it just needs to be activated. This used to be done by the ifup scripts or by issuing ifconfig eth0 up.

Are you using roaming mode or static mode in Network Manager? Check that wireless is enabled by right-clicking nm-applet in the notification area. If you are using static then make sure there is a 'auto eth0' line in the /etc/network/interfaces file.

---

### Post by Ayuthia on 2007-07-01
By any chance, did you add bcm43xx to /etc/modprobe.d/blacklist?  I don't think that bcm43xx is supposed to be showing under lsmod.

---

### Post by arashiko28 on 2007-07-02
I forgot about the ndiswrapper, and found a better way, even got it turned on the wireless leds! but, after i restarted the computer, the wireless option dissapeared, i went to the blakclist, but it is not blacklisted. I followed the howto bcm43xx easy way o something like that...

---

### Post by Ayuthia on 2007-07-02
From what I understand, you switched to bcm43xx-fwcutter and now wireless does not work when you restart your computer.  If that is the case, you might want to make sure that you have removed ndiswrapper:
sudo rmmod ndiswrapper
sudo ndisrapper -e bcmwl5

also make sure that the ndiswrapper entry is not in /etc/modules.  You will probably have to reboot after that.

You can verify if ndiswrapper is running by using lsmod.  If all is running right (and you are using bcm43xx-fwcutter), you should bcm43xx in there and ndiswrapper should not be in there.

---

### Post by arashiko28 on 2007-07-03
What I did was follow this istructions, given by Darkn00b: [http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990), now, it does works, but it seems that i have to install it every time i'm going to use it 8-[

---

### Post by Ayuthia on 2007-07-03
Do you have bcm43xx blacklisted in /etc/modprobe.d/blacklist?  If you type:
cat /etc/modprobe.d/blacklist
It should not be in there.  If it is, you will need to edit the file and take it out.  His script is copying the missing firmware into the firmware directory and then it adds to module to the system (via modprobe) which basically activates your wireless.

---

### Post by arashiko28 on 2007-07-09
It was not blacklisted, apparently i need to reinstall the firmware everytime i turn on the wireless.

---

