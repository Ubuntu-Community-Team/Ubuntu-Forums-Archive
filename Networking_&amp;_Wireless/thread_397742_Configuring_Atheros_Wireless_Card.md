---
title: "Configuring Atheros Wireless Card"
date: 2007-03-31
forum: Networking &amp; Wireless
---

### Post by DistroTech on 2007-03-31
Hello all, just updated to Feisty Beta release, and it is absolutely amazing.  Kudos to all involved!

Anyway, one reason I wanted to update was in the hopes for improved hardware detection, particularly for my Atheros wireless card that was included with this computer.  It does not seem to be working at all, though it is detected by the system in some ways.

This is an HP Media Center PC m7760n, [here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00820224&lc=en&cc=us&dlc=en&query=m7760n%20&product=3339302") are the hardware stats.

The wireless card shows up in lspci as "01:03.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev01)"

iwconfig does not display an ath0 extension, neither does ifconfig.

dmesg shows this, pertaining to the Atheros modules/drivers:

ath_hal: module license 'Proprietary' taints kernel

ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF 2413, RF5413)

ath_pci: 0.9.4.5 (0.9.3)

wifi%d: unable to attach hardware: 'Hardware self-test failed' (HAL status 14)

ACPI: PCI Interrupt for device 0000:01:03.0 disabled


That last one looks like it could be the root of the problem, but I have no idea.  I'd rather not go the ndiswrapper way if possible, but if it has to happen, it has to happen.

Thanks for your help!

-DT

---

### Post by DistroTech on 2007-03-31
Bump

---

### Post by GSF1200S on 2007-03-31
> **DistroTech said:**
> Hello all, just updated to Feisty Beta release, and it is absolutely amazing.  Kudos to all involved!

Anyway, one reason I wanted to update was in the hopes for improved hardware detection, particularly for my Atheros wireless card that was included with this computer.  It does not seem to be working at all, though it is detected by the system in some ways.

This is an HP Media Center PC m7760n, [here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00820224&lc=en&cc=us&dlc=en&query=m7760n%20&product=3339302") are the hardware stats.

The wireless card shows up in lspci as "01:03.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev01)"

iwconfig does not display an ath0 extension, neither does ifconfig.

dmesg shows this, pertaining to the Atheros modules/drivers:

ath_hal: module license 'Proprietary' taints kernel

ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF 2413, RF5413)

ath_pci: 0.9.4.5 (0.9.3)

wifi%d: unable to attach hardware: 'Hardware self-test failed' (HAL status 14)

ACPI: PCI Interrupt for device 0000:01:03.0 disabled


That last one looks like it could be the root of the problem, but I have no idea.  I'd rather not go the ndiswrapper way if possible, but if it has to happen, it has to happen.

Thanks for your help!

-DT

The evil word HAL.. I have a gigabyte W101GT, and HAL is the reason I had problems. I really want to help you here, but that last line does look bad... Heres what dmesg showed me. Keep in mind the vendor is listed as Atheros Communications on my system, so we have some things in common...


 17
[   16.492000] PCI: Setting latency timer of device 0000:06:04.2 to 64
[   16.492000] mmc0: SDHCI at 0xd2100c00 irq 17 DMA
[   16.516000] ath_hal: module license 'Proprietary' taints kernel.
[   16.516000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   16.660000] tpm_inf_pnp 00:02: Found TPM with ID IFX0102
[   16.660000] tpm_inf_pnp 00:02: TPM found: config base 0x4e, io base 0x1670, chip version 0x000b, vendor id 0x15d1 (Infineon), product id 0x000b (SLB 9635 TT 1.2)
[   16.804000] wlan: 0.8.4.2 (0.9.3)
[   16.832000] ath_pci: 0.9.4.5 (0.9.3)
[   16.832000] ACPI: PCI Interrupt 0000:02:00.0[A] -> GSI 16 (level, low) -> IRQ 16
[   16.832000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[   17.348000] NET: Registered protocol family 17
[   17.400000] ath_rate_sample: 1.2 (0.9.3)
[   17.416000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   17.416000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   17.416000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   17.416000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   17.416000] wifi0: mac 10.1 phy 6.1 radio 10.2
[   17.416000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   17.416000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   17.416000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   17.416000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   17.416000] wifi0: Use hw queue 8 for CAB traffic
[   17.416000] wifi0: Use hw queue 9 for beacons
[   17.444000] wifi0: Atheros 5424/2424: mem=0xd2000000, irq=16
[   17.444000] Yenta: CardBus bridge found at 0000:06:04.0 [14c0:0020]
[   17.444000] Yenta: Using CSCINT to route CSC interrupts to PCI
[   17.444000] Yenta: Routing CardBus interrupts to PCI
[   17.444000] Yenta TI: socket 0000:06:04.0, mfunc 0x88501212, devctl 0x44
[   17.536000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 22 (level, low)

Maybe you can use this as reference.

Let me ask you a few questions.. Do you dual boot on this system? If so, does windows work with the card in question? Have you used the Synaptic Package manager to download the latest madwifi drivers? Is youre wireless card a pci card? Have you researched updating HAL?

Hopefully some of what Ive written helps, and post back when you try something. Im actually trying to create a HowTo thread on wireless, but im finding so many unique issues im having a hard time addressing it. Post back, and if I cant help you, maybe someone a bit more knowledgeable will come along...

**edit** haha, if id looked a little closer at your dmesg output, I would have seen its a pci wireless card.. scratch that one question...

---

### Post by ssc351 on 2007-04-01
Alright more people with my problem... :)  
I can't get the thing to work either...I have a rather lengthy thread going here:  
[http://www.ubuntuforums.org/showthread.php?t=384878](http://www.ubuntuforums.org/showthread.php?t=384878)

take a look maybe we can help each other.

Here is my dmesg output.

[   20.112000] intel_rng: FWH not detected
[   20.148000] ath_hal: module license 'Proprietary' taints kernel.
[   20.148000] ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413, RF5413)
[   20.256000] wlan: 0.8.4.2 (0.9.3)
[   20.292000] ath_pci: 0.9.4.5 (0.9.3)
[   20.292000] ACPI: PCI Interrupt 0000:0c:00.0[A] -> GSI 17 (level, low) -> IRQ 17
[   20.292000] PCI: Setting latency timer of device 0000:0c:00.0 to 64
[   20.904000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000
[   20.924000] ath_rate_sample: 1.2 (0.9.3)
[   20.928000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[   20.928000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   20.928000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[   20.928000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[   20.928000] wifi0: mac 10.1 phy 6.1 radio 10.2
[   20.928000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[   20.928000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[   20.928000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[   20.928000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[   20.928000] wifi0: Use hw queue 8 for CAB traffic
[   20.928000] wifi0: Use hw queue 9 for beacons
[   20.936000] sdhci: Secure Digital Host Controller Interface driver
[   20.936000] sdhci: Copyright(c) Pierre Ossman
[   20.940000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   20.996000] wifi0: Atheros 5424/2424: mem=0xefdf0000, irq=17
[   20.996000] sdhci: SDHCI controller found at 0000:02:01.1 [1180:0822] (rev 19)
[   20.996000] ACPI: PCI Interrupt 0000:02:01.1[B] -> GSI 18 (level, low) -> IRQ 23
[   20.996000] mmc0: SDHCI at 0xef9fd400 irq 23 DMA
[   21.088000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 21 (level, low) -> IRQ 20
[   21.088000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[   21.612000] b44: eth0: Link is up at 100 Mbps, full duplex.
[   21.612000] b44: eth0: Flow control is off for TX and off for RX.
[   21.668000] lp: driver loaded but no devices found
[   21.808000] Adding 2522164k swap on /dev/disk/by-uuid/831402f6-c4c9-4a36-bb92-8d46d9ebc6a0.  Priority:-1 extents:1 across:2522164k
[   21.884000] EXT3 FS on sda6, internal journal

---

### Post by DistroTech on 2007-04-01
Sorry about the totally untimely reply!

Anyway, in regards to GSF: 
-Yes, I dual boot Vista on this, and the card works very well with it.  
-I am in the process of updating MADWIFI now, and I have also researched updating HAL, and will do so if necessary.

In regards to SSC,
-Holy crap, you've been trying to tackle this for two weeks...ridiculous.  Sorry it hasn't worked for you man!

I think the difference between our three dmesg outputs is that you both receive wifi signal responses, while I do not.  I don't get to the wifi stage where it can receive, and it almost seems like ACPI is killing it for some strange reason.

I'll update MADWIFI and post back.

-DT

---

### Post by stchman on 2007-04-02
> **DistroTech said:**
> Hello all, just updated to Feisty Beta release, and it is absolutely amazing.  Kudos to all involved!

Anyway, one reason I wanted to update was in the hopes for improved hardware detection, particularly for my Atheros wireless card that was included with this computer.  It does not seem to be working at all, though it is detected by the system in some ways.

This is an HP Media Center PC m7760n, [here]("http://h10025.www1.hp.com/ewfrf/wc/document?docname=c00820224&lc=en&cc=us&dlc=en&query=m7760n%20&product=3339302") are the hardware stats.

The wireless card shows up in lspci as "01:03.0 Ethernet controller: Atheros Communications, Inc. AR5006X 802.11abg NIC (rev01)"

iwconfig does not display an ath0 extension, neither does ifconfig.

dmesg shows this, pertaining to the Atheros modules/drivers:

ath_hal: module license 'Proprietary' taints kernel

ath_hal: 0.9.18.0 (AR5210, AR5211, AR5212, RF5111, RF5112, RF 2413, RF5413)

ath_pci: 0.9.4.5 (0.9.3)

wifi%d: unable to attach hardware: 'Hardware self-test failed' (HAL status 14)

ACPI: PCI Interrupt for device 0000:01:03.0 disabled


That last one looks like it could be the root of the problem, but I have no idea.  I'd rather not go the ndiswrapper way if possible, but if it has to happen, it has to happen.

Thanks for your help!

-DT

I had the same problem with my Toshiba laptop using 6.10.  Edgy kernel is madwifi and Atheros compatible but for the newer Atheros cards you will need to install the madwifi drivers.

I have the procedure laid out to install the latest madwifi drivers on my website:

[http://www.stchman.com/ath_drv.html](http://www.stchman.com/ath_drv.html)

I hope this helps.

---

### Post by DistroTech on 2007-04-03
Following your procedure, I still cannot seem to get this to work...

I'm not sure if it is actually installing the new version, and I might be misunderstanding the first part of your guide about identifying the compatible kernel modules.

I have also tried ndiswrapper, just to see if it would work, and it just jumbled things into a mess.  Now dmesg is going nuts with ndiswrapper output, even though I've uninstalled the modules...

Might be time to buy a wireless bridge.

Also, in addition to following your steps on installing from source, I tried installing from debian packages...this also did not seem to work.

-DT

---

