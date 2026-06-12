---
title: "Gutsy WUSB11 install issues"
date: 2007-11-12
forum: Networking &amp; Wireless
---

### Post by gasholine on 2007-11-12
I was about to give up on wireless adapters entirely in my new mythTV install when I figured I give it one more go. I switched from knoppmyth to mythbuntu (excellent decision, from what I've seen so far), and many of the former issues were fixed, but wireless still isn't working. Here are the specifics:

I'm runing Gutsy on a Via EPIA SP board. Works great. Attempting to use a Linksys WUSB11 ver 2.8 wireless adapter. The adapter IS recognized, albeit a generic drive seems to be used to get it up and running. Here's the output from 'dmesg | grep wlan0':

[   52.224215] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/wireless/at76/at76c503.c: registered wlan0
[   75.448815] wlan0: no IPv6 routers present

Good. Correct chipset (Atmel 76c503), and no, I don't broadcast a !Pv6 address. 

Here's the output from iwconfig:

wlan0     IEEE 802.11b  ESSID:"linksys"  Nickname:""
          Mode:Managed  Frequency:2.437 GHz  Access Point: *****   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   
          Retry limit:8   RTS thr=1536 B   Fragment thr=1536 B   
          Power Management:off
          Link Quality=96/100  Signal level=100/100  
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


I blurred out the AP info,  but the MAC address is correct. And it appears that the device is recieving a signal (?). 

This pops up in dmesg, however:

[   60.718639] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/bui
ld-generic/wireless/at76/at76c503.c: 2522: assertion dev->istate == INIT failed
[   62.202460] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/bui
ld-generic/wireless/at76/at76c503.c: 1784: assertion dev->curr_bss == NULL faile
d

I'm guessing that's bad. If'n I don't have an ethernet connection for this box, can I hoof over the appropriate packages and sources on a thumb drive in order to compile a driver, or should I just get me a cheap WAP and configure it as a node on my network and save myself lots of hair-pulling-outing. 
 
Gasholine

---

