---
title: "Wireless on Aspire 7741z inop"
date: 2011-03-09
forum: New to Ubuntu
---

### Post by Don1500 on 2011-03-09
I have an Aspire 7741z running Ubuntu 10.04
I just loaded the 32 bit version today, then did the Update manager (398 updates)
Before the update everything worked fine. After the update, no wireless. Password & security is correct, all wireless setup is correct. Aside from my network, I do have access to a local hotel (next door) and I can always get into their unsecured guest network, that doesn't work either. 

output from lspci
```
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 18 )
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 18 )
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
```

I know I can go to the 64 bit version, but is that the answer or is something else wrong?

---

### Post by Don1500 on 2011-03-09
Anyone?

---

### Post by Don1500 on 2011-03-09
Chirp, Chirp

---

### Post by Don1500 on 2011-03-09
Well, since nobody would offer anything I did a LOT more searching and found a note buried way down in another thread from 2008 that had nothing to do with this. It mentioned back ports and said some were old. I went to the synaptic manager and found that there are some generic wireless backports that are not installed, so I installed them. Guess what, it worked. I figured there had to be a way without a new driver since the live disk worked.

 atheros AR9287 wireless  

If you have this wireless adaptor and it doesn't work, go to the synaptic manager and load =>  linux-backports-modules-compat-wireless-[COLOR="Red"](Your version here)[/COLOR]-generic

---

