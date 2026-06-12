---
title: "Connection Properties problem (6.10)"
date: 2007-01-16
forum: Networking &amp; Wireless
---

### Post by DeltaS on 2007-01-16
I only see "eth1" and "lo" as optional connections in the Connection Properties panel, even if there's a configured modem card or a configured wireless card in the PCI slots of my Dell Latitude laptop. Must be missing something simple, but can't figure it. New with Linux, too - please go easy in responses.
Thanks!

---

### Post by lukew on 2007-01-16
> **DeltaS said:**
> I only see "eth1" and "lo" as optional connections in the Connection Properties panel, even if there's a configured modem card or a configured wireless card in the PCI slots of my Dell Latitude laptop. Must be missing something simple, but can't figure it. New with Linux, too - please go easy in responses.
Thanks!

lspci /lsusb will list devices which are recognized but not configured. For example if you need to use ndswrapper but have not done so the card will be listed under lsusb / lspci but not within the network items. 

What do you mean by you the card is configured? What steps have you taken so far?

Thanks

Luke

---

### Post by lukew on 2007-01-16
The card will appear as a network device in the network admin GUI once the correct drivers have been installed.

---

### Post by DeltaS on 2007-01-18
lspci shows these lines for the wired and wireless cards:

02:00.0 Ethernet controller: Linksys, A Division of Cisco Systems [AirConn] INPROCOMM IPN 2220 Wireless LAN Adapter (rev 01)
06:00.0 Ethernet controller: Linksys 21x4x DEC-Tulip compatible 10/100 Ethernet (rev 11)

The wired connection has worked all along, I assume using a driver built in to 6.10. I used ndiswrapper to install a driver from the CD that came with the wireless card. It appears to have been a successful install - here's the output from ifconfig:

adp@adp-laptop:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:0F:B5:43:D6:8A  
          inet addr:192.168.10.20  Bcast:192.168.10.255  Mask:255.255.255.0
          inet6 addr: fe80::20f:b5ff:fe43:d68a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:453 errors:0 dropped:0 overruns:0 frame:0
          TX packets:444 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:452656 (442.0 KiB)  TX bytes:53439 (52.1 KiB)
          Interrupt:11 Base address:0x1800 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:68 errors:0 dropped:0 overruns:0 frame:0
          TX packets:68 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5276 (5.1 KiB)  TX bytes:5276 (5.1 KiB)

wlan0     Link encap:Ethernet  HWaddr 00:03:6D:20:DE:A0  
          inet6 addr: fe80::203:6dff:fe20:dea0/64 Scope:Link
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:3 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:11 Memory:22000000-22000800 

This is iwconfig:

adp@adp-laptop:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

wlan0     Auto  ESSID:off/any  
          Mode:Managed  Frequency:2.422 GHz  Access Point: Not-Associated   
          Bit Rate:1 Mb/s   Tx-Power:0 dBm   
          RTS thr:2347 B   Fragment thr:2346 B   
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

In the System - Admin - Networking GUI, three icons are now showing (Wireless, Wired and Modem), each has a checkmark beside it, and I configured the wireless with the net name and login for my wireless system. Below the Wireless connection icon are Essid: <netname> Address: DHCP. Below the Modem connection icon are my ISP phone number and login name.

But neither the Wireless nor the Modem show up in the Network Connection pane?/panel? that I access in the menu bar (icon of two monitors). The only options there are eth1 and lo. (There are only 2 pci slots in this machine, so only two connections can appear along with "lo", but regardless of which cards are inserted, only eth1 and lo show up).

Hope you spy an inconsistency somewhere, Luke. Much appreciate the help!

---

### Post by lukew on 2007-01-18
You need to configure the desklette / panel object to use this new interface.

Luke

---

### Post by DeltaS on 2007-01-18
The Connections Properties pane only allows configuration of the selected connection. SInce wlan0 never appears there, I can't configure it there.

From other forum entries I've tried the following:

Does it matter that wlan0 and eth1 share the same Interrupt??

~$ sudo cat /proc/interrupts
           CPU0       
  0:     245949          XT-PIC  timer
  1:        733          XT-PIC  i8042
  2:          0          XT-PIC  cascade
  5:       5881          XT-PIC  ESS Maestro
  7:        186          XT-PIC  parport0
  8:          3          XT-PIC  rtc
  9:          1          XT-PIC  acpi
 11:       4391          XT-PIC  uhci_hcd:usb1, yenta, yenta, eth1, wlan0
 12:      20229          XT-PIC  i8042
 14:       6918          XT-PIC  ide0
 15:       7679          XT-PIC  ide1
NMI:          0 
LOC:          0 
ERR:          0
MIS:          0

Another post suggested running demsg. The giant output included these lines:

[17179616.132000] ndiswrapper version 1.34 loaded (preempt=no,smp=yes)
[17179616.216000] ndiswrapper: driver neti2220 (INPROCOMM,02/24/2005,3.07.02.2005) loaded
[17179616.216000] PCI: Enabling device 0000:02:00.0 (0000 -> 0003)
[17179616.216000] ACPI: PCI Interrupt 0000:02:00.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179616.220000] PCI: Setting latency timer of device 0000:02:00.0 to 64
[17179616.256000] ndiswrapper: using IRQ 11
[17179616.756000] wlan0: ethernet device 00:03:6d:20:de:a0 using NDIS driver: neti2220, version: 0x30007, NDIS version: 0x501, vendor: 'INPROCOMM IPN2220 Wireless LAN Adapter', 17FE:2220.5.conf
[17179616.756000] wlan0: encryption modes supported: WEP; TKIP with WPA, WPA2, WPA2PSK; AES/CCMP with WPA, WPA2, WPA2PSK

Lots of traffic about the wireless card and the driver I installed using ndiswrapper, but much of what's listed is Greek to me.

Much puzzlement continues. Hope this makes more sense to you!

---

### Post by DeltaS on 2007-01-18
I assume that if both wired and wireless cards are present, the fact that I'm connected with the wired one doesn't prevent the wireless one being listed as a network connection option?

---

### Post by Vox754 on 2007-02-13
Your card seems correctly installed, you may need to "turn it on".
Optionally turn off the wired connection.
```

sudo ifconfig eth1 down
sudo ifconfig wlan0 up

```

Look at this thread [http://ubuntuforums.org/showthread.php?t=324967](http://ubuntuforums.org/showthread.php?t=324967)

The GUI may not always work, so try to set up the network through the terminal. Greek is really not that hard.

[http://ubuntuforums.org/showthread.php?t=179270&highlight=inprocomm](http://ubuntuforums.org/showthread.php?t=179270&highlight=inprocomm)
[http://ubuntuforums.org/showthread.php?t=316249&highlight=inprocomm](http://ubuntuforums.org/showthread.php?t=316249&highlight=inprocomm)
[http://ubuntuforums.org/showthread.php?t=65680&highlight=inprocomm](http://ubuntuforums.org/showthread.php?t=65680&highlight=inprocomm)

---

