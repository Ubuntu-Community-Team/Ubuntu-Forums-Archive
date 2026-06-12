---
title: "Vostro Wifi"
date: 2007-12-26
forum: Networking &amp; Wireless
---

### Post by karl0sglover on 2007-12-26
Hello,

I recently got hold of a Dell Vostro 1000 everything works perfect wireless works using the following walkthrough;
[http://ubuntuforums.org/showthread.php?t=405990](http://ubuntuforums.org/showthread.php?t=405990)


Wireles Card;
05:00.0 Network controller: Broadcom Corporation BCM94311MCG wlan mini-PCI (rev 01)

iwconfig output; 

eth0      IEEE 802.11g  ESSID:"core-fxp0-glover"
          Mode:Managed  Frequency:2.417 GHz  
          Bit Rate=54 Mb/s   Tx-Power:32 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Power Management:off
          Link Quality:79/100  Signal level:-45 dBm  Noise level:-96 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Connects works perfect, but when trying to download files locally from a fileserver i seem to get speeds 426KB/s and then lowers to around 12XKB/s same happens on wired which is very strange when downloading small files ( ie a couple of megs i peaks around 1.2MB/s )

The fileserver is not the issue as i have tried it on other machines on the network nor a duplex issue ( server end anyway ) when wired it shows as full duplex 100baseTX so no issues there.

I presume the IPv6 fix was for slow DNS issues i did try it anyway but made no difference.

also the dhclient fix of uncommenting the DNS servers line, again a dns resolution fix.

I have tried reinstalling the driver and the complete OS did not help, i am currently running Gutsy; was running Feisty still had the same problem.

Any suggestions would be great.

Thanks,
Karl Glover.

---

