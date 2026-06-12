---
title: "Wireless not enabled"
date: 2009-03-14
forum: New to Ubuntu
---

### Post by mr-woof on 2009-03-14
I know this is a known problem with ubuntu, so sorry to bother you all again with this :)

I've got an old laptop with a intel pro/wireless 2200bg onboard wireless card, in the network manager the option to enable it is greyed out and i can't get the fecker to enable.

any ideas?

---

### Post by Kobalt on 2009-03-14
Hello,

This wireless card should work out-of-the-box since Ubuntu Breezy... Which version of Ubuntu to do use? Is the card working in Windows (if you have a dual boot)? Can you please post the output of the following command line : 
```
iwconfig
```

---

### Post by mr-woof on 2009-03-14
Hi,

thanks for the reply, i'm just running gparted to shrink the ubuntu partition as i'm going to install xp, just to see if the card is 100% working, then i'll post the output of iwconfig

---

### Post by mr-woof on 2009-03-14
The wireless card is definately working in xp, output of iwconfig:

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

pan0      no wireless extensions.

---

### Post by mr-woof on 2009-03-15
Well that's completely mental, i shrank the ubuntu partition and created an XP install in the unallocated space. Installed all the wireless drivers and the panel drivers for the wireless keys, wireless all working :)

Rebooted back into ubuntu and the wireless is now working, the only other thing i did was to update the bios as i'm trying to boot from a usb pen drive. 

Any ideas ?

---

