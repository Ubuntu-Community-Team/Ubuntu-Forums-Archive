---
title: "bcm43xx 11Mb in Fesity??  Why?"
date: 2007-04-28
forum: Networking &amp; Wireless
---

### Post by finite9 on 2007-04-28
I read on the bcm43xx dev-list ages ago that they had increased the speed to 36Mbit in kernel 2.6.17, but in Feisty release it is still only running at 11Mbit.

What gives?

---

### Post by chili555 on 2007-04-28
What does iwconfig report after:```
sudo iwconfig eth1 rate auto
```Substitute your wireless interface, wlan0, wifi0, etc. here.

---

### Post by zumbi77 on 2007-04-29
I have the same problem. iwconfig reports:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Haldr"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.412 GHz  Access Point: 00:19:5B:49:E0:3B   
          Bit Rate=11 Mb/s   Tx-Power=15 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality=71/100  Signal level=-47 dBm  Noise level=-72 dBm
          Rx invalid nwid:0  Rx invalid crypt:867  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by mudhog on 2007-04-29
I too am experiencing this quirk. Is there anyway to remedy this?

---

### Post by Kobalt on 2007-04-29
I've never been able to have more than 11Mb/s using the bcm43xx drivers... I had to use [ndiswrapper]("http://ubuntuforums.org/showthread.php?t=197102&highlight=bcm4318") in order to have a full 54Mb/s.

---

### Post by mudhog on 2007-04-29
Ok thanks for the info. Is there anyway to manually edit the bcm43xx drivers so i dont have to use the ndiswrapper and the windows drivers?

---

### Post by Kobalt on 2007-04-30
> **mudhog said:**
> Ok thanks for the info. Is there anyway to manually edit the bcm43xx drivers so i dont have to use the ndiswrapper and the windows drivers?
Never heard anything in this way...

---

### Post by finite9 on 2007-04-30
I get this...

```
andrew@everest:~$ sudo iwconfig eth1
eth1      IEEE 802.11g  ESSID:"HenryWLAN"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:B3:23:0E   
          Bit Rate:11 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:4827-21C0-B928-256A-8FE1-E41C-0CC4-A38B-A4BD-3A85-E271-F580-DADD-4174-DBB2-3E68   Security mode:open
          Power Management:off
          Link Quality=68/100  Signal level=-37 dBm  Noise level=-38 dBm
          Rx invalid nwid:0  Rx invalid crypt:1  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:16   Missed beacon:0
```

Believe me, I have tried setting this in my /etc/network/interfaces startup script (I use a seperate script for pre-up, but it doesn't seem to help.

I cannot find the devlist anymore on bcm43xx homepage where they say that speed has been increased to 36Mbit but I do know I have read that.

By the way, I am using Network-manager and it is this that reports 11Mbit as well.  I have another laptop with ipw3945 and there, nmapplet reports 54mBit.

---

