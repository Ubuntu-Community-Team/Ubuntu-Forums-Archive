---
title: "cant get wireless card on HP TC1100 tablet to power on"
date: 2008-08-19
forum: Networking &amp; Wireless
---

### Post by reverend1313 on 2008-08-19
I have read some other posts about the wireless cards in these tablets and them not wanting to power on. I can get wireless to work when i plug my netgear WG111 in but not off the built in wireless. 

Im running 8.04. 
Any ideas on how to make it turn on. 



iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  Nickname:"ipw2100"
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:off   
          Retry short limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by reverend1313 on 2008-08-20
OK figured it out... I took a quick glance at the forums thinking it was harder to solve than it really was. 

Bios... Wireless/Bluetooth =enabled... fixed. 

One thing to note for anyone else that searches on this. The HP Q Menu software that turns the wireless on and off actually flips this switch in the bios. So the last time it was used if it got turned off and you install linux, it will be off by default.

---

### Post by trksh22 on 2008-09-22
Thank you for this! I was searching for hours trying to figure out why the internet wouldn't work! Went to the BIOS and saw that wireless was disabled. Enabled it. Started up the computer and now the internet and bluetooth works! Thank you, I registered just to say that, by the way!:KS

---

