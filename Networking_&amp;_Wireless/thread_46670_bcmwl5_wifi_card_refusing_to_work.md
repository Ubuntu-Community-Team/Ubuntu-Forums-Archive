---
title: "bcmwl5 wifi card refusing to work"
date: 2005-07-05
forum: Networking &amp; Wireless
---

### Post by telex4 on 2005-07-05
Ahoy,

I am trying to help a friend get his Linksys wifi card, using Broadcom's bcmwl5 driver, to work in Kubuntu. It works fine in Windows, so it's not a hardware problem. I've been using GNU/Linux for about 5 years now, and have wifi working fine on my own machine, so I'm quite stumped with this.

Basically, we went through the usual steps:
- installed ndiswrapper-utils
- copied the windows drivers to a save place
- installed the inf file with ndiswrapper
- turned RadioState to '0'
- modprobed ndiswrapper (no errors)
- edited the wireless config file as follows:

```

auto wlan0
iface wlan0 inet dhcp
wireless_key ---------------------------
wireless_essid Hazelby

```

But it doesn't work. The only problem I can find that might give some insight is in the output to dmesg:

```

$ dmesg | grep ndiswrapper:
ndiswrapper version 1.0rc2 loaded (preempt=yes,smp=no)
ndiswrapper: using irq 17
wlan0: ndiswrapper ethernet device 00:0f:66:74:24:1a using driver bcmwl5
ndiswrapper: driver bcmwl5 (Linksys,07/17/2003, 3.30.15.0) added

```

Usually on the penultimate line it will say something like "...using driver bcmwl5, configuration file 14E4:4320.5.conf". but on his machine it doesn't say it is using any of the config files. They're all there, nothing obviously wrong with them.

Any suggestions would be much appreciated... he'd love to be able to use a free desktop if only his network would work! ](*,)

---

### Post by TheSavage on 2005-07-05
I could only got my broadcom to work by following one of the thread in this forum about how to install ndiswrapper **1.1**.  Other then that, I wasn't able to make it work.

EDIT: I just find what I was referring to about the ndiswrapper 1.1 installation, here's the link.

[ndiswrapper wiki](https://wiki.ubuntu.com/SetupNdiswrapperHowto?highlight=%28ndiswrapper%29)

---

### Post by telex4 on 2005-07-06
OK, I'll set him on that path, thanks :)

Incidentally, just to check, what's a good sequence to check it's working after he has finished the ndiswrapper install (i.e. the module is loaded, and niswrapper reports the driver and hardware as present)?

I'm suggesting just doing a "iwlist scan", is that enough? Should that find an access point?

---

### Post by TheSavage on 2005-07-06
I never got any problem with it, as long as I see my ***wlan0*** in my network configuration panel (System -> Administration -> Networking).  Of cours, this is after your "**module**" is load, "**ndiswrapper -l**" is reporting your driver and that "**iwlist *wlan0* scanning**" show you something.

---

