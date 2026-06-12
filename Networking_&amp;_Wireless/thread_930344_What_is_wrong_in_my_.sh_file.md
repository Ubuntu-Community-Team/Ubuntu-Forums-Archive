---
title: "What is wrong in my .sh file?"
date: 2008-09-25
forum: Networking &amp; Wireless
---

### Post by newred on 2008-09-25
I made a .sh file to make ubuntu detect my wireless card, but when i run it it won`t run the last line "ifconfig ath0 up".

When i type it in manualy it works fine.

WHY???

Here is the file:

#!/bin/sh

modprobe ath_pci
#finner kortet

#wlanconfig ath0 create wlandev wifi0 wlanmode sta
#laster driver
#wlanconfig ath0 destroy
#fjerner gammel driver
wlanconfig ath0 create wlandev wifi0 wlanmode sta
#If wlanconfig doesn't work, you retry it after executing '
wlanconfig ath0 destroy
#
modprobe ath_pci
#
wlanconfig ath0 create wlandev wifi0 wlanmode sta
#
iwconfig
#Now, if you type iwconfig, you should see a list like the following: 
#eth0      no wireless extensions.

#lo        no wireless extensions.

#wifi0     no wireless extensions.

#ath0      IEEE 802.11g  ESSID:""
#          Mode:Managed  Frequency:2.457 GHz  Access Point: 00:00:00:00:00:00
#          Bit Rate:0 kb/s   Tx-Power:20 dBm   Sensitivity=0/3
#          Retry:off   RTS thr:off   Fragment thr:off
#          Power Management:off
#          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
#          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
#          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

ifconfig ath0 up

---

### Post by lisati on 2008-09-25
Nothing obvious leaps off the screen to my attention, the best thing I can suggest at the moment is to check if it has a proper "newline" at the end of the last command.
Anyone else?

---

### Post by newred on 2008-09-25
Thanks alot for superfast reply :)

But how do i check if i have a propper newline at the end?

P.S!
You guys are great :D

---

### Post by willca on 2008-09-26
run your script in verbose...as such

#!/bin/sh
set -x  <----just add that

---

