---
title: "Issues with ath9k backport / Ubuntu 12.04 on Acer Aspire E1 laptop"
date: 2014-03-17
forum: Networking &amp; Wireless
---

### Post by Fred_Anderson on 2014-03-17
Hi all.

I'm trying to get the ath9k backport working on a new Acer Aspire E1 laptop, but I'm having problems with (I think) my kernel boot options. When I first tried to install Ubuntu, my screen went black during the boot process. A friend who knows a lot more about kernel stuff than I do suggested I add "acpi=off noapic" to disable ACPI and APIC at boot time, and with those options the system works great except for the lack of wireless networking (side note: those options didn't work when I tried 13.10 and I never found anything that did, so I stuck with 12.04). 

With the system mostly working, I set about getting the wireless networking going. Some other threads on this forum led me to install the latest backports and the ath9k driver (my wireless NIC is an Atheros 9565), but at boot time there's an IRQ conflict. dmesg shows:

```

[   12.537375] ath9k 0000:07:00.0: can't find IRQ for PCI INT A; please try using pci=biosirq
[   12.537478] genirq: Flags mismatch irq 0. 00000080 (ath9k) vs. 00015a20 (timer)
[   12.537512] ath9k 0000:07:00.0: request_irq failed
[   12.537554] ath9k: probe of 0000:07:00.0 failed with error -16

```

Further threads suggested kernel boot options of "acpi=force irqpoll noapictimer", and sure enough, those options make the wireless adapter start working...but unless I have an external monitor attached, I get the black screen I was originally getting.

I'm pretty much a user-level person, not any kind of expert, so I'm not sure what to do. I feel like I'm close, and that there's some combination of kernel parameters that will let me have both video and wireless networking, but I can't figure out what it is. I don't knew enough about it.

Can someone offer assistance / suggestions, using small words even a non-tech can understand?

Thanks in advance.

---

### Post by lisati on 2014-03-18
*Thread moved to **Networking & Wireless**.*

---

### Post by Fred_Anderson on 2014-03-18
So I figured it out. Like I suspected, it was related to the kernel boot parameters.


All I did was take off all the parameters I had and put "video=1024x768" instead. During boot, it switches to that mode briefly, then when X starts it jumps to 1600x900 and shows me a login prompt, and the wireless card is working great. I'm posting this from that laptop right now.

---

