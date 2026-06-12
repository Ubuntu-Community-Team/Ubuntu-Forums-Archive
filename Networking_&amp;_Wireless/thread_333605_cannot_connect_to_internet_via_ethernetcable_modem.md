---
title: "cannot connect to internet via ethernet/cable modem router"
date: 2007-01-07
forum: Networking &amp; Wireless
---

### Post by suebelle62 on 2007-01-07
Just installed ubuntu 6.10.

Cannot connect with wired ethernet/cox cable modem/router secenario.

I use windows XP and windows 98 on other machines connecting thru router and cox cable modem.

Help much appreciated.

Thanks

---

### Post by n00b@linux on 2007-01-07
Did you have the ethernet cable plugged in when you booted up?  It should detect your ethernet card automatically and use dhcp.  Can you post some details about your ethernet card, viz. make and model?

---

### Post by suebelle62 on 2007-01-07
yes ethernet cable was connected to router when installation began.

When trying the live CD yesterday the settings were not picked up either.

Only choice for internet that did show up was dial up modem.

---

### Post by n00b@linux on 2007-01-07
Well, it's either (a) your ethernet card is not detected by the kernel, (b) your ethernet card is detected by the kernel but the kernel module (ie. 'driver') has not been loaded, or (c) it's something else.

Open a terminal (Applications > Accessories > Terminal) and type the command:```
lspci
```which, btw, stands for '_l_i_s_t _pci_ devices'.  It should show your ethernet controller which should help us to eliminate (a) above.  Post the output to this thread.

---

### Post by suebelle62 on 2007-01-07
lspci brings up the AMD bridges, IDE, Yamaha, audio and PCTel dial up modem info.
Ubuntu did not pick up the CDR, DVD Rom, NIC and printer connections.

will have to transpose all info here, as this is sent off a WIN98 machine in another room.

Guess I could see if the WIN XP will boot and get all info off that machine as that is the same on Ubuntu is on.

---

### Post by suebelle62 on 2007-01-07
> **suebelle62 said:**
> lspci brings up the AMD bridges, IDE, Yamaha, audio and PCTel dial up modem info.
Ubuntu did not pick up the CDR, DVD Rom, NIC and printer connections.

will have to transpose all info here, as this is sent off a WIN98 machine in another room.

Guess I could see if the WIN XP will boot and get all info off that machine as that is the same on Ubuntu is on.

  never mind XP will not boot.   It was only working in safe mode.

May just reformat everything and start over somewhere.

---

