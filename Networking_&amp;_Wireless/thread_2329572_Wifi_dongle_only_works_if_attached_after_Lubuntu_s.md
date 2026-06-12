---
title: "Wifi dongle only works if attached after Lubuntu started"
date: 2016-07-03
forum: Networking &amp; Wireless
---

### Post by sir2 on 2016-07-03
Hi,

I installed Lubuntu 16.04 on an Asus Transformer Book T100HA. Unfortunately its Wifi (Broadcom) is not supported yet, so I bought a cheap USB Wifi dongle, a mini USB stick from TP-Link. 

At the moment where I put this Wifi dongle in my USB slot it is automatically recognized and it works great.

However, I have problems when I start the laptop. I usually never remove the Wifi dongle, ie it is still in the USB slot when the computer is shut down. If I then start it, no connection to my network is established. What I then have to do is to remove the Wifi dongle. Actually, this gives me a message that ethernet has been disconnected and that I'm offline. If I then put the Wifi dongle back to the USB slot it is recognized and I have a connection within a few seconds. Btw, if I then remove the Wifi dongle again, the message is slightly different from before. Its basically the same, but instead of disconnection from ethernet I get a disconnection from a wireless network.

Any idea what I could try, so I am connected to the wireless network right from the start?

Thanks in advance

Claus

---

### Post by movienut50 on 2016-07-04
Try installing the linux driver from here:

[http://www.tp-link.com/res/down/soft/TL-WN723N_V3_150909.zip](http://www.tp-link.com/res/down/soft/TL-WN723N_V3_150909.zip)

---

### Post by jeremy31 on 2016-07-04
Please post results for ```
dmesg | grep brcm
```

---

### Post by sir2 on 2016-07-04
> **movienut50 said:**
> Try installing the linux driver from here:

[http://www.tp-link.com/res/down/soft/TL-WN723N_V3_150909.zip](http://www.tp-link.com/res/down/soft/TL-WN723N_V3_150909.zip)

Instead of that driver (which gave the same problems) I used the one  for my stick, ie TL-WN725N_V2_150911. I could fix some of the problems  while compiling (seq_printf is no a void method, so the two occurences  of if(....) had to by changed by removing the if, and I added  -Wno-error=date-time to the CFLAGS in the Makefile. Furthermore I  changed STATION_INFO_SIGNAL to BIT(NL80211_STA_INFO_SIGNAL).
But I  still get compile errors, this time from STATION_INFO_ASSOC_REQ_IES. And  changing it the same way to BIT(...) does not work.

So, for now  this did not yet help due to compile errors due to my kernel  (4.4.0-28-generic) and my gcc version (5.3.1 20160413), which seam to be  incompatible with that driver.

> **jeremy31 said:**
> Please post results for ```
dmesg | grep brcm
```
That one does not give any result.

Thanks to both of you, but so far I still have that problem. Any more ideas? Or help with compiling that driver?

Btw, only once it happend yesterday that the Wifi connection was there right from the start. But really just once, several times after that it did not work. Maybe some sort of timing problem...

---

### Post by sir2 on 2016-07-05
> **movienut50 said:**
> Try installing the linux driver from here:

[http://www.tp-link.com/res/down/soft/TL-WN723N_V3_150909.zip](http://www.tp-link.com/res/down/soft/TL-WN723N_V3_150909.zip)

That really was a terrible advice from you. Apart of the compile errors I got as mentioned  in my previous post, I had about 5 additional compile errors. More removed fields, additional parameters in methods, renamed methods, new variable in conflict with private ones, ...

Nonetheless, since there was no better idea, I went through all of those errors, and fixed them with the help of google. And indeed, with that driver my network is available right from the start.

So, despite the fact that you gave a really terrible advice, thank you for that good advice ;-)

---

### Post by movienut50 on 2016-07-05
Your welcome I think???? :redface:

---

### Post by him610 on 2016-07-05
I am not sure, but I think it comes from attempting to boot with two wireless network devices connected. The first priority, when the system boots, is probably the internal Broadcom device on the PCI bus. The boot sequence probably never detects the TP-Link device on the USB bus. 

You have some alternative solutions to address your issue:
1.  Get a proper driver installed for the Broadcom adapter, or
2.  Open it up and remove the Broadcom adapter (maybe disable in BIOS), or
3.  Replace the Broadcom adapter with an Intel adapter, or
4.  Continue with your current workaround.

Consider it as a feature instead of a shortcoming.:)

Oh, one other thing - about 10 years or so ago, there used to be a method using, I think, *ndiswrapper* where one could take Windows drivers for a Broadcom adapter to get a working driver for Linux. Don't know if it is still used, available, or what.

---

