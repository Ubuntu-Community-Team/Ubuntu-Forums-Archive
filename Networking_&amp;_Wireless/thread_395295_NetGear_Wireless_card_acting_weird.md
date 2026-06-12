---
title: "NetGear Wireless card acting weird"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by robinhoode on 2007-03-28
Hey everyone,

  I have a NetGear WPN511 running in laptop's PCI slot (with Edgy), and it's acting kinda weird. Normally I run through a wired connection at my house, but I sometimes use the wireless network at my friend's house or at work. At those times, it acts fine. But at my house, the power seems to cut in and out, going from one light to none, then back, stopping the flow of all applications.

  The only thing I know that remedies this is to turn the device off through **System** -> **Admin** -> **Networking.** When I do this, I can't seem to 'start it up' immediately, say when I'm at my friend's house, so I prefer not to have to do that. In light of this, I tried a few **iwconfig** commands, such as **essid** **off** and **twpower** **off** but no luck.

  BTW Is there any way to disable the device from the command line instead of the GUI?

  When the light is off, it shows this on **iwconfig:**

robinhoode@robinhoode-laptop:~/Desktop$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.


and this when it's on:

  robinhoode@robinhoode-laptop:~/Desktop$ **iwconfig**
lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     no wireless extensions.

sit0      no wireless extensions.

wifi0     no wireless extensions.

ath0      IEEE 802.11b  ESSID:""  
          Mode:Managed  Channel:0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:0 dBm   Sensitivity=0/3  
          Retry:off   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=0/94  Signal level=-95 dBm  Noise level=-95 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0


Also, here's some stuff from my **dmesg:**

[17219029.968000] ACPI: PCI Interrupt 0000:04:00.0[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[17219030.576000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17219030.576000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17219030.576000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17219030.576000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17219030.576000] wifi0: mac 7.9 phy 4.5 radio 5.6
[17219030.576000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17219030.576000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17219030.576000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17219030.576000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17219030.576000] wifi0: Use hw queue 8 for CAB traffic
[17219030.576000] wifi0: Use hw queue 9 for beacons
[17219030.576000] wifi0: Atheros 5212: mem=0x28000000, irq=11
[17219031.444000] pccard: card ejected from slot 1
[17219031.540000] ACPI: PCI interrupt for device 0000:04:00.0 disabled
[17219032.416000] pccard: CardBus card inserted into slot 1
[17219032.416000] PCI: Enabling device 0000:04:00.0 (0000 -> 0002)
[17219032.416000] ACPI: PCI Interrupt 0000:04:00.0[A] -> Link [C0C3] -> GSI 11 (level, low) -> IRQ 11
[17219033.020000] wifi0: 11b rates: 1Mbps 2Mbps 5.5Mbps 11Mbps
[17219033.020000] wifi0: 11g rates: 1Mbps 2Mbps 5.5Mbps 11Mbps 6Mbps 9Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17219033.020000] wifi0: turboG rates: 6Mbps 12Mbps 18Mbps 24Mbps 36Mbps 48Mbps 54Mbps
[17219033.020000] wifi0: H/W encryption support: WEP AES AES_CCM TKIP
[17219033.020000] wifi0: mac 7.9 phy 4.5 radio 5.6
[17219033.020000] wifi0: Use hw queue 1 for WME_AC_BE traffic
[17219033.020000] wifi0: Use hw queue 0 for WME_AC_BK traffic
[17219033.020000] wifi0: Use hw queue 2 for WME_AC_VI traffic
[17219033.020000] wifi0: Use hw queue 3 for WME_AC_VO traffic
[17219033.020000] wifi0: Use hw queue 8 for CAB traffic
[17219033.020000] wifi0: Use hw queue 9 for beacons
[17219033.024000] wifi0: Atheros 5212: mem=0x28000000, irq=11


And here's my **lspci** (caught it with the light on, so the last line showed the card):

robinhoode@robinhoode-laptop:~/Desktop$ **lspci**
00:00.0 Host bridge: Intel Corporation 82845 845 (Brookdale) Chipset Host Bridge (rev 04)
00:01.0 PCI bridge: Intel Corporation 82845 845 (Brookdale) Chipset AGP Bridge (rev 04)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 42)
00:1f.0 ISA bridge: Intel Corporation 82801CAM ISA Bridge (LPC) (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801CAM IDE U100 (rev 02)
00:1f.5 Multimedia audio controller: Intel Corporation 82801CA/CAM AC'97 Audio Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]
02:04.0 Communication controller: Agere Systems LT WinModem (rev 02)
02:06.0 CardBus bridge: Texas Instruments PCI1420
02:06.1 CardBus bridge: Texas Instruments PCI1420
02:08.0 Ethernet controller: Intel Corporation 82801CAM (ICH3) PRO/100 VM (KM) Ethernet Controller (rev 42)
02:0e.0 USB Controller: NEC Corporation USB (rev 41)
02:0e.1 USB Controller: NEC Corporation USB (rev 41)
02:0e.2 USB Controller: NEC Corporation USB 2.0 (rev 02)
04:00.0 Ethernet controller: Atheros Communications, Inc. AR5212 802.11abg NIC (rev 01)

I know I might have posted too much, but I'm hoping that someone can spot what's wrong!

Thanks for the help in advance!

-Rob

---

