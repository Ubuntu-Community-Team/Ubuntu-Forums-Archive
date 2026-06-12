---
title: "Disabled wireless?"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by scream_sayonara on 2009-07-30
My wireless which has been working perfectly for months has suddenly stopped working.

It will not recognise any of the many wireless networks in reach of my house...

I have checked iwconfig and it says:

lo        no wireless extensions.

eth0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11abgn  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=15 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

pan0      no wireless extensions.


I haven't had any trouble with it before on this install, but I was trying to get on the uni wireless network today and I am concerned that I may have disabled the wireless card somehow, or knocked some other setting around accidentally?

Or maybe not? Any ideas?

Please help me!

---

### Post by scream_sayonara on 2009-07-30
bump! come on smarties!

---

### Post by mapes12 on 2009-07-30
Does it show up in ```
lspci
``` or  ```
sudo lshw -C network
```?

---

### Post by pastalavista on 2009-07-30
Is your PC a notebook with a physical, manual wireless switch that might have gotten switched off?

---

