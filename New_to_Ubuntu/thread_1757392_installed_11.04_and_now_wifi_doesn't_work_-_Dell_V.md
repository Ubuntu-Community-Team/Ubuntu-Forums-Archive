---
title: "installed 11.04 and now wifi doesn't work - Dell Vostro 1500"
date: 2011-05-13
forum: New to Ubuntu
---

### Post by Coretj on 2011-05-13
I have a Dell Vostro 1500 I installed 10.10 because of massive issues in the past and it fixed them all.  Among those issues was that my WIFI didn't work.

I got a notice that an upgrade was available so I figured, "why not?"  It took FOREVER (about 9 hours) but when it was done I was looking forward to playing around with it only to find that my WIFI doesn't work. 

I'm not a programmer or even really linux "literate" so I have no clue how to fix this....

Any help would be extremely appreciated.

---

### Post by Coretj on 2011-05-13
SOLVED!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!!
Thank you to NGRONEWOLD

> **ngronewold said:**
> RedStar, if you're laptop is one of the Dell Inspiron series and has a Broadcom wireless card inside, then here is the solution (no coding required):

Re: 11.04 wireless issues
- I removed the STA driver from Additional Drivers
- I opened synaptic and installed b43-fwcutter then firmware-b43-installer
- Reboot

Now it works.

You have to be hooked up to the internet via a land line for this to work though. I struggled for hours with land internet but no wireless connection until I found this solution here on the Forum.

---

### Post by khushalb on 2011-05-14
iwconfig gives me this for my broadcom wifi acer laptop

into terminal, which yields: 

lo no wireless extensions.

eth0 no wireless extensions.

wlan0 IEEE 802.11bg ESSID: off/any 
Mode:Managed Access Point: Not-Associated 
Tx-Power= 0dBm
Retry long limit:7 RTS thr: off Fragment thr: off
Power Management: off

Any Solution to this. I want to connect to my Wifi network.

---

