---
title: "restoring problem"
date: 2011-08-02
forum: New to Ubuntu
---

### Post by aju1991 on 2011-08-02
I am using ubuntu11.04.
When i open the  lid after closing sometimes i can't returned to the prevoius state.It shows only the blank screen.
pls help me................

---

### Post by skatinjj on 2011-08-02
Is the power light blinking on the system?

Have you tried hitting keys and/or the power button?

It may just go to standby.  You should be able to change that with power management (not sure if that is the right place to look).

---

### Post by aju1991 on 2011-08-02
> **skatinjj said:**
> Is the power light blinking on the system?

Have you tried hitting keys and/or the power button?

It may just go to standby.  You should be able to change that with power management (not sure if that is the right place to look).

Threr is no use to hitting the keys .only way to restart the computer.
Inthe power management i given that when lid closed is
blank screen

---

### Post by Redblade20XX on 2011-08-02
Usually when that happens to me, it a graphic driver problem. Did this always happen or did it just start happening? Also what's your graphics card?

---

### Post by aju1991 on 2011-08-02
> **Redblade20XX said:**
> Usually when that happens to me, it a graphic driver problem. Did this always happen or did it just start happening? Also what's your graphics card?

it happens only in sometimes .
sometimes i got the previous screen.
When i use old versions of ubuntu,always  i had the same problem.
Now it reduced.but it happens in sometimes

---

### Post by skatinjj on 2011-08-02
What laptop is it and can you post the results of this:

```
lspci
```

Ran from the terminal.

---

### Post by aju1991 on 2011-08-02
> **skatinjj said:**
> What laptop is it and can you post the results of this:

```
lspci
```

Ran from the terminal.

hi,
 i am using compaq presario cq42



Reslt of command you given is given below...........






00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
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
02:00.0 Network controller: Atheros Communications Inc. AR9285 Wireless Network Adapter (PCI-Express) (rev 01)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 02)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

---

### Post by wildmanne39 on 2011-08-03
Hi, it looks like you left a lot out of the information you posted. Here is a link on freezing.
[https://wiki.ubuntu.com/X/Troubleshooting/Freeze](https://wiki.ubuntu.com/X/Troubleshooting/Freeze)

---

