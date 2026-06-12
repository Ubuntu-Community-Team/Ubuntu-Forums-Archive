---
title: "Wireless trouble, Netgear WG121 (USB)"
date: 2006-11-06
forum: Networking &amp; Wireless
---

### Post by yawnster on 2006-11-06
Howdy guys,

Ive got a little trouble with the netgear USB card, when i use the network-admin included in Edgy, it lists the card fine, all the lights are on, I can put in the ESSID, but after activating the network it just wont connect..

So I try disabling the driver and using ndiswrapper..

Ive used 1.1 and 1.8 both to no avail, (as well as 1.20 and 1.28 compiled..)..

Every time it says that the driver and hardware were both present and working correctly, but then when actually connecting to the network it doesnt play ball.. (basically it cant find any networks.. however it does find a windows network when i go to Places>>Network Servers)

Anyway, the card is listed under the eth3 heading instead of wlan0, im guessing thats not a problem as all reading I have done thus far on the subject seems to state that this is not an issue.

Ive also downloaded wifi-radar and thats not detecting anything, despite the fact that im sitting right next to the router, having to now use an Ethernet cable to get access.. (computer normally resides upstairs, been moved to in order to be usable..)

Erm.. I suppose a few vitals then..

```
alex@alex-ubuntu-desk:~$ lsusb
Bus 003 Device 003: ID 0846:4210 NetGear, Inc. WG121 WiFi (v2)
Bus 003 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  
Bus 002 Device 001: ID 0000:0000  
alex@alex-ubuntu-desk:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

sit0      no wireless extensions.

eth3      IEEE 802.11b  ESSID:""  
          Mode:Auto  Channel=1  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

alex@alex-ubuntu-desk:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:11:2F:26:2C:DD  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe26:2cdd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:31291 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17030 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:45757455 (43.6 MiB)  TX bytes:1365872 (1.3 MiB)
          Interrupt:209 

eth3      Link encap:Ethernet  HWaddr 00:09:5B:D2:6D:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)
```

Erm, im not really sure what else to say.. if you need anything more from me just ask..

Thanks in advance..

Alex

---

### Post by yawnster on 2006-11-06
hmm i have managed to get the device to scan successfully now, it is now picking up the correct router that i am using, (verfied by the MAC address)..

```
alex@alex-ubuntu-desk:~$ sudo iwlist eth3 scan
eth3      Scan completed :
          Cell 01 - Address: 00:09:5B:C4:B2:E6
                    ESSID:"LATCHFORD"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:100  Signal level:0  Noise level:0
                    Extra: Last beacon: 60ms ago
```

however im not really too sure what to do next, the instructions from the ndiswrapper manual state that i shoudl now ahead and either run the commands..

**dhcliient eth3** or **iwconfig eth3 up**

However dhclient eth3 gives..

> alex@alex-ubuntu-desk:~$ sudo dhclient eth3
There is already a pid file /var/run/dhclient.pid with pid 5622
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth3/00:09:5b:d2:6d:72
Sending on   LPF/eth3/00:09:5b:d2:6d:72
Sending on   Socket/fallback
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 9
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 12
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

and iwconfig eth3 up just runs without any errors or feedback..

Any suggestions from here.. as im a little stumped..

Thanks in advance.. Alex

---

### Post by yawnster on 2006-11-07
Bump... Anyone got a clue?

---

### Post by FrodoB on 2006-11-07
No experience with this device, but maybe you could make a little command line script to set it up and maybe call it net.sh:

#!/bin/sh
/sbin/ifconfig eth3 up
/sbin/iwconfig eth3 mode "Managed"
/sbin/iwconfig eth3 key "XXXXXXXXXXXXXXXXXXXXXXXXXX"
/sbin/iwconfig eth3 essid "My ESSID"
/sbin/dhclient eth3

make it an executable script and set the correct WEP key and ESSID and then run it with:

$ sudo ./net.sh

---

### Post by yawnster on 2006-11-07
> **FrodoB said:**
> No experience with this device, but maybe you could make a little command line script to set it up and maybe call it net.sh:

#!/bin/sh
/sbin/ifconfig eth3 up
/sbin/iwconfig eth3 mode "Managed"
/sbin/iwconfig eth3 key "XXXXXXXXXXXXXXXXXXXXXXXXXX"
/sbin/iwconfig eth3 essid "My ESSID"
/sbin/dhclient eth3

make it an executable script and set the correct WEP key and ESSID and then run it with:

$ sudo ./net.sh

Hmmm, trying this didn't do much, when i set the essid and the mode to managed i can then scan for a network and it will find the one im looking for, and it will even show up in wifi-radar, but with no signal (look at the signal strength reading above.. its at 0..)

I put in this into the file..

```
#!/bin/sh
/sbin/ifconfig eth3 up
/sbin/iwconfig eth3 mode "Managed"
/sbin/iwconfig eth3 essid "LATCHFORD"
/sbin/dhclient eth3
```

and this was what was outputted..

```
alex@alex-ubuntu-desk:~$ sudo ./net.sh
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth3/00:09:5b:d2:6d:72
Sending on   LPF/eth3/00:09:5b:d2:6d:72
Sending on   Socket/fallback
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 14
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 13
DHCPDISCOVER on eth3 to 255.255.255.255 port 67 interval 9
No DHCPOFFERS received.
No working leases in persistent database - sleeping.#
```

I had this card working correctly on dapper, but under a compiled kernel, (2.6.16.19 I believe), cant remember what version of ndiswrapper I was using though.. At the moment im stumped at this, seeing as all the config is setup correctly it seems, the hardware and driver is setup and being detected, and its even finding the Access Point, but it doesnt find any signal strength, which is a little weird..

Anyone got any more ideas?

Thanks again.. Alex

---

### Post by FrodoB on 2006-11-07
Well, did the output of iwconfig eth3 at least change? I mean I hope it now has the ESSID, etc.

---

### Post by yawnster on 2006-11-07
oh yeah it changed, it changed when i set the mode to managed..

here is the output of **iwconfig** and **iwlist eth3 scan**

```
alex@alex-ubuntu-desk:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      no wireless extensions.

eth3      IEEE 802.11b  ESSID:"LATCHFORD"  
          Mode:Managed  Channel=11  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.
alex@alex-ubuntu-desk:~$ iwlist eth3 scan
eth3      Scan completed :
          Cell 01 - Address: 00:09:5B:C4:B2:E6
                    ESSID:"LATCHFORD"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:100  Signal level:0  Noise level:0
                    Extra: Last beacon: 80ms ago
```

Sorry for not making that clear.. Alex

---

### Post by yawnster on 2006-11-07
A screenshot of everything I think is going on...

[[IMG]http://img371.imageshack.us/img371/5933/networkde5.th.png[/IMG]](http://img371.imageshack.us/my.php?image=networkde5.png)

---

### Post by FrodoB on 2006-11-07
So you are not trying to use any WEP keys at the moment?

---

### Post by yawnster on 2006-11-07
> **FrodoB said:**
> So you are not trying to use any WEP keys at the moment?

nope, just plain wireless..

this card is a little old (got it in 2003) but it comes with a set of Linux drivers that I am using, when i got it to work before it was under the name wlan0, not eth3..

I remember that it was under eth3 for a while and then I did something and it was named under wlan0 and then it worked, but exactly what that command was has been last in the realms of time..

Thanks.. Alex

---

### Post by FrodoB on 2006-11-07
What channel is your access point supposed to be on.  Perhaps if you tell it with:

sudo iwconfig eth3 channel ?

and set the question mark to your access point channel?

---

### Post by yawnster on 2006-11-07
hmmm, i am supposed to be using channel 11..

After running that command 11 has now been set as the channel.. but it still is none the wiser to actually connecting to the connection..

the outputs are..

> alex@alex-ubuntu-desk:~$ iwconfig
lo        no wireless extensions.

eth1      no wireless extensions.

eth0      no wireless extensions.

eth3      IEEE 802.11b  ESSID:"LATCHFORD"  
          Mode:Managed  Channel=11  Access Point: Invalid   
          Sensitivity=0/200  
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

alex@alex-ubuntu-desk:~$ ifconfig
eth1      Link encap:Ethernet  HWaddr 00:11:2F:26:2C:DD  
          inet addr:192.168.0.5  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::211:2fff:fe26:2cdd/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8542 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4692 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12451298 (11.8 MiB)  TX bytes:367975 (359.3 KiB)
          Interrupt:209 

eth3      Link encap:Ethernet  HWaddr 00:09:5B:D2:6D:72  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:17 errors:0 dropped:0 overruns:0 frame:0
          TX packets:17 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2368 (2.3 KiB)  TX bytes:2368 (2.3 KiB)

alex@alex-ubuntu-desk:~$ iwlist eth3 scan
eth3      Scan completed :
          Cell 01 - Address: 00:09:5B:C4:B2:E6
                    ESSID:"LATCHFORD"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:11
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 9 Mb/s; 11 Mb/s
                              6 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality:100  Signal level:0  Noise level:0
                    Extra: Last beacon: 36ms ago

Thanks.. Alex

PS.. I think the problem is the Access Point Invalid.. in the first command.. If I run the command..

sudo iwconfig eth3 essid "LATCHFORD" mode Managed

then it will set the access point to the MAC address of my router, but then about 5 seconds later I try running the iwconfig command (this is doing it repeated for the 5 seconds..) it will go back to invalid..

A little strange..

---

### Post by FrodoB on 2006-11-07
Can you post the part of the dmesg output where the WG121 v2 is loaded? This may help us see if the device started correctly.

---

### Post by Jose Catre-Vandis on 2006-11-07
FWIW here is my experience with a Netgear WG111v2 USB Wireless adapter, used for connecting to a DHCP wireless mesh controlled by MAC address (just like a home wireless router really)

I have a lightweight Edgy install going on using the ALT CD to do a command line install, followed up by the XFCE4 desktop, so its Edgy underneath.

Stick to the CLI and stay away from the GUI networking dialogs

!! Adapter unplugged from PC

```
sudo install ndiswrapper-utils
```
```
sudo ndiswrapper -i /path to driver.inf
```
(in my case net111v2.inf, in the WINXP folder of the CD)


```
ndiswrapper -l
```
should show driver installed

```
ndiswrapper -m
```
ensures ndiswrapper starts up on boot and sets alias

```
sudo nano /etc/networking/interfaces
```
add the following:
```
#the wireless interface
auto wlano
iface wlan0 inet dhcp
wireless-essid mynetwork
wireless-mode managed
```
save file and exit

```
sudo modprobe ndiswrapper
```
loads ndiswrapper (you won't need to do this on reboot/cold start)

```
sudo /etc/init.d/networking restart
```
reloads the network settings

!!Now plug in the adapter and with any luck the blue light will come on

```
iwconfig
```
and you should see your connection details

NB: you may need to blacklist rtl8187/r8187 islsm islsm_usb (I didn't have to due to the minimal install)

NB: I find things work just fine, as long as I unplug the adapter after use and ensure it is only plugged back in after a reboot to desktop, doesn't work "automagically" if left plugged in for a cold start or reboot. Any answers to this bit would be welcome!

---

### Post by yawnster on 2006-11-08
> alex@alex-ubuntu-desk:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000f0000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000004fff0000 (usable)
[17179569.184000]  BIOS-e820: 000000004fff0000 - 000000004fff3000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000004fff3000 - 0000000050000000 (ACPI data)
[17179569.184000]  BIOS-e820: 00000000fec00000 - 00000000fec01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fee00000 - 00000000fee01000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffff0000 - 0000000100000000 (reserved)
[17179569.184000] 383MB HIGHMEM available.
[17179569.184000] 896MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 327664
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 225280 pages, LIFO batch:31
[17179569.184000]   HighMem zone: 98288 pages, LIFO batch:31
[17179569.184000] DMI 2.2 present.
[17179569.184000] ACPI: RSDP (v000 Nvidia                                ) @ 0x000f75e0
[17179569.184000] ACPI: RSDT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x4fff3000
[17179569.184000] ACPI: FADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x4fff3040
[17179569.184000] ACPI: MADT (v001 Nvidia AWRDACPI 0x42302e31 AWRD 0x00000000) @ 0x4fff7640
[17179569.184000] ACPI: DSDT (v001 NVIDIA AWRDACPI 0x00001000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x4008
[17179569.184000] ACPI: Local APIC address 0xfee00000
[17179569.184000] ACPI: LAPIC (acpi_id[0x00] lapic_id[0x00] enabled)
[17179569.184000] Processor #0 6:10 APIC version 16
[17179569.184000] ACPI: LAPIC_NMI (acpi_id[0x00] high edge lint[0x1])
[17179569.184000] ACPI: IOAPIC (id[0x02] address[0xfec00000] gsi_base[0])
[17179569.184000] IOAPIC[0]: apic_id 2, version 17, address 0xfec00000, GSI 0-23
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 0 global_irq 2 dfl dfl)
[17179569.184000] ACPI: BIOS IRQ0 pin2 override ignored.
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 9 global_irq 9 high level)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 14 global_irq 14 high edge)
[17179569.184000] ACPI: INT_SRC_OVR (bus 0 bus_irq 15 global_irq 15 high edge)
[17179569.184000] ACPI: IRQ9 used by override.
[17179569.184000] ACPI: IRQ14 used by override.
[17179569.184000] ACPI: IRQ15 used by override.
[17179569.184000] Enabling APIC mode:  Flat.  Using 1 I/O APICs
[17179569.184000] Using ACPI (MADT) for SMP configuration information
[17179569.184000] Allocating PCI resources starting at 60000000 (gap: 50000000:aec00000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] mapped APIC to ffffd000 (fee00000)
[17179569.184000] mapped IOAPIC to ffffc000 (fec00000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 4096 (order: 12, 16384 bytes)
[17179569.184000] Detected 2079.854 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.332000] Dentry cache hash table entries: 131072 (order: 7, 524288 bytes)
[17179572.332000] Inode-cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.368000] Memory: 1289076k/1310656k available (1910k kernel code, 20384k reserved, 1070k data, 308k init, 393152k highmem)
[17179572.368000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.448000] Calibrating delay using timer specific routine.. 4163.92 BogoMIPS (lpj=8327844)
[17179572.448000] Security Framework v1.0.0 initialized
[17179572.448000] SELinux:  Disabled at boot.
[17179572.448000] Mount-cache hash table entries: 512
[17179572.448000] CPU: After generic identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179572.448000] CPU: After vendor identify, caps: 0383fbff c1c3fbff 00000000 00000000 00000000 00000000 00000000
[17179572.448000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.448000] CPU: L2 Cache: 512K (64 bytes/line)
[17179572.448000] CPU: After all inits, caps: 0383fbff c1c3fbff 00000000 00000420 00000000 00000000 00000000
[17179572.448000] Checking 'hlt' instruction... OK.
[17179572.464000] SMP alternatives: switching to UP code
[17179572.464000] Freeing SMP alternatives: 16k freed
[17179572.464000] checking if image is initramfs... it is
[17179572.912000] Freeing initrd memory: 5563k freed
[17179572.912000] ACPI: Core revision 20060707
[17179572.920000] ACPI: Looking for DSDT ... not found!
[17179572.920000] CPU0: AMD Athlon(tm) XP 2800+ stepping 00
[17179572.920000] Total of 1 processors activated (4163.92 BogoMIPS).
[17179572.920000] ENABLING IO-APIC IRQs
[17179572.920000] ..TIMER: vector=0x31 apic1=0 pin1=0 apic2=-1 pin2=-1
[17179573.064000] Brought up 1 CPUs
[17179573.064000] migration_cost=0
[17179573.064000] NET: Registered protocol family 16
[17179573.064000] EISA bus registered
[17179573.064000] ACPI: bus type pci registered
[17179573.080000] PCI: PCI BIOS revision 2.10 entry at 0xfb410, last bus=3
[17179573.080000] PCI: Using configuration type 1
[17179573.080000] Setting up standard PCI resources
[17179573.092000] ACPI: Interpreter enabled
[17179573.092000] ACPI: Using IOAPIC for interrupt routing
[17179573.092000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.092000] PCI: Probing PCI hardware (bus 00)
[17179573.096000] PCI: nForce2 C1 Halt Disconnect fixup
[17179573.096000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:09.0
[17179573.096000] Boot video device is 0000:03:00.0
[17179573.096000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.164000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.HUB0._PRT]
[17179573.164000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.AGPB._PRT]
[17179573.164000] ACPI: PCI Interrupt Link [LNK1] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.164000] ACPI: PCI Interrupt Link [LNK2] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179573.164000] ACPI: PCI Interrupt Link [LNK3] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.164000] ACPI: PCI Interrupt Link [LNK4] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.164000] ACPI: PCI Interrupt Link [LNK5] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.164000] ACPI: PCI Interrupt Link [LUBA] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.168000] ACPI: PCI Interrupt Link [LUBB] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179573.168000] ACPI: PCI Interrupt Link [LMAC] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179573.168000] ACPI: PCI Interrupt Link [LAPU] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179573.168000] ACPI: PCI Interrupt Link [LACI] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179573.168000] ACPI: PCI Interrupt Link [LMCI] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.168000] ACPI: PCI Interrupt Link [LSMB] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179573.168000] ACPI: PCI Interrupt Link [LUB2] (IRQs 3 4 *5 6 7 9 10 11 12 14 15)
[17179573.168000] ACPI: PCI Interrupt Link [LFIR] (IRQs 3 4 5 6 7 *9 10 11 12 14 15)
[17179573.168000] ACPI: PCI Interrupt Link [L3CM] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.168000] ACPI: PCI Interrupt Link [LIDE] (IRQs 3 4 5 6 7 9 10 11 12 14 15) *0, disabled.
[17179573.168000] ACPI: PCI Interrupt Link [APC1] (IRQs *16), disabled.
[17179573.168000] ACPI: PCI Interrupt Link [APC2] (IRQs *17), disabled.
[17179573.168000] ACPI: PCI Interrupt Link [APC3] (IRQs *18), disabled.
[17179573.168000] ACPI: PCI Interrupt Link [APC4] (IRQs *19), disabled.
[17179573.172000] ACPI: PCI Interrupt Link [APC5] (IRQs *16), disabled.
[17179573.172000] ACPI: PCI Interrupt Link [APCF] (IRQs 20 21 22) *0, disabled.
[17179573.172000] ACPI: PCI Interrupt Link [APCG] (IRQs 20 21 22) *0, disabled.
[17179573.172000] ACPI: PCI Interrupt Link [APCH] (IRQs 20 21 22) *0, disabled.
[17179573.172000] ACPI: PCI Interrupt Link [APCI] (IRQs 20 21 22) *0, disabled.
[17179573.172000] ACPI: PCI Interrupt Link [APCJ] (IRQs 20 21 22) *0, disabled.
[17179573.172000] ACPI: PCI Interrupt Link [APCK] (IRQs 20 21 22) *0, disabled.
[17179573.172000] ACPI: PCI Interrupt Link [APCS] (IRQs *23), disabled.
[17179573.172000] ACPI: PCI Interrupt Link [APCL] (IRQs 20 21 22) *0, disabled.
[17179573.172000] ACPI: PCI Interrupt Link [APCM] (IRQs 20 21 22) *0, disabled.
[17179573.172000] ACPI: PCI Interrupt Link [AP3C] (IRQs 20 21 22) *0, disabled.
[17179573.172000] ACPI: PCI Interrupt Link [APCZ] (IRQs 20 21 22) *0, disabled.
[17179573.176000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.176000] pnp: PnP ACPI init
[17179573.184000] pnp: PnP ACPI: found 17 devices
[17179573.184000] PnPBIOS: Disabled by ACPI PNP
[17179573.184000] PCI: Using ACPI for IRQ routing
[17179573.184000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.236000] pnp: 00:00: ioport range 0x4000-0x407f could not be reserved
[17179573.236000] pnp: 00:00: ioport range 0x4080-0x40ff has been reserved
[17179573.236000] pnp: 00:00: ioport range 0x4400-0x447f has been reserved
[17179573.236000] pnp: 00:00: ioport range 0x4480-0x44ff could not be reserved
[17179573.236000] pnp: 00:00: ioport range 0x4200-0x427f has been reserved
[17179573.236000] pnp: 00:00: ioport range 0x4280-0x42ff has been reserved
[17179573.236000] pnp: 00:01: ioport range 0x5000-0x503f has been reserved
[17179573.236000] pnp: 00:01: ioport range 0x5500-0x553f has been reserved
[17179573.236000] PCI: Bridge: 0000:00:08.0
[17179573.236000]   IO window: a000-bfff
[17179573.236000]   MEM window: df000000-e0ffffff
[17179573.236000]   PREFETCH window: 60000000-600fffff
[17179573.236000] PCI: Bridge: 0000:00:1e.0
[17179573.236000]   IO window: disabled.
[17179573.236000]   MEM window: dd000000-deffffff
[17179573.236000]   PREFETCH window: d0000000-d7ffffff
[17179573.236000] PCI: Setting latency timer of device 0000:00:08.0 to 64
[17179573.236000] NET: Registered protocol family 2
[17179573.276000] IP route cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.276000] TCP established hash table entries: 262144 (order: 9, 2097152 bytes)
[17179573.276000] TCP bind hash table entries: 65536 (order: 7, 524288 bytes)
[17179573.276000] TCP: Hash tables configured (established 262144 bind 65536)
[17179573.276000] TCP reno registered
[17179573.280000] audit: initializing netlink socket (disabled)
[17179573.280000] audit(1163003874.280:1): initialized
[17179573.280000] highmem bounce pool size: 64 pages
[17179573.280000] VFS: Disk quotas dquot_6.5.1
[17179573.280000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.280000] Initializing Cryptographic API
[17179573.280000] io scheduler noop registered
[17179573.280000] io scheduler anticipatory registered
[17179573.280000] io scheduler deadline registered
[17179573.280000] io scheduler cfq registered (default)
[17179573.280000] isapnp: Scanning for PnP cards...
[17179573.636000] isapnp: No Plug & Play device found
[17179573.656000] Real Time Clock Driver v1.12ac
[17179573.656000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179573.660000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.660000] serial8250: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.660000] 00:0a: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179573.660000] 00:0b: ttyS1 at I/O 0x2f8 (irq = 3) is a 16550A
[17179573.660000] mice: PS/2 mouse device common for all mice
[17179573.660000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179573.660000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179573.660000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179573.660000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179573.664000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179573.664000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179573.664000] EISA: Probing bus 0 at eisa.0
[17179573.664000] Cannot allocate resource for EISA slot 4
[17179573.664000] Cannot allocate resource for EISA slot 5
[17179573.664000] EISA: Detected 0 cards.
[17179573.664000] TCP bic registered
[17179573.664000] NET: Registered protocol family 1
[17179573.664000] NET: Registered protocol family 8
[17179573.664000] NET: Registered protocol family 20
[17179573.664000] Using IPI No-Shortcut mode
[17179573.664000] ACPI: (supports S0 S1 S4 S5)
[17179573.664000] Freeing unused kernel memory: 308k freed
[17179573.692000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179574.788000] Capability LSM initialized
[17179575.108000] SCSI subsystem initialized
[17179575.108000] libata version 1.20 loaded.
[17179575.112000] NFORCE2: IDE controller at PCI slot 0000:00:09.0
[17179575.112000] NFORCE2: chipset revision 162
[17179575.112000] NFORCE2: not 100% native mode: will probe irqs later
[17179575.112000] NFORCE2: BIOS didn't set cable bits correctly. Enabling workaround.
[17179575.112000] NFORCE2: 0000:00:09.0 (rev a2) UDMA133 controller
[17179575.112000]     ide0: BM-DMA at 0xf000-0xf007, BIOS settings: hda:DMA, hdb:DMA
[17179575.112000]     ide1: BM-DMA at 0xf008-0xf00f, BIOS settings: hdc:DMA, hdd:DMA
[17179575.112000] Probing IDE interface ide0...
[17179575.400000] hda: HDS722580VLAT20, ATA DISK drive
[17179575.680000] hdb: Maxtor 6E030L0, ATA DISK drive
^[[A[17179575.736000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179575.752000] Probing IDE interface ide1...
[17179576.492000] hdc: PIONEER DVD-RW DVR-108, ATAPI CD/DVD-ROM drive
[17179577.276000] hdd: SONY CD-RW CRX140E, ATAPI CD/DVD-ROM drive
[17179577.332000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.344000] hda: max request size: 512KiB
[17179577.360000] hda: 160836480 sectors (82348 MB) w/1794KiB Cache, CHS=16383/255/63, UDMA(100)
[17179577.360000] hda: cache flushes supported
[17179577.360000]  hda: hda1 hda2 < hda5 >
[17179577.388000] hdb: max request size: 128KiB
[17179577.388000] hdb: 60058656 sectors (30750 MB) w/2048KiB Cache, CHS=59582/16/63, UDMA(133)
[17179577.388000] hdb: cache flushes supported
[17179577.388000]  hdb: hdb1
[17179577.412000] hdc: ATAPI 63X DVD-ROM DVD-R CD-R/RW drive, 2000kB Cache, UDMA(33)
[17179577.412000] Uniform CD-ROM driver Revision: 3.20
[17179577.444000] hdd: ATAPI 32X CD-ROM CD-R/RW drive, 4096kB Cache, UDMA(33)
[17179577.736000] sata_sil 0000:01:0b.0: version 0.9
[17179577.736000] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[17179577.736000] ACPI: PCI Interrupt 0000:01:0b.0[A] -> Link [APC3] -> GSI 18 (level, high) -> IRQ 177
[17179577.736000] ata1: SATA max UDMA/100 cmd 0xF887C080 ctl 0xF887C08A bmdma 0xF887C000 irq 177
[17179577.736000] ata2: SATA max UDMA/100 cmd 0xF887C0C0 ctl 0xF887C0CA bmdma 0xF887C008 irq 177
[17179577.940000] ata1: SATA link down (SStatus 0)
[17179577.948000] scsi0 : sata_sil
[17179578.152000] ata2: SATA link down (SStatus 0)
[17179578.160000] scsi1 : sata_sil
[17179578.224000] usbcore: registered new driver usbfs
[17179578.224000] usbcore: registered new driver hub
[17179578.228000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.228000] ACPI: PCI Interrupt Link [APCF] enabled at IRQ 22
[17179578.228000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [APCF] -> GSI 22 (level, high) -> IRQ 185
[17179578.228000] PCI: Setting latency timer of device 0000:00:02.0 to 64
[17179578.228000] ohci_hcd 0000:00:02.0: OHCI Host Controller
[17179578.228000] ohci_hcd 0000:00:02.0: new USB bus registered, assigned bus number 1
[17179578.264000] ieee1394: Initialized config rom entry `ip1394'
[17179578.280000] ohci_hcd 0000:00:02.0: irq 185, io mem 0xe1087000
[17179578.336000] usb usb1: configuration #1 chosen from 1 choice
[17179578.336000] hub 1-0:1.0: USB hub found
[17179578.336000] hub 1-0:1.0: 3 ports detected
[17179578.440000] ACPI: PCI Interrupt Link [APCG] enabled at IRQ 21
[17179578.440000] ACPI: PCI Interrupt 0000:00:02.1[B] -> Link [APCG] -> GSI 21 (level, high) -> IRQ 193
[17179578.440000] PCI: Setting latency timer of device 0000:00:02.1 to 64
[17179578.440000] ohci_hcd 0000:00:02.1: OHCI Host Controller
[17179578.440000] ohci_hcd 0000:00:02.1: new USB bus registered, assigned bus number 2
[17179578.468000] ohci_hcd 0000:00:02.1: irq 193, io mem 0xe1082000
[17179578.524000] usb usb2: configuration #1 chosen from 1 choice
[17179578.524000] hub 2-0:1.0: USB hub found
[17179578.524000] hub 2-0:1.0: 3 ports detected
[17179578.636000] ACPI: PCI Interrupt Link [APCL] enabled at IRQ 20
[17179578.636000] ACPI: PCI Interrupt 0000:00:02.2[C] -> Link [APCL] -> GSI 20 (level, high) -> IRQ 201
[17179578.636000] PCI: Setting latency timer of device 0000:00:02.2 to 64
[17179578.636000] ehci_hcd 0000:00:02.2: EHCI Host Controller
[17179578.636000] ehci_hcd 0000:00:02.2: new USB bus registered, assigned bus number 3
[17179578.636000] ehci_hcd 0000:00:02.2: debug port 1
[17179578.636000] PCI: cache line size of 64 is not supported by device 0000:00:02.2
[17179578.636000] ehci_hcd 0000:00:02.2: irq 201, io mem 0xe1083000
[17179578.636000] ehci_hcd 0000:00:02.2: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.636000] usb usb3: configuration #1 chosen from 1 choice
[17179578.636000] hub 3-0:1.0: USB hub found
[17179578.636000] hub 3-0:1.0: 6 ports detected
[17179578.740000] ACPI: PCI Interrupt Link [APCM] enabled at IRQ 22
[17179578.740000] ACPI: PCI Interrupt 0000:00:0d.0[A] -> Link [APCM] -> GSI 22 (level, high) -> IRQ 185
[17179578.740000] PCI: Setting latency timer of device 0000:00:0d.0 to 64
[17179578.800000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[185]  MMIO=[e1084000-e10847ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179578.872000] Attempting manual resume
[17179578.892000] kjournald starting.  Commit interval 5 seconds
[17179578.892000] EXT3-fs: mounted filesystem with ordered data mode.
[17179579.912000] ohci1394: fw-host0: SelfID received outside of bus reset sequence
[17179580.184000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00e018000081c9e5]
[17179587.104000] Linux agpgart interface v0.101 (c) Dave Jones
[17179587.104000] agpgart: Detected NVIDIA nForce2 chipset
[17179587.108000] agpgart: AGP aperture is 64M @ 0xd8000000
[17179587.120000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179587.120000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179587.420000] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x5000
[17179587.420000] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x5500
[17179587.560000] input: PC Speaker as /class/input/input1
[17179587.920000] forcedeth.c: Reverse Engineered nForce ethernet driver. Version 0.54.
[17179587.920000] ACPI: PCI Interrupt Link [APCH] enabled at IRQ 21
[17179587.920000] ACPI: PCI Interrupt 0000:00:04.0[A] -> Link [APCH] -> GSI 21 (level, high) -> IRQ 193
[17179587.920000] PCI: Setting latency timer of device 0000:00:04.0 to 64
[17179587.928000] input: PS/2 Generic Mouse as /class/input/input2
[17179588.280000] parport: PnPBIOS parport detected.
[17179588.280000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179588.328000] FDC 0 is a post-1991 82077
[17179588.420000] ts: Compaq touchscreen protocol output
[17179588.440000] eth0: forcedeth.c: subsystem: 01043:80a7 bound to 0000:00:04.0
[17179588.440000] ACPI: PCI Interrupt Link [APCJ] enabled at IRQ 20
[17179588.440000] ACPI: PCI Interrupt 0000:00:06.0[A] -> Link [APCJ] -> GSI 20 (level, high) -> IRQ 201
[17179588.440000] PCI: Setting latency timer of device 0000:00:06.0 to 64
[17179588.760000] intel8x0_measure_ac97_clock: measured 52810 usecs
[17179588.760000] intel8x0: clocking to 48000
[17179588.760000] ACPI: PCI Interrupt Link [APC2] enabled at IRQ 17
[17179588.760000] ACPI: PCI Interrupt 0000:01:04.0[A] -> Link [APC2] -> GSI 17 (level, high) -> IRQ 209
[17179588.760000] skge 1.5 addr 0xe0000000 irq 209 chip Yukon-Lite rev 7
[17179588.760000] skge eth1: addr 00:11:2f:26:2c:dd
[17179589.020000] lp0: using parport0 (interrupt-driven).
[17179589.040000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179589.040000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179589.068000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
[17179589.108000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179589.124000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179589.188000] fuse init (API version 7.6)
[17179589.216000] Adding 3285252k swap on /dev/disk/by-uuid/6b25d4cf-fbe3-49a6-aac8-74b2d69e8333.  Priority:-1 extents:1 across:3285252k
[17179589.276000] EXT3 FS on hda1, internal journal
[17179590.972000] NET: Registered protocol family 17
[17179592.132000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
[17179592.148000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179592.164000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179592.192000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
[17179592.208000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179592.224000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179592.240000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
[17179592.256000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179592.272000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179592.288000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
[17179592.304000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179592.324000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179595.384000] ACPI: Power Button (FF) [PWRF]
[17179595.384000] ACPI: Power Button (CM) [PWRB]
[17179595.496000] ibm_acpi: ec object not found
[17179595.524000] pcc_acpi: loading...
[17179598.200000] apm: BIOS version 1.2 Flags 0x07 (Driver version 1.16ac)
[17179598.200000] apm: overridden by ACPI.
[17179603.976000] NET: Registered protocol family 10
[17179603.976000] lo: Disabled Privacy Extensions
[17179603.976000] IPv6 over IPv4 tunneling driver
[17179604.580000] Bluetooth: Core ver 2.8
[17179604.580000] NET: Registered protocol family 31
[17179604.580000] Bluetooth: HCI device and connection manager initialized
[17179604.580000] Bluetooth: HCI socket layer initialized
[17179604.624000] Bluetooth: L2CAP ver 2.8
[17179604.624000] Bluetooth: L2CAP socket layer initialized
[17179604.652000] Bluetooth: RFCOMM socket layer initialized
[17179604.652000] Bluetooth: RFCOMM TTY layer initialized
[17179604.652000] Bluetooth: RFCOMM ver 1.7
[17179612.780000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17179612.924000] ISOFS: changing to secondary root
[17179695.804000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
[17179695.820000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179695.836000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179705.968000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
[17179705.984000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179706.000000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179744.320000] usb 3-2: new high speed USB device using ehci_hcd and address 2
[17179744.452000] usb 3-2: configuration #1 chosen from 1 choice
[17179744.568000] ieee80211_crypt: registered algorithm 'NULL'
[17179744.572000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179744.572000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179744.620000] islusb: suitable configuration found for net2280 + PCI device
[17179745.060000] usbcore: registered new driver islusb
[17179746.656000] scheduling int bh
[17179746.660000] scheduling int bh
[17179747.400000] ADDRCONF(NETDEV_UP): eth3: link is not ready
[17179821.016000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
[17179821.032000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179821.048000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179821.092000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
[17179821.108000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179821.124000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179821.144000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
[17179821.160000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179821.180000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179821.204000] ndiswrapper version 1.8 loaded (preempt=no,smp=yes)
[17179821.220000] ndiswrapper (wrapper_init:173): loadndiswrapper failed (32512); check system log for messages from 'loadndisdriver'
[17179821.252000] ndiswrapper (wrapper_init:180): ndiswrapper: initialization failed
[17179822.340000] ADDRCONF(NETDEV_UP): eth3: link is not ready
[17179952.256000] usb 3-2: USB disconnect, address 2
[17179964.604000] skge eth1: enabling interface
[17179964.608000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179966.600000] skge eth1: Link is up at 100 Mbps, full duplex, flow control none
[17179966.604000] ADDRCONF(NETDEV_CHANGE): eth1: link becomes ready
[17179976.700000] eth1: no IPv6 routers present

Hmm.. thats the entire output of dmesg, it states that the initalization has failed.. ive installed ndiswrapper about 20 times now, got so many bleeding variants on now that im not sure of what ive actually got on there now lol.. (Just followed Jose's tutorial then, so im guessing I have ndiwrapper-utils 1.1)

Any clues now?

Thanks alot guys.. Alex

PS.. Jose, thanks for the effort, but following your tutorial drew a blank,  i think the problem lies in the fact that the interface is listed under eth3 and not wlan0, does anyone know how to switch it? because from what I can remember when i got this working on Dapper it was under a 2.6.16.19 kernel under the wlan0 interface, after struggling with eth3 on 2.6.15.x for about 2 weeks previously..

However having already tried a 2.6.18.2 kernel, and it not even finding my card whatsoever, it was not looking too good.. :(

---

### Post by Jose Catre-Vandis on 2006-11-08
Try removing the eth3 from interfaces and inserting wlan0 ?

I tell Ubuntu to use wlan0 rather than Ubuntu telling me! <- Which suggests ubuntu is loadiung a driver that won't work for you, so....

Blacklist preloaded linux drivers

```
sudo gedit /etc/modprobe.d/blacklist
```
Add to file: for example (check lsmod for what is loaded)

blacklist bcm43xx
blacklist rtl8187
blacklist islsm
blacklist islsm_usb

---

### Post by yawnster on 2006-11-08
hmmm.. well blacklisting the drivers didnt do much really, apart from not allowing the card to even turn on lol.. So i have re-enabled the drivers to get the card to function at all..

Also trying to manually rename the eth3 to wlan0 was not as much of a success as i hoped.. it just didnt show up in the network-admin and it also didnt allow for scanning of networks etc.. so I have changed that back too..

Thanks.. Alex

---

### Post by FrodoB on 2006-11-08
Definitely an issue in the loading there.  Does the device require a firmware, and perhaps that is missing? 

On another forum someone said that it was necessary to set their WG121 in Ad-Hoc mode first and then to put it into Managed mode for it to work.

---

### Post by Jose Catre-Vandis on 2006-11-08
> **yawnster said:**
> hmmm.. well blacklisting the drivers didnt do much really, apart from not allowing the card to even turn on lol.. So i have re-enabled the drivers to get the card to function at all..

Also trying to manually rename the eth3 to wlan0 was not as much of a success as i hoped.. it just didnt show up in the network-admin and it also didnt allow for scanning of networks etc.. so I have changed that back too..

Thanks.. Alex

Sounds like you are still using gui tools to get this working, my success was working purely in terminal.

Suggest you uninstall everything ndiswrapper and start again with the synaptic or aptitude/apt-get default for ndiswrapper-utils

Oh, just found this:

[http://lists.linux-wlan.com/pipermail/linux-wlan-user/2005-December/013564.html](http://lists.linux-wlan.com/pipermail/linux-wlan-user/2005-December/013564.html)

which suggests your adapter uses a prism chipset and therefore needs linux-wlan to run?

---

### Post by FrodoB on 2006-11-08
I believe that wlan is for the prism2 - prism3.  The prism54 project is for 802.11g devices.

---

### Post by Jose Catre-Vandis on 2006-11-08
I have just tried my adapter in a clean full install of Edgy, and no go, refuses to fully connect. I can get to the mesh but not through to the net. this is symptomatic of another driver taking over, and I get the same ndiswrapper loading errors as you :-(

---

### Post by yawnster on 2006-11-09
hmm.. well i knwo that it uses a Prism GT chipset, and that the Prism54 says it supports my device, but im unsure of exactly what to do with .arm files..

[http://prism54.org/newdrivers.html](http://prism54.org/newdrivers.html)

As its USB 2.0 I need the 2.5.8.0 version.. But exactly what I need to do 
with it is beyond me.. Any Ideas? (never used .arm files..)

The device is running on 802.11b at the moment, but I believe I can also run on 802.11g too..

Hmmm.. Thanks for all the effort guys.. getting a little fustrating now lol.. Alex

EDIT: Didnt see Page 3.. Hmm.. seems like a common problem then.. lsmod gives..

> alex@alex-ubuntu-desk:~$ lsmod
Module                  Size  Used by
nls_cp437               6912  1 
isofs                  38076  1 
udf                    89348  0 
binfmt_misc            13448  1 
rfcomm                 42260  0 
l2cap                  27136  5 rfcomm
bluetooth              53476  4 rfcomm,l2cap
ipv6                  272288  17 
cpufreq_userspace       5408  0 
cpufreq_stats           7744  0 
freq_table              6048  1 cpufreq_stats
cpufreq_powersave       2944  0 
cpufreq_ondemand        8876  0 
cpufreq_conservative     8712  0 
video                  17540  0 
tc1100_wmi              8324  0 
sony_acpi               6412  0 
sbs                    16804  0 
pcc_acpi               14080  0 
i2c_ec                  6272  1 sbs
hotkey                 11556  0 
dev_acpi               12292  0 
container               5632  0 
button                  7952  0 
battery                11652  0 
asus_acpi              17688  0 
ac                      6788  0 
af_packet              24584  4 
fuse                   43912  2 
sbp2                   24584  0 
lp                     12964  0 
tsdev                   9152  0 
islsm_usb              33028  0 
islsm_device           13576  1 islsm_usb
islsm                  37004  2 islsm_usb,islsm_device
ieee80211softmac       33792  1 islsm
ieee80211              35272  2 islsm,ieee80211softmac
ieee80211_crypt         7552  1 ieee80211
skge                   40336  0 
snd_mpu401              9640  0 
snd_mpu401_uart        10240  1 snd_mpu401
analog                 12960  0 
gameport               17160  1 analog
crc_ccitt               3200  1 islsm
parport_pc             37796  1 
parport                39496  2 lp,parport_pc
snd_rawmidi            27264  1 snd_mpu401_uart
snd_seq_device          9868  1 snd_rawmidi
pcspkr                  4352  0 
psmouse                41352  0 
serio_raw               8452  0 
evdev                  11392  1 
snd_intel8x0           34844  1 
snd_ac97_codec         97696  1 snd_intel8x0
snd_ac97_bus            3456  1 snd_ac97_codec
snd_pcm_oss            47360  0 
snd_mixer_oss          19584  1 snd_pcm_oss
snd_pcm                84612  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              25348  1 snd_pcm
i2c_nforce2             8192  0 
i2c_core               23424  2 i2c_ec,i2c_nforce2
nvidia_agp              9628  1 
agpgart                34888  1 nvidia_agp
shpchp                 42144  0 
pci_hotplug            32828  1 shpchp
forcedeth              32268  0 
floppy                 63044  0 
snd                    58372  12 snd_mpu401,snd_mpu401_uart,snd_rawmidi,snd_seq_device,snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              11232  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm
ext3                  142728  1 
jbd                    62228  1 ext3
ohci1394               37040  0 
ieee1394              306104  2 sbp2,ohci1394
ehci_hcd               34696  0 
ohci_hcd               22532  0 
usbcore               134912  4 islsm_usb,ehci_hcd,ohci_hcd
ide_generic             2432  0 
sata_sil               11016  0 
ide_cd                 33696  1 
cdrom                  38944  1 ide_cd
ide_disk               18560  5 
generic                 5764  0 
amd74xx                15260  0 [permanent]
sata_nv                11268  0 
libata                 74892  2 sata_sil,sata_nv
scsi_mod              144648  2 sbp2,libata
thermal                15624  0 
processor              31560  1 thermal
fan                     6020  0 
fbcon                  41504  0 
tileblit                3840  1 fbcon
font                    9344  1 fbcon
bitblit                 7168  1 fbcon
softcursor              3328  1 bitblit
vesafb                  9244  0 
capability              5896  0 
commoncap               8704  1 capability

for me.. if that helps..

---

### Post by FrodoB on 2006-11-09
Apparently the .arm files go into:

/lib/firmware/2.6.17-10-generic

If that does not work then I would move them to:

/lib/firmware

Then you should see it load in dmesg.

---

### Post by FrodoB on 2006-11-09
One would think, that with a prism54 device, that you would not need ndiswrapper at all.

I have a PC Card device and I did not have to load the arm files, evidently the ones that came with Ubuntu worked.

When it loads it shows the following in dmesg:

[17188856.224000] pccard: CardBus card inserted into slot 0
[17188856.328000] Loaded prism54 driver, version 1.2
[17188856.328000] PCI: Enabling device 0000:03:00.0 (0000 -> 0002)
[17188856.328000] ACPI: PCI Interrupt 0000:03:00.0[A] -> GSI 18 (level, low) -> IRQ 169
[17188856.332000] eth1: uploading firmware...
[17188856.448000] eth1: firmware version: 1.0.4.3
[17188856.448000] eth1: firmware upload complete

This is a so called full mac device and not soft mac card.

---

### Post by yawnster on 2006-11-10
hmmm well dropped the .arm file into the /lib/firmare folder didnt gave any output to dmesg, neither did putting it in /lib/firmware/2.6.17-generic so im a little stumped..

I noticed that despite having the correct ESSID on the /etc/network/interfaces file, and it shows up in the Network-Admin as that, when I run iwconfig after a restart the essid is back to nothing.. it doesnt take the essid from the file like it should..

There is one more thing I would like to try, i am going to revert to a 2.6.16 kernel, (if i can get one to compile, any ideas guys?) as thats the way i got it to work last time.. 

If that fails, Im not really too sure of what to do next, I was wondering if anyone could perhaps recommend a different card, as this one seems to be gradually running out of options...

Thanks Frodo..

PS.. I tested the card on my windows machine to make sure that the cards not actually faulty and surprisingly enough it works fine there.. So its definately not a hardware problem..

---

### Post by FrodoB on 2006-11-10
I have several working USB wireless devices, but each of them requires compiling and installing the drivers.

Belkin F5D7050 ver 3000

Belkin F5D7050 ver 4000

Zonet ZEW2500P

Airlink101 AWLL3026

The Airlink101 AWLL3036 and the Belkin F5D7050 ver 4000 both use the Zydas zd1211b chipset. The are recognized in Edgy by the zd1211rw driver, but it is broken, so you have to get a driver that works from [http://zd1211.ath.cx/](http://zd1211.ath.cx/) and modify the makefile for the zd1211b version of the zd1211 family. The Belkin is the better constructed of the two, I think.

The Belkin F5D7050 ver 3000 requires the rt73 driver from Ralink's web site and you have to modify the rtmp_def.h file and add the device's USB ID to it.

The Zonet ZEW2500P is recognized by Edgy, but somewhat fussy and problematic.

[http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads)

So I don't have any easy suggestions, all require downloading software and building drivers.

If you are interested I would suggest building the drivers first and purchasing based upon which seemed easier. I can post instructions for any of them that you would like.

---

### Post by FrodoB on 2006-11-10
Just noticed, the Zonet ZEW2500P does not like to be unplugged while the system is running. Works OK, but does not plug and play like the others.

---

### Post by FrodoB on 2006-11-10
I think that the module:

islsm_usb

may conflict with all you have done with ndiswrapper.  Could you try blacklisting it and see if it helps ndiswrapper?

---

### Post by FrodoB on 2006-11-10
OK, it looks to me ndiswrapper is the only way. It seems like the chipset is supported but not on USB?

---

### Post by FrodoB on 2006-11-10
I also wonder what your .arm file should be named?

---

### Post by FrodoB on 2006-11-10
Some German folks who seem to have solved it, but I cannot understand the Google translation:

[http://translate.google.com/translate?hl=en&sl=de&u=http://www.linux-club.de/viewtopic.php%3Fp%3D149302&sa=X&oi=translate&resnum=3&ct=result&prev=/search%3Fq%3DLinux%2BWG121%2Bndiswrapper%2Bfirmware%26start%3D20%26hl%3Den%26lr%3D%26sa%3DN](http://translate.google.com/translate?hl=en&sl=de&u=http://www.linux-club.de/viewtopic.php%3Fp%3D149302&sa=X&oi=translate&resnum=3&ct=result&prev=/search%3Fq%3DLinux%2BWG121%2Bndiswrapper%2Bfirmware%26start%3D20%26hl%3Den%26lr%3D%26sa%3DN)

---

### Post by FrodoB on 2006-11-11
Note that someone has it working, with issues, but working here:

[http://www.ubuntuforums.org/showthread.php?t=297612](http://www.ubuntuforums.org/showthread.php?t=297612)

---

### Post by oimon on 2006-11-11
hello
this procedure can be followed for the wg121 too (obviously using the wg121 windows drivers with ndiswrapper)
[https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111](https://help.ubuntu.com/community/WifiDocs/Device/NetgearWG111)

However i installed edgy but retained my home directory which already contained the ndiswrapper 1.16 source. therefore i did a "make install" again and used this version. However the blacklist section is very useful because the prism drivers in the kernel don't work, you must therefore override them in the /etc/modprobe.d/blacklist file.
If you have it working correctly, the card will show as a wlan0 device, and not an ethX device.

---

### Post by Jose Catre-Vandis on 2006-11-11
I have just had success with a WG111v2 in edgy (having overcome a vmware problem) using the rtl8187 driver that comes with edgy. Is WG121 similar enough to get picked up by this?

See here:  (and big thanks to FrodoB for guidance)

[http://www.ubuntuforums.org/showpost.php?p=1746116&postcount=6](http://www.ubuntuforums.org/showpost.php?p=1746116&postcount=6)

---

### Post by yawnster on 2006-11-12
hmm.. i will try and follow oimons lead.. seeing as he has got it working..

trying to compile ndiswrapper 1.16 gives me an error message though..

> alex@alex-ubuntu:/usr/src/ndiswrapper-1.16$ sudo make distclean
make -C driver clean
make[1]: Entering directory `/usr/src/ndiswrapper-1.16/driver'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o x86_64_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions
make[1]: Leaving directory `/usr/src/ndiswrapper-1.16/driver'
make -C utils clean
make[1]: Entering directory `/usr/src/ndiswrapper-1.16/utils'
rm -f *~ *.o loadndisdriver
make[1]: Leaving directory `/usr/src/ndiswrapper-1.16/utils'
rm -f *~
rm -fr ndiswrapper-1.16 ndiswrapper-1.16.tar.gz *.deb patch-stamp
make -C driver distclean
make[1]: Entering directory `/usr/src/ndiswrapper-1.16/driver'
rm -rf ndiswrapper.ko ndiswrapper.o hal.o iw_ndis.o loader.o misc_funcs.o ndis.o ntoskernel.o ntoskernel_io.o pe_linker.o pnp.o proc.o wrapmem.o wrapndis.o wrapper.o usb.o divdi3.o usb.o x86_64_stubs.o \
           divdi3.o workqueue.o .*.ko.cmd .*.o.cmd \
           ndiswrapper.mod.[oc] *~ .tmp_versions
rm -f *_exports.h .\#* x86_64_stubs.h
make[1]: Leaving directory `/usr/src/ndiswrapper-1.16/driver'
make -C utils distclean
make[1]: Entering directory `/usr/src/ndiswrapper-1.16/utils'
rm -f *~ *.o loadndisdriver
rm -f .\#*
make[1]: Leaving directory `/usr/src/ndiswrapper-1.16/utils'
rm -f .\#*
alex@alex-ubuntu:/usr/src/ndiswrapper-1.16$ sudo make
make -C driver
make[1]: Entering directory `/usr/src/ndiswrapper-1.16/driver'
make -C /lib/modules/2.6.17-10-generic/build SUBDIRS=/usr/src/ndiswrapper-1.16/driver \
                DRIVER_VERSION=1.16
make[2]: Entering directory `/usr/src/linux-headers-2.6.17-10-generic'
  LD      /usr/src/ndiswrapper-1.16/driver/built-in.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/hal.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/iw_ndis.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/loader.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/misc_funcs.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/ndis.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/ntoskernel.o
/usr/src/ndiswrapper-1.16/driver/ntoskernel.c: In function &#8216;KeClearEvent&#8217;:
/usr/src/ndiswrapper-1.16/driver/ntoskernel.c:1628: warning: value computed is not used
  CC [M]  /usr/src/ndiswrapper-1.16/driver/ntoskernel_io.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/pe_linker.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/pnp.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/proc.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/wrapmem.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/wrapndis.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/wrapper.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/usb.o
  CC [M]  /usr/src/ndiswrapper-1.16/driver/divdi3.o
  LD [M]  /usr/src/ndiswrapper-1.16/driver/ndiswrapper.o
  Building modules, stage 2.
  MODPOST
  CC      /usr/src/ndiswrapper-1.16/driver/ndiswrapper.mod.o
  LD [M]  /usr/src/ndiswrapper-1.16/driver/ndiswrapper.ko
make[2]: Leaving directory `/usr/src/linux-headers-2.6.17-10-generic'
make[1]: Leaving directory `/usr/src/ndiswrapper-1.16/driver'
make -C utils
make[1]: Entering directory `/usr/src/ndiswrapper-1.16/utils'
gcc -g -Wall -DUTILS_VERSION=\"1.8\"  -o loadndisdriver loadndisdriver.c
loadndisdriver.c:15:20: error: stdlib.h: No such file or directory
loadndisdriver.c:16:19: error: stdio.h: No such file or directory
loadndisdriver.c:17:19: error: errno.h: No such file or directory
loadndisdriver.c:18:20: error: string.h: No such file or directory
loadndisdriver.c:19:20: error: libgen.h: No such file or directory
loadndisdriver.c:21:22: error: sys/mman.h: No such file or directory
loadndisdriver.c:23:23: error: sys/types.h: No such file or directory
loadndisdriver.c:24:23: error: sys/ioctl.h: No such file or directory
loadndisdriver.c:25:22: error: sys/stat.h: No such file or directory
loadndisdriver.c:26:20: error: unistd.h: No such file or directory
loadndisdriver.c:27:19: error: fcntl.h: No such file or directory
In file included from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/syslimits.h:7,
                 from /usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:11,
                 from loadndisdriver.c:28:
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h:122:61: error: limits.h: No such file or directory
loadndisdriver.c:29:19: error: ctype.h: No such file or directory
loadndisdriver.c:30:20: error: dirent.h: No such file or directory
loadndisdriver.c:31:20: error: syslog.h: No such file or directory
loadndisdriver.c:34:25: error: linux/major.h: No such file or directory
loadndisdriver.c:35:25: error: linux/ioctl.h: No such file or directory
In file included from loadndisdriver.c:37:
../driver/loader.h:24: error: expected specifier-qualifier-list before &#8216;size_t&#8217;
loadndisdriver.c: In function &#8216;load_file&#8217;:
loadndisdriver.c:67: error: &#8216;size_t&#8217; undeclared (first use in this function)
loadndisdriver.c:67: error: (Each undeclared identifier is reported only once
loadndisdriver.c:67: error: for each function it appears in.)
loadndisdriver.c:67: error: expected &#8216;;&#8217; before &#8216;size&#8217;
loadndisdriver.c:68: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:69: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:71: warning: implicit declaration of function &#8216;basename&#8217;
loadndisdriver.c:71: warning: initialization makes pointer from integer without a cast
loadndisdriver.c:73: warning: implicit declaration of function &#8216;open&#8217;
loadndisdriver.c:73: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;syslog&#8217;
loadndisdriver.c:75: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:75: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:75: warning: implicit declaration of function &#8216;strerror&#8217;
loadndisdriver.c:75: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:76: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:79: warning: implicit declaration of function &#8216;fstat&#8217;
loadndisdriver.c:81: warning: implicit declaration of function &#8216;close&#8217;
loadndisdriver.c:84: error: &#8216;size&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: implicit declaration of function &#8216;mmap&#8217;
loadndisdriver.c:86: error: &#8216;PROT_READ&#8217; undeclared (first use in this function)
loadndisdriver.c:86: error: &#8216;MAP_PRIVATE&#8217; undeclared (first use in this function)
loadndisdriver.c:86: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:87: error: &#8216;MAP_FAILED&#8217; undeclared (first use in this function)
loadndisdriver.c:93: warning: implicit declaration of function &#8216;strncpy&#8217;
loadndisdriver.c:93: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:95: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:96: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:69: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;parse_setting_line&#8217;:
loadndisdriver.c:109: warning: implicit declaration of function &#8216;isspace&#8217;
loadndisdriver.c:115: warning: implicit declaration of function &#8216;strchr&#8217;
loadndisdriver.c:115: warning: incompatible implicit declaration of built-in function &#8216;strchr&#8217;
loadndisdriver.c:115: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:117: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:118: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:138: warning: implicit declaration of function &#8216;strlen&#8217;
loadndisdriver.c:138: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c: In function &#8216;read_conf_file&#8217;:
loadndisdriver.c:150: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:151: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:151: error: &#8216;config&#8217; undeclared (first use in this function)
loadndisdriver.c:157: warning: implicit declaration of function &#8216;lstat&#8217;
loadndisdriver.c:158: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:158: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:159: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:162: warning: implicit declaration of function &#8216;sscanf&#8217;
loadndisdriver.c:162: warning: incompatible implicit declaration of built-in function &#8216;sscanf&#8217;
loadndisdriver.c:178: warning: implicit declaration of function &#8216;fopen&#8217;
loadndisdriver.c:178: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:182: warning: implicit declaration of function &#8216;fgets&#8217;
loadndisdriver.c:194: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:205: warning: implicit declaration of function &#8216;fclose&#8217;
loadndisdriver.c:150: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;load_bin_file&#8217;:
loadndisdriver.c:218: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:218: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:220: warning: implicit declaration of function &#8216;tolower&#8217;
loadndisdriver.c:222: warning: implicit declaration of function &#8216;chdir&#8217;
loadndisdriver.c:223: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:225: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:231: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:233: warning: implicit declaration of function &#8216;ioctl&#8217;
loadndisdriver.c:233: warning: implicit declaration of function &#8216;_IOW&#8217;
loadndisdriver.c:233: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c: In function &#8216;load_driver&#8217;:
loadndisdriver.c:251: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:251: error: &#8216;driver_dir&#8217; undeclared (first use in this function)
loadndisdriver.c:253: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:257: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:257: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:259: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:261: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:263: warning: implicit declaration of function &#8216;opendir&#8217;
loadndisdriver.c:269: warning: implicit declaration of function &#8216;malloc&#8217;
loadndisdriver.c:269: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
loadndisdriver.c:273: warning: implicit declaration of function &#8216;memset&#8217;
loadndisdriver.c:273: warning: incompatible implicit declaration of built-in function &#8216;memset&#8217;
loadndisdriver.c:274: warning: incompatible implicit declaration of built-in function &#8216;strncpy&#8217;
loadndisdriver.c:282: warning: implicit declaration of function &#8216;readdir&#8217;
loadndisdriver.c:282: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:284: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:286: warning: implicit declaration of function &#8216;strcmp&#8217;
loadndisdriver.c:286: error: dereferencing pointer to incomplete type
loadndisdriver.c:287: error: dereferencing pointer to incomplete type
loadndisdriver.c:290: warning: implicit declaration of function &#8216;stat&#8217;
loadndisdriver.c:290: error: dereferencing pointer to incomplete type
loadndisdriver.c:291: warning: implicit declaration of function &#8216;S_ISREG&#8217;
loadndisdriver.c:292: error: dereferencing pointer to incomplete type
loadndisdriver.c:297: warning: incompatible implicit declaration of built-in function &#8216;strlen&#8217;
loadndisdriver.c:297: error: dereferencing pointer to incomplete type
loadndisdriver.c:299: error: dereferencing pointer to incomplete type
loadndisdriver.c:302: error: dereferencing pointer to incomplete type
loadndisdriver.c:305: error: dereferencing pointer to incomplete type
loadndisdriver.c:306: error: dereferencing pointer to incomplete type
loadndisdriver.c:308: error: dereferencing pointer to incomplete type
loadndisdriver.c:314: error: dereferencing pointer to incomplete type
loadndisdriver.c:315: error: dereferencing pointer to incomplete type
loadndisdriver.c:316: warning: implicit declaration of function &#8216;strcpy&#8217;
loadndisdriver.c:316: warning: incompatible implicit declaration of built-in function &#8216;strcpy&#8217;
loadndisdriver.c:317: error: dereferencing pointer to incomplete type
loadndisdriver.c:320: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:321: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:324: error: dereferencing pointer to incomplete type
loadndisdriver.c:284: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c:347: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c:349: warning: implicit declaration of function &#8216;closedir&#8217;
loadndisdriver.c:351: warning: implicit declaration of function &#8216;free&#8217;
loadndisdriver.c:358: warning: implicit declaration of function &#8216;munmap&#8217;
loadndisdriver.c:358: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:358: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c:360: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;data&#8217;
loadndisdriver.c:360: error: &#8216;struct load_driver_file&#8217; has no member named &#8216;size&#8217;
loadndisdriver.c: At top level:
loadndisdriver.c:383: error: expected &#8216;)&#8217; before &#8216;*&#8217; token
loadndisdriver.c: In function &#8216;load_all_devices&#8217;:
loadndisdriver.c:472: error: storage size of &#8216;statbuf&#8217; isn&#8217;t known
loadndisdriver.c:474: error: &#8216;DIR&#8217; undeclared (first use in this function)
loadndisdriver.c:474: error: &#8216;dir&#8217; undeclared (first use in this function)
loadndisdriver.c:474: error: &#8216;driver&#8217; undeclared (first use in this function)
loadndisdriver.c:474: warning: left-hand operand of comma expression has no effect
loadndisdriver.c:474: warning: statement with no effect
loadndisdriver.c:480: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:480: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:480: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:482: error: &#8216;EINVAL&#8217; undeclared (first use in this function)
loadndisdriver.c:484: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:490: warning: incompatible implicit declaration of built-in function &#8216;malloc&#8217;
loadndisdriver.c:496: warning: assignment makes pointer from integer without a cast
loadndisdriver.c:497: error: dereferencing pointer to incomplete type
loadndisdriver.c:498: error: dereferencing pointer to incomplete type
loadndisdriver.c:501: error: dereferencing pointer to incomplete type
loadndisdriver.c:502: warning: implicit declaration of function &#8216;S_ISDIR&#8217;
loadndisdriver.c:504: error: dereferencing pointer to incomplete type
loadndisdriver.c:505: error: dereferencing pointer to incomplete type
loadndisdriver.c:509: error: dereferencing pointer to incomplete type
loadndisdriver.c:510: error: dereferencing pointer to incomplete type
loadndisdriver.c:515: warning: implicit declaration of function &#8216;add_driver_devices&#8217;
loadndisdriver.c:515: error: dereferencing pointer to incomplete type
loadndisdriver.c:531: error: expected expression before &#8216;struct&#8217;
loadndisdriver.c:472: warning: unused variable &#8216;statbuf&#8217;
loadndisdriver.c: In function &#8216;get_ioctl_device&#8217;:
loadndisdriver.c:552: error: &#8216;FILE&#8217; undeclared (first use in this function)
loadndisdriver.c:552: error: &#8216;proc_misc&#8217; undeclared (first use in this function)
loadndisdriver.c:560: warning: implicit declaration of function &#8216;strstr&#8217;
loadndisdriver.c:560: warning: incompatible implicit declaration of built-in function &#8216;strstr&#8217;
loadndisdriver.c:561: warning: implicit declaration of function &#8216;strtol&#8217;
loadndisdriver.c:561: error: &#8216;NULL&#8217; undeclared (first use in this function)
loadndisdriver.c:571: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:571: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:576: warning: implicit declaration of function &#8216;unlink&#8217;
loadndisdriver.c:577: warning: implicit declaration of function &#8216;mknod&#8217;
loadndisdriver.c:577: error: &#8216;S_IFCHR&#8217; undeclared (first use in this function)
loadndisdriver.c:577: error: &#8216;MISC_MAJOR&#8217; undeclared (first use in this function)
loadndisdriver.c:579: error: &#8216;errno&#8217; undeclared (first use in this function)
loadndisdriver.c:584: error: &#8216;O_RDONLY&#8217; undeclared (first use in this function)
loadndisdriver.c: In function &#8216;main&#8217;:
loadndisdriver.c:605: warning: implicit declaration of function &#8216;openlog&#8217;
loadndisdriver.c:605: error: &#8216;LOG_PERROR&#8217; undeclared (first use in this function)
loadndisdriver.c:605: error: &#8216;LOG_CONS&#8217; undeclared (first use in this function)
loadndisdriver.c:605: error: &#8216;LOG_KERN&#8217; undeclared (first use in this function)
loadndisdriver.c:605: error: &#8216;LOG_DEBUG&#8217; undeclared (first use in this function)
loadndisdriver.c:607: error: &#8216;LOG_INFO&#8217; undeclared (first use in this function)
loadndisdriver.c:609: warning: implicit declaration of function &#8216;strncmp&#8217;
loadndisdriver.c:611: warning: implicit declaration of function &#8216;printf&#8217;
loadndisdriver.c:611: warning: incompatible implicit declaration of built-in function &#8216;printf&#8217;
loadndisdriver.c:621: warning: implicit declaration of function &#8216;atoi&#8217;
loadndisdriver.c:636: warning: implicit declaration of function &#8216;atof&#8217;
loadndisdriver.c:668: warning: implicit declaration of function &#8216;closelog&#8217;
make[1]: *** [loadndisdriver] Error 1
make[1]: Leaving directory `/usr/src/ndiswrapper-1.16/utils'
make: *** [all] Error 2
alex@alex-ubuntu:/usr/src/ndiswrapper-1.16$ 

it says im missing some files, but i have installed the kernel source and made the link from /usr/src/linux-`uname -r to /lib/modules/`uname -r`/build

hmmm.. a little stumped..

Tnhanks again guys, you really are doing a superb job for me here, cant thank you enough..Alex

---

### Post by oimon on 2006-11-12
The installer is looking for gcc files - the error mentions that 
/usr/lib/gcc/i486-linux-gnu/4.1.2/include/limits.h
is missing.

Gcc and other compiler stuff is not installed by default with ubuntu (naughty ubuntu). So check that you have it:

test@newt:~$ dpkg --list | grep build-essential
ii  build-essential                            11.3                                 informational list of build-essential packages

IF not, install with 
sudo apt-get install build-essential

And try to recompile.

Oimon

ps
for completeness, here are the kernel headers i have installed:
test@newt:~$ dpkg --list | grep 2.6.17-10
ii  linux-headers-2.6.17-10                    2.6.17-10.33                         Header files related to Linux kernel version
ii  linux-headers-2.6.17-10-generic            2.6.17-10.33                         Linux kernel headers for version 2.6.17 on x
ii  linux-image-2.6.17-10-generic              2.6.17-10.33                         Linux kernel image for version 2.6.17 on x86
ii  linux-libc-dev                             2.6.17-10.33                         Linux Kernel Headers for development
ii  linux-restricted-modules-2.6.17-10-generic 2.6.17.7-1                           Non-free Linux 2.6.17 modules on x86_64 gene

---

### Post by yawnster on 2006-11-12
hehehehe...

its working.. thanks alot to everybody that helped here, FrodoB, Jose and Oimon thanks for the effort I really appreicate this guys.. I will write up the method in a minute so that others can bebenfit from it, seeing as just before I did this I reinstalled Edgy to get a clean slate to work with, so I now know the exact method..

Thanks for sticking with me lol.. Alex

---

### Post by FrodoB on 2006-11-12
Alex;

Great work and I am excited to hear you got. I would be anxious for you to publish a howto explaining this for everyone. 

Best Regards

---

### Post by yawnster on 2006-11-12
[https://help.ubuntu.com/community/WifiDocs/Device/WG121](https://help.ubuntu.com/community/WifiDocs/Device/WG121)

Theres the article. If anyone has the ability to rename it NetgearWG121, I feel it would be more informative. I forgot to name it NetgearWG121 when I created the page, and I dont think I have the ability to change it now..

Thanks again guys.. Alex

---

### Post by Jose Catre-Vandis on 2006-11-12
Pleased to hear you got it all going OK, and a nice write up too :-)

I found I needed ndiswrapper 1.8, and the ndiswrapper kernel source from Synaptic to get things going under ndiswrapper, although as FrodoB pointed out the WG111 v2 runs from the kernel using rtl8187.

---

### Post by oimon on 2006-11-13
nice work - although a couple of typos on the doc:

sudo apt-get install update 
should be
sudo apt-get update 

and 
sudo depmod a
should be 
sudo depmod -a

i should add that having 
blacklist prism2_usb
blacklist islsm_pci
blacklist net2280
in the blacklist is *probably* overkill but i was desperate at the time. there's no harm for me to leave them there now.

---

### Post by FrodoB on 2006-11-13
Gentlemen;

I already had to refer someone to the howto, so I made the changes suggested by oimon. Please check my work for accuracy. 

Thanks to all of you who spent the time and effort, it is already paying off for others.

Best Regards,

FrodoB

---

### Post by yawnster on 2006-11-14
> **oimon said:**
> nice work - although a couple of typos on the doc:

sudo apt-get install update 
should be
sudo apt-get update 

and 
sudo depmod a
should be 
sudo depmod -a

i should add that having 
blacklist prism2_usb
blacklist islsm_pci
blacklist net2280
in the blacklist is *probably* overkill but i was desperate at the time. there's no harm for me to leave them there now.

Aha ok, well make the changes if you feel they are warranted, but I think that Frodo may have already pipped you to the post lol..

Thanks.. Alex

---

### Post by nikkkko on 2007-04-25
Hi and thanks for the howto.  

This thread is old but if someone does happen to read it, I successfully installed ndiswrapper-1.38 for a new Feisty installation with Kubuntu following this guide.  However, I had to also blacklist prism54usb and prism54common as well as the other drivers which are mentioned.

---

### Post by Rickmeister on 2007-04-25
Hey

Absolute new-by. Installed Ubuntu last week and still, after reading 100s of forums can't get internet!!!!!!!
I have got a D-Link DWL-G520+, which worked on windows flawlessly...

If u can help me it would be mostly appreciated, otherwise i'm going back to windows...

---

