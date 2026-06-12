---
title: "Problem with Broadcom 4313 Wireless Lan Chip"
date: 2015-05-11
forum: Networking &amp; Wireless
---

### Post by Paul_Palm on 2015-05-11
Hello you guys and girls

I am relatively new to Linux (aside from running a XBMC Raspberry Pi media center) and I decided to wipe Windows from my old Laptop and install Ubuntu. Everything works like a charm except the WLAN, during installation it worked just fine but since starting the system up normally for the first time it can't yonnect (I see the networks though). I started with 14.04 and yesterday updated to 15.04. Now that problem is widely known with Broadcom chips but none of the suggested fixes worked for me as of yet. I would greatly appreciate any help and first let me know wich terminal readouts youd like to see.

A great many thanks
Paul

---

### Post by dino99 on 2015-05-11
The open-source firmware-b43-installer package is maintained upstream by the linux kernel community.  Is that driver installed on your system ?
( you can check it via synaptic (> sudo apt-get install synaptic)
[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx)

---

### Post by Paul_Palm on 2015-05-11
I do not currently have the driver installed because according to the documentation it does not support the 4313 chip wich I have. I did try to install the driver earlier anyway and well to no surprise it didn't work ;)

---

### Post by mörgæs on 2015-05-12
[http://ubuntuforums.org/showthread.php?t=2214110](http://ubuntuforums.org/showthread.php?t=2214110)

---

### Post by Paul_Palm on 2015-05-12
Sadly it did not work :(
here is the output of iwconfig


```
eth0      no wireless extensions.


wlan0     IEEE 802.11bgn  ESSID:"FRITZ!Box SL WLAN"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:15:0C:B3:49:CC   
          Bit Rate=48 Mb/s   Tx-Power=27 dBm   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=48/70  Signal level=-62 dBm  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:232   Missed beacon:0


lo        no wireless extensions.

```

---

### Post by jeremy31 on 2015-05-12
So what version of bcmwl do you have ```
dpkg -l | grep bcmwl
```

---

### Post by Paul_Palm on 2015-05-12
I can not use bcmwl (wich from my understanding is the sta driver) because it doesn't support the 4313 chipset.
According to most sources I have to use bcma+ brcmsmac.
But you gave me an idea, I checked with Synaptic wether any component with these names is installed and tada it isn't, although it is supposed to come preinstalled with the linux-firmware package.
So I tried using
```

sudo apt-get install linux-firmware

```
but it told me I already have the newest version. Any suggestions?

Edit: Right now if I press connect it starts end never stops trying to connect, previously it stopped and gave a fail message after about half a minute or so...

---

### Post by jeremy31 on 2015-05-12
You may have to blacklist b43 and/or ssb for the bcma combo to work correctly, but don't blacklist ssb if ```
lspci -nnk | grep -iA2 net
``` shows that ethernet uses b44 module.  Check ```
iwlist scan
``` to see if the group or pairwise cipher for your access point is using TKIP as it could cause disconnects

---

### Post by Paul_Palm on 2015-05-12
b43 and ssb are blacklisted, the lspci give following:
```

07:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
	Subsystem: Hewlett-Packard Company Device [103c:3388]
	Kernel driver in use: r8169
0d:00.0 Network controller [0280]: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter [14e4:4727] (rev 01)
	Subsystem: Hewlett-Packard Company Device [103c:145c]
	Kernel driver in use: bcma-pci-bridge

```

I can't see any mention of b44 so I assume the blacklisting of ssb is ok

as for TKIP it seems that it is active (here: [http://pastebin.com/PRPCZ66E](http://pastebin.com/PRPCZ66E) is the iwlist result)

---

### Post by sudodus on 2015-05-12
Good luck in this networking forum :-)

---

