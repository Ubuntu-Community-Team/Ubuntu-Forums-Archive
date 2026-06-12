---
title: "Radio disabled by HW RF Kill switch"
date: 2007-11-18
forum: Networking &amp; Wireless
---

### Post by Swed on 2007-11-18
Hi, 
when I installed Ubuntu on my laptop, my wifi worked fine. But then I didn't know, how to turn it off to save battery. Fn+F1, Fn+F2, HW switch on laptop nothing worked. So I turned it off in BIOS. Then everything was ok but when I turned it on in BIOS again, my Ubuntu didn't find it.
dmesq writes:

iwl4965: Intel(R) Wireless WiFi Link 4965AGN driver for Linux, 1.1.0
iwl4965: Copyright(c) 2003-2007 Intel Corporation
iwl4965: Detected Intel Wireless WiFi Link 4965AGN
iwl4965: Radio disabled by HW RF Kill switch 

cat /sys/bus/pci/drivers/iwl4965/*/rf_kill                                                                      
0
echo "1" > /sys/bus/pci/drivers/iwl4965/*/rf_kill
echo "0" > /sys/bus/pci/drivers/iwl4965/*/rf_kill
log:
iwl4965: Radio disabled by HW RF Kill switch

I have Fujitsu Siemens Esprimo mobile v5505.
Linux swed 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

Thanks

---

### Post by Blutack on 2007-11-18
Not trying to be patronising but did you run those echo commands with sudo?
Sorry, it wouldn't matter if you did or not, 

cat /sys/bus/pci/drivers/ipw3945/0000\:02\:00.0/rf_kill 
0

And my wireless is fine.

---

### Post by Swed on 2007-11-18
> **Blutack said:**
> Not trying to be patronising but did you run those echo commands with sudo?


:) Yes, I did

---

### Post by Swed on 2007-11-20
Really no ideas?

---

### Post by Swed on 2007-11-20
How to do it, that when I touch the wifi button, it enables or disables wifi? It doesn't do anything (no logs).

---

### Post by Swed on 2007-11-20
Solved.
I just Loaded Defaults in BIOS and it started working
:)

But I still dont know how to disable it, when I need to.

---

### Post by rafalr on 2008-02-07
Hi,

before you find anything better you could just disable the service maintaining your wifi connection (nm-applet possibly ?)

also, you could give a try to wicd, which is probably much better replacement for network manager and available in repos. Still another option is wlassistant.

cheers,
rafal

---

