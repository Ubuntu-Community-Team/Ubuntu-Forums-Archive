---
title: "Extremely slow internet connection (BCM4310)"
date: 2006-12-07
forum: Networking &amp; Wireless
---

### Post by KentS on 2006-12-07
I got my broadcom wireless to work using fwcutter following this guide:
[http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+bcm4310](http://ubuntuforums.org/showthread.php?t=185174&highlight=broadcom+bcm4310)
Unfortunately its extremely slow. My download rate is approx. 180 kbit/s on linux. I have Windows on the same PC and my downloadrate in Windows is 5Mbit/s. I was thinking about trying ndiswrapper according to this guide:
[http://ubuntuforums.org/showthread.php?t=201902&highlight=slow+connection](http://ubuntuforums.org/showthread.php?t=201902&highlight=slow+connection)
Can that help? What do I do to remove the files already installed using the first method? Or should I try something else?

My PC is a HP Pavilion dv2004ea with AMD Turion 64 x2. I have installed Ubuntu Dapper Drake with the PC (intel x86) desktop CD. 
My output from 'lspci | grep Broadcom\ Corporation' is '0000:01:00.0 Network controller: Broadcom Corporation BCM4310 UART (rev 01)' 
My output concerning eth1 from iwconfig when the wifi card is deactivated is
> 
eth1      IEEE 802.11b/g  ESSID:off/any  Nickname:"Broadcom 4311"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid
          Bit Rate=11 Mb/s   Tx-Power=18 dBm
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Are there other solutions, like an external antenna that you can plug into a USB port, that works with Ubuntu? I'm also willing to try solutions like that, but I don't know what hardware is compatible with Linux.

---

### Post by KentS on 2006-12-07
Now, I've done something stupid. I typed 'sudo rm bcm43xx...' and so on for every file starting with bcm43xx in the folders given in the first guide I mentioned. Then I used the second guide. I got some errors using the second guide, and now Ubuntu doesn't detect eth1, which is my wireless card. Please help! What do I do?

---

