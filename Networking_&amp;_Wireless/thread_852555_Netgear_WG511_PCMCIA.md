---
title: "Netgear WG511 PCMCIA"
date: 2008-07-07
forum: Networking &amp; Wireless
---

### Post by mitchell2345 on 2008-07-07
Hi,

I am runing Xubuntu off a liveCD and trying to get my wireless card to work.  It is of model Netgear WG511.

When i plug it into the PCMCIA slot in DMESG i see the following error:
```
[  367.331553] pccard: CardBus card inserted into slot 0
[  369.126896] PCI: Enabling device 0000:05:00.0 (0000 -> 0002)
[  369.126913] ACPI: PCI Interrupt 0000:05:00.0[A] -> GSI 16 (level, low) -> IRQ 18
[  369.126935] PCI: Setting latency timer of device 0000:05:00.0 to 64
[  369.453587] p54: LM86 firmware
[  369.453594] p54: FW rev 2.7.0.0 - Softmac protocol 4.1
[  370.475587] 0000:05:00.0 (prism54pci): Cannot read eeprom!
[  370.475660] ACPI: PCI interrupt for device 0000:05:00.0 disabled
[  370.475684] prism54pci: probe of 0000:05:00.0 failed with error -22
```

A listing with lspci shows me:
05:00.0 Network controller: Intersil Corporation ISL3890 [Prism GT/Prism Duette]/ISL3886 [Prism Javelin/Prism Xbow] (rev 01)

According to this page it should be supported out of the box.
[https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear](https://help.ubuntu.com/community/HardwareSupportComponentsWirelessNetworkCardsNetgear)

The card works fine in Windows.

Thanks,
Mitchell

---

### Post by chili555 on 2008-07-07
I saw this: [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/106987](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/106987) 

I was especially interested in this:> kernel hackers be aware: At first glance this appears to be a bug in the driver p54. But I have discovered a workaround which suggests it's not. This is why I did not put this against the linux-source-2.6.20 package.

I have my system in a state now where if I boot the pc with the Netgear wireless card inserted, the output from dmesg shows:

[ 36.698584] 0000:03:00.0 (prism54pci): Cannot read eeprom!
[ 36.698656] prism54pci: probe of 0000:03:00.0 failed with error -22

The system does not show the network device wlan0. If I remove the card and re-insert it, problem solved, the card initialises, wlan0 appears and off I go to grab the latest ep. of lugradio.
I have also booted from cold *without* the card inserted, and then proceeded to insert it, this works and I'm on the internet in seconds.

I really need some help narrowing down the cause of this, obviously the environment the card is initialised in during boot is different to when it is inserted after boot.This mirrors my experience with my old WG511.

---

