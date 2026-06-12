---
title: "super slow internet"
date: 2007-05-27
forum: Networking &amp; Wireless
---

### Post by justincormier on 2007-05-27
Ok so im new to Ubuntu... i got beryl and all that cool jazz and i love it... but why oh why is the internet sooo slow?  Im barely running at 20k... whats the deal?  Is there a fix for this?

---

### Post by quagee on 2007-05-28
have you tried disabling ipv6 in firefox??

type in about:config in your browser and you will see a list of configuratioin settings.  filter out ipv6 and toggle by right clicking.

Not sure if this is the problem, perhaps if you could give more information about your ubuntu version and configuration settings someone might be able to help.:)

---

### Post by justincormier on 2007-05-28
I checked IPv6 in FIreFox and it was set to "false" which makes me assume it is off.  Im actually browsing in Opera (i get slightly better results), but that is either here nor there... 

as for my configuration settings.. i would love to post'em, but i dont know what you need to see or even how to get them... I can say that I have a netgear wireless card with Ubuntu Feisty 7.04.  Let me know what you need and how to retrieve the information and we can go from there.. ive also been reading on this forum and it seems alot of people experience slow internet, but i cant understand what they are talking about. haha im so new.

justin

---

### Post by justincormier on 2007-05-29
> lo        no wireless extensions.

eth0      no wireless extensions.

wifi0     IEEE 802.11b  ESSID:"pirates"  Nickname:"pirates"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:9A:BB:0B   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          
wlan1     IEEE 802.11b  ESSID:"pirates"  Nickname:"pirates"
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:0F:66:9A:BB:0B   
          Bit Rate:11 Mb/s   Sensitivity=1/3  
          Retry limit:8   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=40/70  Signal level=-54 dBm  Noise level=-94 dBm
          Rx invalid nwid:0  Rx invalid crypt:72  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:547   Missed beacon:0

-----------
my config settings using "iwconfig" in my terminal

---

