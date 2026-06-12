---
title: "Belkin 54 USB Wireless"
date: 2009-03-05
forum: New to Ubuntu
---

### Post by gdn1947 on 2009-03-05
Thanks to the guys who responded to my original query yesterday but am no further forward.

I am an absolute new starter so please excuse any potentially stupid questions!

Ubuntu 8.10 / Belkin 54 USB Wireless Adaptor F5D7050 V3000

We have an active wireless adaptor working on another desktop in the house 

If the device is plug and play, and is working, what should I be seeing on screen?

The indicator light on the adaptor flashes occasionally suggesting that it is doing, or trying to do, something.

We had issues getting an internet connection originally and had to make some changes to the sudo code. The bottom line is that we have a connection but there are NO internet connections shown in Network Connections.

Any further step by step help would be very much appreciated

---

### Post by FreewheelinFrank on 2009-03-05
This adapter seems to work out of the box with Ubuntu. I'm pretty sure it's the one I have- anyway, someone at Amazon found it worked.

[http://www.amazon.com/F5D7050-Wireless-802-11g-Network-Adapter/product-reviews/B0002HA7FY/ref=cm_cr_dp_synop?ie=UTF8&showViewpoints=0&sortBy=bySubmissionDateDescending#R2VSGMKXO4XJBM](http://www.amazon.com/F5D7050-Wireless-802-11g-Network-Adapter/product-reviews/B0002HA7FY/ref=cm_cr_dp_synop?ie=UTF8&showViewpoints=0&sortBy=bySubmissionDateDescending#R2VSGMKXO4XJBM)

Do you have wireless enabled in Network Manager?

Is the Belkin adapter listed? It should be.

---

### Post by gdn1947 on 2009-03-05
hi the network manager shows eth0 and lo

---

### Post by skymera on 2009-03-05
I have this USB for my laptop.

F5D7050 and i run the F5D7000 in my desktop

Both work out the box fine.

---

### Post by gdn1947 on 2009-03-05
Would you like to tell me what I need to do to make the thing work and what I should be looking for in the various 8.10 Network screens? Thanks

---

### Post by skymera on 2009-03-05
I'll try but i don't have very long.
So, sorry if i leave you in the dark :)

In the terminal type
```
 iwconfig 
```

Paste the output. This'll show if your network USB is being detected.

---

### Post by FreewheelinFrank on 2009-03-05
> **gdn1947 said:**
> 

We had issues getting an internet connection originally and had to make some changes to the sudo code.

Can you remember what changes you made?

---

### Post by gdn1947 on 2009-03-05
result of iwconfig

lo        no wireless extensions.

eth0      no wireless extensions.

pan0      no wireless extensions.

wmaster0  no wireless extensions.

wlan0     IEEE 802.11bg  ESSID:""  
          Mode:Managed  Frequency:2.412 GHz  Access Point: Not-Associated   
          Tx-Power=8 dBm   
          Retry min limit:7   RTS thr:off   Fragment thr=2352 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

---

### Post by gdn1947 on 2009-03-05
I think we changed it to  

auto eth0
iface eth0 inet dhcp

---

### Post by FreewheelinFrank on 2009-03-05
I'm sure it's a network problem rather than a problem with the adapter.

Looks like skymera knows more than I do: hopefully he can tell you something from the information you posted.

Otherwise, post the same information in the networking & wireless forum and I'm sure somebody will sort you out.

---

### Post by gdn1947 on 2009-03-05
I think you are right. Thanks for the advice> I'll repost.

---

