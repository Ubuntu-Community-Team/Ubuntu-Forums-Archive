---
title: "suddenly i lost wireless connection"
date: 2007-01-10
forum: Networking &amp; Wireless
---

### Post by threefcata on 2007-01-10
i installed edgy on my acer aspire 5512WLMi laptop. After installation i immediately installed network manager for access to WPA-enabled wireless network at my home. Everything went on fine until last night all of a sudden, when i logged in gnome, network manager prompted that no network devices was found, i made several reboot afterwards until it brought back the wired network. now it still cannot detect any wireless network. what should i do?

threefcata@threefcata-yuri:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      radio off  ESSID:off/any  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=off   Sensitivity=8/0  
          Retry limit:7   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

threefcata@threefcata-yuri:~$ 
threefcata@threefcata-yuri:~$ iwlist eth1 scanning
eth1      No scan results
threefcata@threefcata-yuri:~$ 

thx!

---

