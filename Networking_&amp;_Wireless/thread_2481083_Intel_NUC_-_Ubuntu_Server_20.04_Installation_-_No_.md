---
title: "Intel NUC - Ubuntu Server 20.04 Installation - No Wired Ethernet"
date: 2022-11-18
forum: Networking &amp; Wireless
---

### Post by pardman on 2022-11-18
Setup:
- Intel NUC11TNHi3000 
- Trying to install Ubuntu Server 20.04
- Cannot get installation process to recognize wired Ethernet connection (pictures attached) - Wired ethernet connection works fine for other network devices so I know it's a functioning Ethernet cable
- Wireless connection works fine (however, I need to run my device over a wired connection, so wireless operation is not workable for steady state operation)

Has anyone encountered this issue before?  I am new to Ubuntu installations so would appreciate any advice/suggestions

---

### Post by TheFu on 2022-11-18
Well, the specific NIC chip is extremely important, but you didn't post that.  Nothing can be suggested before that data is provided.

If you are new to Linux, best to stick with a desktop installation, not server.  Server doesn't have any GUI, as you've learned.  OTOH, if you are willing to have a very steep learning curve, a server will teach you things that apply across all versions of Linux on almost all devices from the $5 single-chip-computer up into the thousand node supercomputers.

As others said below, newer kernels have support for newer hardware. Sometimes the automatic selector for which driver to use for which piece of hardware doesn't work as well as we'd like.  For networking, this is typically a failure caused by the chip maker using the same major name for 30 different internal chips.  Realtek does this all-the-time, unfortunately.  So what happens is Linux takes a guess at the hardware.  Appears either the NIC chip is very new (bleeding edge) or Linux made a bad guess.

Ubuntu Server expects to use a wired ethernet connection, so it doesn't have the hundreds of drivers for every possible NIC on the market.  Desktop distros tend to have all there are of those.

Anyway, once the NIC chip (including the revision) is known, next steps are possible.

---

### Post by sudodus on 2022-11-18
Try a newer version of Ubuntu Server, 22.04.x LTS or 22.10 in order to get Linux kernels with hardware drivers that are newer and let us hope new enough for the new hardware in the NUC.

---

### Post by praseodym on 2022-11-19
Please post the output of these commands:
```

lspci -nnk | grep -iA2 net
ifconfig -a
```

---

