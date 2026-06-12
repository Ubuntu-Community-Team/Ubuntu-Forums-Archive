---
title: "Wake On Lan issue with D-Link 530TX ?"
date: 2008-10-07
forum: Networking &amp; Wireless
---

### Post by dcarpeneto on 2008-10-07
Hi all - I have hardy running on a server with a D-Link 530TX card installed. Ubuntu picked this up as a VIA Rhine III card, and it works fine for networking, however wake on lan does not work. 

I know I installed the card properly (including the WOL cable), and set up the BIOS correctly, as wake on lan works fine when I run WinXP on the server. 

I know I've got WOL configured correctly in Ubuntu, as ethtool shows:
```

  # sudo ethtool eth1
  Settings for eth1:
	Supported ports: [ TP MII ]
  ...
	Port: MII
	PHYAD: 1
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: g
	Current message level: 0x00000001 (1)
	Link detected: yes

```

... is it maybe an issue with the device being picked up with the wrong driver ? Any ideas how I correct this ? Truthfully I have no idea how the hardware got picked up - Ubuntu's plug & play is pretty impressive :) . 

Fwiw here's the dmesg messages on this interface:

```
# dmesg | grep eth1
[   46.385679] eth1: VIA Rhine III at 0xdf001000, 00:0d:88:f8:14:8b, IRQ 10.
[   46.386404] eth1: MII PHY found at address 1, status 0x786d advertising 01e1 Link 41e1.
[  268.169854] eth1: link up, 100Mbps, full-duplex, lpa 0x41E1
[  229.966716] eth1: no IPv6 routers present
```

Thanks for any help you can give - Dave

---

### Post by dcarpeneto on 2008-10-10
OK, so it turns out wake on lan works if I power off ubuntu, but not if I suspend or hibernate (unlike WinXP, where wake on lan works without fail in all 3 situations).

Is this maybe some sort of oddity in how my box goes to suspend ? Is there a way in ubuntu to flip between S1 / S3 suspend ? From what I can find on the web WinXP uses S1, so maybe this is the issue ... any help appreciated :)

 - Dave

---

### Post by dcarpeneto on 2008-10-10
Aside - if I allows S1 suspend only (in BIOS) dmesg shows:

```
  [   26.761616] ACPI: (supports S0 S1 S4 S5)
```

... however I magically loose the ability to suspend:

```
# pm-is-supported --suspend
# echo $?
1
#
```

... how do I enable S1 suspend in Ubuntu ? Changing ACPI_SLEEP_MODE in /etc/default/acpi-support seems to have no effect :(

---

### Post by P86 on 2008-12-16
Did you have to do anything other than "ethtool -s eth0 wol g" to get WOL working from a complete shutdown? I'm running Hardy with a dlink 530tx as well, with no luck.

---

### Post by dcarpeneto on 2008-12-17
> **P86 said:**
> Did you have to do anything other than "ethtool -s eth0 wol g" to get WOL working from a complete shutdown?

Not really. There's a WOL cable that the card comes with - you need this hooked up before this will work - maybe this is the issue ?

Also: check your BIOS settings - make them as permissive as you can regarding ACPI.

Other than that the only advice I can give is try the setup in Windows - this is what I did & all worked fine (I eventually reverted to WinXP because of the issues seen here :(  ).

---

### Post by P86 on 2008-12-17
> **dcarpeneto said:**
> Not really. There's a WOL cable that the card comes with - you need this hooked up before this will work - maybe this is the issue ?

Also: check your BIOS settings - make them as permissive as you can regarding ACPI.

Other than that the only advice I can give is try the setup in Windows - this is what I did & all worked fine (I eventually reverted to WinXP because of the issues seen here :(  ).

I've got the hardware issues covered. I've had WOL working on this box with FreeNAS. I just find it weird that you got it working (from shutdown at least) and I'm having problems. Oh well... at least Ubuntu is getting better with age. I'm not convinced that you can say the same about Windows ;)

---

