---
title: "4311 Broadcom - Card installed but does not see wireless networks."
date: 2007-05-04
forum: Networking &amp; Wireless
---

### Post by WkenCouser on 2007-05-04
Hello

I am a recemt convert to Linux / Ubuntu and I have installed 7.04 (Feisty).
I have a Compaq Presario - C506CA Notebook that has a Broadcom 0x4311 wireless device. 

iwconfig says 
wlan0 IEEE 802.11b/g ESSID:off/any Nickname:"Broadcom 4311"
          Mode:Managed Frequency=2.484 GHz Access Point: Invalid
          Bit Rate=1 Mb/s Tx-Power=18 dBm
          RTS thr:off Fragment thr:off
          Link Quality=0/100 Signal level=-256 dBm Noise level=-256 dBm
          Rx invalid nwid:0 Rx invalid crypt:0 Rx invalid frag:0
          Tx excessive retries:0 Invalid misc:0 Missed beacon:0

I noticed that my iwconfig version is not the same as my eth1 version and i can not <set< my ESSID using iwconfig.

I appreciate any and all assistance.
ken :-)

---

### Post by Candace on 2007-05-05
Hi Ken,
I am pretty sure this link may help you:

[http://ubuntuforums.org/showthread.php?p=2589722#post2589722](http://ubuntuforums.org/showthread.php?p=2589722#post2589722)

I am not sure though if you have made changes to your Ubuntu install or if it is a fresh one...? The above link works with a fresh install. I was having a similar problem and at one point my Access Point said 'invalid' but I think I did a fresh install (sorry I don't really remember, I am played with it so much) and then it was no longer invalid. 

QUOTE:
I noticed that my iwconfig version is not the same as my eth1 version and i can not <set< my ESSID using iwconfig.

In the link, it gives instructions to set your ESSID the GUI way. Hope it helps. Post if you have more questions.

---

