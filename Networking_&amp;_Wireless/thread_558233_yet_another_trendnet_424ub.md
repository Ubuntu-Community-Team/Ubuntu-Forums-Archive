---
title: "yet another trendnet 424ub"
date: 2007-09-23
forum: Networking &amp; Wireless
---

### Post by anfractuosities on 2007-09-23
soooo...i am trying to get my trendnet wifi to work. i think I found the right driver finally realtek net8187b.inf . ive tried following the instructions all over the web but there is one part i get stuck on.  I have no wlan0.

I am also using an internal wireless, i want to be able to use them both at different times.  this is my iwcinfig and such

iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:"linksys"  
          Mode:Managed  Frequency=2.437 GHz  Access Point: 00:18:F8:4E:F8:39   
          Bit Rate:0 kb/s   Tx-Power:16 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:36   Missed beacon:0


lsusb

Bus 002 Device 001: ID 0000:0000  
Bus 005 Device 001: ID 0000:0000  
Bus 004 Device 002: ID 0b05:1712 ASUSTek Computer, Inc. 
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 004: ID 0402:5602 ALi Corp. 
Bus 001 Device 002: ID 0bda:8189 Realtek Semiconductor Corp. 
Bus 001 Device 001: ID 0000:0000  



the driver and device are recognized withe ndiswrapper -l
thank you

---

### Post by anfractuosities on 2007-09-24
WHY DO I NOT HAVE WLAN0???? its driving me CRAZY!!!

---

