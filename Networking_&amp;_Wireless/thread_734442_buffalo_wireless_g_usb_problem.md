---
title: "buffalo wireless g usb problem"
date: 2008-03-24
forum: Networking &amp; Wireless
---

### Post by yoma819 on 2008-03-24
hello
i have a buffalo wli-u2-kg125s usb wirless dongle
i am having a slight problem installing it!
when i execute the command lsusb itcomes up as:

Bus 005 Device 005: ID 0411:00da MelCo., Inc. 

i have tried ndiswrapper but the command ndiswrapper -l shows

netu2g54 : driver installed

nothing else
what am i doing wrong?
i am running ubuntu gutsy gibbon 7.10
help please
thanks
--yoma
:confused::confused::confused:

---

### Post by dstew on 2008-03-24
Post the output of ```
iwconfig
```

---

### Post by yoma819 on 2008-03-25
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4318"
          Mode:Managed  Frequency=2.472 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=18 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=0/100  Signal level=-256 dBm  Noise level=-256 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0
thanks
--yoma
note the broardcom is an internal pci phisically broken wireless card i have not been bothered take out!
thanks
--yoma

---

### Post by dstew on 2008-03-25
I've been googling around a bit, and it seems that dongle should work with the zd1211rw driver that is built into the Ubuntu generic kernel, at least after 2.6.23.  See [this document]("https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsBuffalo").  Maybe you just need to update your kernel. Are you using a custom kernel perhaps? Did you blacklist that driver in your attempts to get ndiswrapper to work?

---

