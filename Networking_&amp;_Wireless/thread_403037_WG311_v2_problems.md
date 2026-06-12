---
title: "WG311 v2 problems"
date: 2007-04-06
forum: Networking &amp; Wireless
---

### Post by Kuroyume on 2007-04-06
I have a WG311 v2 PCI card, wich uses the TI acx 111 chipset, and the acx driver

i managed to get the card working and running WEP, however every once in a while it will drop the connection and be unable to reconnect until i reboot. This usually happens when there is heavier traffic on the card.

i am running the Feisty beta, with kernel 2.6.20-13

this is the output of dmesg | grep acx after a crash:

```
[   15.728000] acx: Loaded combined PCI/USB driver, firmware_ver=default
[   15.728000] acx: compiled to use 32bit I/O access. I/O timing issues might occur, such as non-working firmware upload. Report them
[   15.728000] acx: found ACX111-based wireless network card at 0000:04:08.0, irq:21, phymem1:0xFDCFC000, phymem2:0xFDCC0000, mem1:0xf8a9c000, mem1_size:8192, mem2:0xf8b40000, mem2_size:131072
[   15.728000] acx: loading firmware for acx1111 chipset with radio ID 16
[   16.496000] acx: === chipset TNETW1130, radio type 0x16 (Radia), form factor 0x01 ((mini-)PCI / CardBus), EEPROM version 0x05: uploaded firmware 'Rev 1.2.1.34' ===
[   16.496000] acx v0.3.36: net device wlan0, driver compiled against wireless extensions 21 and Linux 2.6.20-13-generic
[   16.496000] usbcore: registered new interface driver acx_usb
[ 2351.312000] acx: BUG: no free txdesc left
[ 2353.812000] acx: BUG: no free txdesc left
[ 2356.312000] acx: BUG: no free txdesc left
[ 2358.812000] acx: BUG: no free txdesc left
[ 2361.312000] acx: BUG: no free txdesc left
[ 2372.324000] acx: BUG: no free txdesc left
[ 2373.824000] acx: BUG: no free txdesc left
[ 2376.324000] acx: BUG: no free txdesc left
[ 2378.824000] acx: BUG: no free txdesc left
[ 2394.476000] acx: BUG: no free txdesc left
[ 2395.976000] acx: BUG: no free txdesc left
[ 2398.476000] acx: BUG: no free txdesc left
[ 2400.980000] acx: BUG: no free txdesc left
[ 2403.480000] acx: BUG: no free txdesc left
[ 2403.884000] acx: BUG: no free txdesc left
[ 2403.884000] acx: BUG: no free txdesc left
[ 2403.884000] acx: BUG: no free txdesc left
[ 2403.888000] acx: BUG: no free txdesc left
[ 2403.888000] acx: BUG: no free txdesc left
[ 2403.888000] acx: BUG: no free txdesc left
[ 2403.896000] acx: BUG: no free txdesc left
[ 2403.896000] acx: BUG: no free txdesc left
[ 2403.896000] acx: BUG: no free txdesc left
[ 2403.900000] acx: BUG: no free txdesc left
[ 2403.900000] acx: BUG: no free txdesc left
[ 2403.904000] acx: BUG: no free txdesc left
[ 2403.904000] acx: BUG: no free txdesc left
[ 2403.904000] acx: BUG: no free txdesc left
[ 2403.908000] acx: BUG: no free txdesc left
[ 2405.408000] acx: BUG: no free txdesc left
[ 2407.908000] acx: BUG: no free txdesc left
[ 2410.408000] acx: BUG: no free txdesc left
[ 2412.908000] acx: BUG: no free txdesc left
[ 2415.408000] acx: BUG: no free txdesc left
[ 2417.908000] acx: BUG: no free txdesc left
[ 2420.408000] acx: BUG: no free txdesc left
[ 2422.908000] acx: BUG: no free txdesc left
[ 2425.408000] acx: BUG: no free txdesc left
[ 2430.472000] acx: BUG: no free txdesc left
[ 2431.972000] acx: BUG: no free txdesc left
[ 2434.472000] acx: BUG: no free txdesc left
[ 2436.972000] acx: BUG: no free txdesc left
[ 2439.472000] acx: BUG: no free txdesc left
[ 2441.972000] acx: BUG: no free txdesc left
[ 2444.472000] acx: BUG: no free txdesc left
[ 2446.972000] acx: BUG: no free txdesc left
[ 2449.472000] acx: BUG: no free txdesc left
[ 2451.972000] acx: BUG: no free txdesc left
[ 2457.036000] acx: BUG: no free txdesc left
[ 2458.536000] acx: BUG: no free txdesc left
[ 2461.036000] acx: BUG: no free txdesc left
[ 2463.536000] acx: BUG: no free txdesc left
[ 2466.036000] acx: BUG: no free txdesc left
[ 2468.536000] acx: BUG: no free txdesc left
[ 2471.036000] acx: BUG: no free txdesc left
[ 2473.536000] acx: BUG: no free txdesc left
[ 2476.036000] acx: BUG: no free txdesc left
[ 2478.536000] acx: BUG: no free txdesc left
[ 2483.704000] acx: BUG: no free txdesc left
[ 2485.204000] acx: BUG: no free txdesc left
[ 2487.704000] acx: BUG: no free txdesc left
[ 2490.204000] acx: BUG: no free txdesc left
[ 2492.704000] acx: BUG: no free txdesc left
[ 2495.204000] acx: BUG: no free txdesc left
[ 2497.704000] acx: BUG: no free txdesc left
[ 2500.204000] acx: BUG: no free txdesc left
[ 2503.236000] acx: BUG: no free txdesc left
[ 2504.736000] acx: BUG: no free txdesc left
[ 2507.236000] acx: BUG: no free txdesc left
[ 2509.736000] acx: BUG: no free txdesc left
[ 2512.236000] acx: BUG: no free txdesc left
[ 2514.736000] acx: BUG: no free txdesc left
[ 2517.236000] acx: BUG: no free txdesc left
[ 2519.736000] acx: BUG: no free txdesc left
[ 2522.236000] acx: BUG: no free txdesc left
[ 2524.736000] acx: BUG: no free txdesc left
[ 2529.800000] acx: BUG: no free txdesc left
[ 2531.300000] acx: BUG: no free txdesc left
[ 2533.800000] acx: BUG: no free txdesc left
[ 2536.300000] acx: BUG: no free txdesc left
[ 2538.800000] acx: BUG: no free txdesc left
[ 2541.300000] acx: BUG: no free txdesc left
[ 2543.800000] acx: BUG: no free txdesc left
[ 2546.300000] acx: BUG: no free txdesc left
[ 2548.800000] acx: BUG: no free txdesc left
[ 2551.300000] acx: BUG: no free txdesc left
[ 2556.260000] acx: BUG: no free txdesc left
[ 2557.760000] acx: BUG: no free txdesc left
[ 2560.260000] acx: BUG: no free txdesc left
[ 2562.760000] acx: BUG: no free txdesc left
[ 2565.260000] acx: BUG: no free txdesc left
[ 2567.760000] acx: BUG: no free txdesc left
[ 2570.260000] acx: BUG: no free txdesc left
[ 2572.760000] acx: BUG: no free txdesc left
[ 2575.260000] acx: BUG: no free txdesc left
[ 2577.760000] acx: BUG: no free txdesc left
[ 2582.516000] acx: BUG: no free txdesc left
[ 2584.016000] acx: BUG: no free txdesc left
[ 2586.516000] acx: BUG: no free txdesc left
[ 2589.016000] acx: BUG: no free txdesc left
[ 2591.516000] acx: BUG: no free txdesc left
[ 2594.016000] acx: BUG: no free txdesc left
[ 2596.516000] acx: BUG: no free txdesc left
[ 2599.016000] acx: BUG: no free txdesc left

```

---

### Post by MeneM on 2007-04-06
**This post could be related to an Ubuntu bug filed at**: [https://answers.launchpad.net/ubuntu/+ticket/3134](https://answers.launchpad.net/ubuntu/+ticket/3134) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Hi,

According to this great page: [http://linux-wless.passys.nl/]("http://linux-wless.passys.nl/query_part.php?brandname=Netgear") the WG 311 v2 is not very well suited for use with Linux.

You see, some companies sell hardware that dont actually do what they said it would do upon selling it. In these cases the software (Almost always only windows-based) does most of the actual work which supposedly the card should be doing...

So is the case with your WG311, it does not really do it's job.

May I suggest a card that appears "[COLOR="Lime"]green[/COLOR]" in the list?

Other than that: [https://answers.launchpad.net/]("https://answers.launchpad.net/ubuntu/+ticket/3134")

---

### Post by Kuroyume on 2007-04-07
thanks for the reply... i would like to keep my hardware, as it is expensive here in Chile for a college student... after some reading i have come to believe that itight be an IRQ conflict with my nvidia graphics card, as other people have reported that has been the case for them.

I tried moving the card to a different slot, and it didn't work, and i have to admit i have no idea how to manually assign irq's...

here is the relevant output of lspci -vv

```


03:00.0 VGA compatible controller: nVidia Corporation G70 [GeForce 7300 GT] (rev a1) (prog-if 00 [VGA])
        Subsystem: eVga.com. Corp. Unknown device c445
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=fast >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 0
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at fa000000 (32-bit, non-prefetchable) [size=16M]
        Region 1: Memory at d0000000 (64-bit, prefetchable) [size=256M]
        Region 3: Memory at fb000000 (64-bit, non-prefetchable) [size=16M]
        Region 5: I/O ports at bc00 [size=128]
        [virtual] Expansion ROM at fcfe0000 [disabled] [size=128K]
        Capabilities: <access denied>


04:08.0 Network controller: Texas Instruments ACX 111 54Mbps Wireless Interface
        Subsystem: Netgear Unknown device 4c00
        Control: I/O+ Mem+ BusMaster+ SpecCycle- MemWINV- VGASnoop- ParErr- Stepping- SERR- FastB2B-
        Status: Cap+ 66MHz- UDF- FastB2B- ParErr- DEVSEL=medium >TAbort- <TAbort- <MAbort- >SERR- <PERR-
        Latency: 32, Cache Line Size: 32 bytes
        Interrupt: pin A routed to IRQ 21
        Region 0: Memory at fdcfc000 (32-bit, non-prefetchable) [size=8K]
        Region 1: Memory at fdcc0000 (32-bit, non-prefetchable) [size=128K]
        Capabilities: <access denied>
```

also, looks like upgrading to the 2.6.20-14 kernel improved this. I managed to have it work overnight, only to fail this morning...

---

### Post by MeneM on 2007-04-07
I'd try the BIOS. I've never manhandled IRQ settings in Linux before, and do not really believe it will be worth your effort.

You might try Feisty Fawn though. It has all kinds of extra goodies, the solution for your issue, may be one of them.

---

