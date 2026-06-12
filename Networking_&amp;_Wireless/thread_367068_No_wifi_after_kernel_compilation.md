---
title: "No wifi after kernel compilation"
date: 2007-02-21
forum: Networking &amp; Wireless
---

### Post by v_oo_v on 2007-02-21
Hi,

I have just compiled the 2.6.20 Kernel onto ubuntu Dapper 6.06.

At first glance, everything seemd to be OK until I inserted my PCMCIA Proxim Orinoco Gold Wi - Fi card.

The system detects it when inserted:

> #lspci -v

0000:07:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: [COLOR="Red"]PROXIM Inc[/COLOR]: Unknown device 0a40
        Flags: medium devsel, IRQ 17
        Memory at 58000000 (32-bit, non-prefetchable) [disabled] [size=64K]
        Capabilities: <available only to root

And the cardbus also detects it when inserted:

> 
#dmesg

[ 2700.360000] pccard: CardBus card inserted into slot 0

On the contrary, when I boot up with 2.6.15-28 kernel, it works perfectly OK:

> #lspci -v

0000:07:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)
        Subsystem: [COLOR="Red"]PROXIM[/COLOR] Inc: Unknown device 0a40
        Flags: bus master, medium devsel, latency 168, IRQ 177
        Memory at 54000000 (32-bit, non-prefetchable) [size=64K]
        Capabilities: <available only to root>


And the dmesg output:

> #dmesg:

17179650.308000] pccard: CardBus card inserted into slot 0
[17179650.392000] ath_hal: module license 'Proprietary' taints kernel.
[17179650.392000] ath_hal: 0.9.14.9 (AR5210, AR5211, AR5212, RF5111, RF5112, RF2413)
[17179650.416000] wlan: 0.8.6.0 (EXPERIMENTAL)
[17179650.420000] ath_rate_sample: 1.2
[17179650.428000] ath_pci: 0.9.6.0 (EXPERIMENTAL)
[17179650.428000] PCI: Enabling device 0000:07:00.0 (0000 -> 0002)
[17179650.428000] ACPI: PCI Interrupt 0000:07:00.0[A] -> GSI 22 (level, low) -> IRQ 177
[17179650.768000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17179650.848000] Build date: Feb  1 2007
[17179650.848000] Debugging version (IEEE80211)
[17179650.848000] ath0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17179650.848000] ath0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179650.848000] ath0: turboG rates: 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17179650.848000] ath0: H/W encryption support: WEP AES AES_CCM TKIP
[17179650.848000] ath0: mac 5.9 phy 4.3 radio 4.6
[17179650.848000] ath0: Use hw queue 1 for WME_AC_BE traffic
[17179650.848000] ath0: Use hw queue 0 for WME_AC_BK traffic
[17179650.848000] ath0: Use hw queue 2 for WME_AC_VI traffic
[17179650.848000] ath0: Use hw queue 3 for WME_AC_VO traffic
[17179650.848000] ath0: Use hw queue 8 for CAB traffic
[17179650.848000] ath0: Use hw queue 9 for beacons
[17179650.848000] Debugging version (ATH)
[17179650.848000] ath0: Atheros 5212: mem=0x54000000, irq=177
[17179650.880000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17179652.984000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17179652.996000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17179655.044000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17179655.060000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17179657.184000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17179657.232000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17179659.300000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17179659.324000] hdb: error code: 0x70  sense_key: 0x02  asc: 0x30  ascq: 0x00
[17179661.280000] ath0: no IPv6 routers present




It seems I have forgotten something important...could anyone assist me? This is not a critical issue as I can fire up with the default 2.6.15 kernel but I need to test the KVM module.

This is for the Proxim card. Also, I have a 2200BG intel wireless card onboard, but probably the problem is the same for both cards.

Thanks in advance.

---

### Post by angryfirelord on 2007-02-21
If you compiled it yourself (meaning that you went to kernel.org & got one of those), then the madwifi modules aren't there. You'll have to set it up manually. The kernel can detect the card, but it doesn't know what else to do with it.

[http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233]("http://sourceforge.net/project/showfiles.php?group_id=82936&package_id=85233")

---

