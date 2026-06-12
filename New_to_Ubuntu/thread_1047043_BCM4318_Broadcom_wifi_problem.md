---
title: "BCM4318 Broadcom wifi problem"
date: 2009-01-20
forum: New to Ubuntu
---

### Post by archeryguru2000 on 2009-01-20
when I run the command lshw -class network, I'm greeted with the following:
```

*-network:1
       description: Network controller
       product: BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller
       vendor: Broadcom Corporation
       physical id: b
       bus info: pci@0000:00:0b.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master
       configuration: driver=b43-pci-bridge latency=64 **[COLOR="Red"]module=ssb[/COLOR]**

```

Should the ssb concern me?  I was under the impression that this should've stated ndiswrapper (or something of the like).  :-k  Am I correct in assuming this?

And with lspci:
```

00:0b.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)

```

I posted this in case it is needed.  By the way, I've tried using ndiswrapper, b43, bcm43xx and still no wireless... very frustrating.  ](*,)  All help appreciated.

Thanks,
~~archery~~

---

### Post by archeryguru2000 on 2009-01-20
Also, just thinking out loud here, I have my wireless configured on my WinXP partition... am I able to "acquire/borrow" any drivers from there to make this work?  I've installed ndisgtk and tried searching for the .inf file but I'm not sure where to look.  Any suggestions?

~~archery~~

---

### Post by archeryguru2000 on 2009-01-21
> If you post back the make/model of your laptop, I may be able to download the driver and extract the files you would need, then post them back here tar'd. I think that is allowed but not sure since they are not "open" drivers.

Acer Aspire 3003LCi

---

