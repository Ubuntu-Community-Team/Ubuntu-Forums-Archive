---
title: "wlan0 not in Network Connections"
date: 2007-01-13
forum: Networking &amp; Wireless
---

### Post by DeltaS on 2007-01-13
Like many posting here, I'm a newcomer to Linux. Acquired a Dell Latitude CPx, installed Ubuntu 6.10 after scraping off XP, picked up an INPROCOMM wireless card, and after much reading and many false starts installed a driver using ndiswrapper. A card image with a checkmark beside it shows in the Networking window, so I think it's working. Hardwire ethernet through another card is working fine (on the same router), but I can't access the wireless network on my Netgear WNR834B router. The router works (wireless) with a Macbook and an HP laptop, so I assume I've not set the Unbuntu system properly.

Here's the printout from wconfig:

~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

wlan0     Auto  ESSID:off/any  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

And from ifconfig:
~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0F:B5:43:D6:8A  
          inet addr:192.168.10.20  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe43:d68a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2211 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2049 errors:1 dropped:0 overruns:0 carrier:2
          collisions:0 txqueuelen:1000 
          RX bytes:2025678 (1.9 MiB)  TX bytes:275822 (269.3 KiB)
          Interrupt:11 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:158 errors:0 dropped:0 overruns:0 frame:0
          TX packets:158 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:13858 (13.5 KiB)  TX bytes:13858 (13.5 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:03:6D:20:DE:A0  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:22000000-22000800 

Under "Network Connections" only the two options eth1 and lo appear - not wlan0. When I select the wireless card in System-Networking, there's no "wlan0" option available to select in Connections. That has to be a problem - I assume "lo" means local - but wlan0 isn't there. 

Looks like there may be a conflict between eth0 and wlan0 (same interrupt #11), but I have no idea what that means or how to change one of them:
 sudo cat /proc/interrupts
           CPU0       
  0:     115294          XT-PIC  timer
  1:         93          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:       5883          XT-PIC  ESS Maestro
  7:        266          XT-PIC  parport0
  8:          3          XT-PIC  rtc
  9:          1          XT-PIC  acpi
 11:       2758          XT-PIC  uhci_hcd:usb1, yenta, yenta, eth1, wlan0
 12:       3165          XT-PIC  i8042
 14:       5650          XT-PIC  ide0
 15:       3017          XT-PIC  ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

So I pulled out the hardwire ethernet card and restarted, hoping that the wireless card would work, but no luck. Now the Network Connection won't open - "SIOCGIFFLAGS error: No such device".  Meanwhile, as I type, the light on the wireless card flashes for a few seconds, goes out, flashes again - appears to be looking for something it isn't finding.

Restarted with both cards inserted.

Another forum entry suggested running dmesg. The product was huge, but here are a couple of "significant" lines (I think :-):
[17179606.616000] pccard: CardBus card inserted into slot 0
[17179606.724000] pccard: CardBus card inserted into slot 1

[17179616.004000] ndiswrapper: driver neti2220 (INPROCOMM,02/24/2005,3.07.02.2005) loaded
[17179616.004000] PCI: Enabling device 0000:02:00.0 (0000 -> 0003)
[17179616.004000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179616.008000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179616.044000] ndiswrapper: using IRQ 11
[17179616.544000] wlan0: ethernet device 00:03:6d:20:de:a0 using NDIS driver: neti2220, version: 0x30007, NDIS version: 0x501, vendor: 'INPROCOMM IPN2220 Wireless LAN Adapter', 17FE:2220.5.conf
[17179616.544000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

Probably something stupid that I'm missing, but my knowledge of Linux is "challenged" to say the least - please keep that in mind if you reply.

Thanks for any hints.  
 Gramps

---

### Post by DeltaS on 2007-01-14
Other obvious things I've done (in case you think I'd missed these):
Network Settings - highlighted wireless card, configured with network name and password in Properties - card image is checked, Essid: shows net, Address: shows DHCP - all appears OK, BUT when I open Network Connection in the menu bar, under Connection, wlan0 does not appear !??

---

