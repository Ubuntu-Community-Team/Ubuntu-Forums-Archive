---
title: "Intersil Prism 2.5 Major Issue on Thinkpad X30"
date: 2007-11-08
forum: Networking &amp; Wireless
---

### Post by cjastram on 2007-11-08
Hi folks,

I have an IBM ThinkPad X30 with the builtin minipci wireless card.  On previous editions of ubuntu, I've had to blacklist hostap and use either the orinoco or the prism2 drivers.  However, these do not appear to be functional in gutsy 7.10....argh!  So, here's the information;
[B]
Relevant dmesg output:[/B]
```
[ 1577.468000] hostap_pci: 0.4.4-kernel (Jouni Malinen <j@w1.fi>)
[ 1577.472000] ACPI: PCI Interrupt 0000:01:02.0[A] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[ 1577.472000] hostap_pci: Registered netdevice wifi0
[ 1577.472000] wifi0: Original COR value: 0x20
[ 1577.484000] prism2_hw_init: initialized in 8 ms
[ 1577.484000] wifi0: NIC: id=0x8013 v1.0.0
[ 1577.484000] wifi0: PRI: id=0x15 v1.1.0
[ 1577.484000] Could not get RID for component STA
[ 1577.484000] wifi0: Failed to read STA f/w version - only Primary f/w present
[ 1577.484000] wifi0: Intersil Prism2.5 PCI: mem=0xf8000000, irq=11
[ 1577.484000] wifi0: registered netdevice wlan0
[ 1577.680000] wlan0: CMD=0x0001 => res=0x7f, resp0=0x0001
[ 1577.680000] wlan0: MAC port 0 enabling failed
[ 1577.680000] wlan0: could not enable MAC port

```

A lot of people have had the "Could not get RID for component STA" trouble.  Most of them were posting 3-5 years ago, and the solutions, such as I have found, do not seem to apply currently.  In particular, I seem to be unable to flash firmware (because of this error).

**lspci -vv says**
```
01:02.0 Network controller: Intersil Corporation Prism 2.5 Wavelan chipset (rev 01)
        Subsystem: Intel Corporation Wireless 802.11b MiniPCI Adapter
        Control: I/O+ Mem+ BusMaster- SpecCycle- MemWINV+ VGASnoop- ParErr- Stepping- SERR+ FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B+ ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Interrupt: pin A routed to IRQ 11
        Region 0: Memory at f8000000 (32-bit, prefetchable) [size=4K]
        Capabilities: [dc] Power Management version 2
                Flags: PMEClk- DSI- D1+ D2+ AuxCurrent=0mA PME(D0+,D1+,D2+,D3hot+,D3cold-)
                Status: D0 PME-Enable- DSel=0 DScale=0 PME-

```

**And of course, iwconfig, fwiw:**
```
wifi0     IEEE 802.11-DS  Mode:Managed  
          Encryption key:off
          
wlan0     no wireless extensions.

```

Can anyone help with this problem?

Thanks!

Chris

---

### Post by cjastram on 2007-11-08
....aaaand 10 genius points for not posting the basic symptoms.....

NetworkManager does see the card as a wireless card.  However, it doesn't set WEP or ESSID settings.  iwconfig/iwlist/etcetera give different error messages, usually "invalid argument."

So, it is actually seen as a wireless card, but it is completely nonfunctional for anything useful.

Yay, this is a bothersome little problem.  Help!

---

### Post by cjastram on 2007-11-11
Arrrgh, I cannot get any firmware to upload.  I think this is a dead end, anyway, because it worked before I upgraded.

Can anybody help?

Chris

---

### Post by cjastram on 2007-11-12
Does anyone know how to get the orinoco drivers working?

---

### Post by bigredradio on 2008-01-31
Did you ever get a resolution to this problem? I have run into the same issue on my Fujitsu Lifebook.

---

### Post by cjastram on 2008-02-01
No, I did not manage to get everything working.  Very nasty situation, IMO.

I ended up digging out an ancient D-Link DE-528 PCMCIA card, and it works with the default Ubuntu drivers.

Oddly enough, the DE-528 card is a Prism chipset...

I noticed last week that the default driver for that card is NOT "prism2_pci", but rather "p54".  The p54 driver appears to belong to a new project that seems to be under much more active development.  I'm not sure if this new project is a complete re-write from scratch, but they seem to be re-supporting lots and lots of cards that used to be supported with a different driver.

So.... the old drivers seem to be broken.  Prism2 and Prism54.org and islsm and all those bad boys are deprecated and outdated.  Effort is going into new drivers.  The new drivers don't seem to support all the cards.  Development is ongoing, and more cards are being supported all the time. 

I'm currently building the latest kernel, in the hopes that my wireless will once again be functional.

See [http://linuxwireless.org/](http://linuxwireless.org/) ... that seems to be the new wireless stack home page, but it's somewhat light on information.

HTH, I'll try to post the results if anyone is interested.

cej102937

---

### Post by bigredradio on 2008-02-01
I got it working finally. Actually took an update to the firmware of the wireless card. Here is a link to info on how to update it. Then use the hostap module.

[http://linux.junsun.net/intersil-prism/](http://linux.junsun.net/intersil-prism/)

In /etc/modules I added:

hostap
hostap_pci

In /etc/modprobe.d/blacklist I have:

blacklist prism2_pci
blacklist orinoco
blacklist orinoco_pci

It even works with Network Manager, (although I had to use manual setup).

Good Luck.

---

### Post by herr_keuner on 2008-02-08
I ran into exactly the same problem. Isn't there an easier way than upgrading the firmware of the wireless card? I tried to use wicd, but that didn't work either. Has someone found out another alternative?

---

### Post by bigredradio on 2008-02-14
It really was not that difficult to upgrade the firmware. Little scary, but rather easy and painless. I hope you can find an alternate solution, but the upgrade was not major surgery.

---

### Post by winstonwl on 2008-03-15
Hi-

Maybe you could try RAM download firmware like I did for a PCI card that was
acting that way.

The problem I had was with a Linksys WMP11 PCI card that had an older version
of the firmware on the card (PRI 1.0.5 and STA 1.3.4). When I tried to bring the
card up with Knoppix ver 5.2, it would lock the machine up when I brought up the
hostap_pci module. It would also report it could not find the STA firmware. I sort
of figured out a way around having to flash the firmware, you may want to give this
procedure a try.

1. Add the following lines to /etc/modprobe.d/blacklist
blacklist orinoco
blacklist orinoco_pci
blacklist prism2_pci

blacklist hostap
blacklist hostap_pci

Then issue these commands to load the hostap modules:

modprobe hostap
modprobe hostap no_primary=1

The no_primary=1 option will not load firmware when the module loads.


2. Obtain the RAM Download firmware. I would recommend 1.1.1 and 1.7.4 to
test and make sure this procedure even works. You can always switch versions later.
Issue these commands with prism2_srec to load the firmware to the card:

To load the primary firmware first:
prism2_srec -vv -gp -O /proc/net/hostap/wlan0/pda wlan0 ak010101.hex

This will load the primary firmware, but leave the card in Genesis mode.

Then, load the secondary firmware:
prism2_srec -vv -rp -O /proc/net/hostap/wlan0/pda wlan0 rf010704.hex

This will load the secondary firmware, and place the card in run mode.

prism2_srec should report success with loading the firmware.

NIC: id=0x8013 v1.0.0
PRI: id=0x15   v1.1.1
STA: id=0x1f   v1.7.4

Give this procedure a try. The place where I got the info from tried it on several
PCI and miniPCI cards that were having this similar problem.

---

