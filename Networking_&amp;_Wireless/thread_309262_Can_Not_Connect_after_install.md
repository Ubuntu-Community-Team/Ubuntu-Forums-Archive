---
title: "Can Not Connect after install"
date: 2006-11-29
forum: Networking &amp; Wireless
---

### Post by bxlinux on 2006-11-29
Hello All, I am new to the linux world and I recently installed ubuntu on to my Dell latitude 505. I am unable to connect. I tried to set my dns settings as my desktop pc but still not connection. In my network tools I am recieving and sending bytes and packets but when I try to connect with firefox I am unable to connect. I am unable to ping any website. I am absolutely new to linux so any help would be appreciated.

---

### Post by trubblemaker on 2006-11-29
so you can't connect at all? wireless or network?

can you post the following so I can help you out.

```

lspci | grep controller
cat /etc/network/interfaces
ifconfig 
iwlist scan 

```

also please tell me wireless or network internet, that you want to work with, and please if you have encryption on for either, please remove it until we get you up and running unencrypted first.

---

### Post by albesan on 2006-11-29
hi there, I've got the same problem, shall I make a new post or can I post the output of the code on this thread?

a.

---

### Post by trubblemaker on 2006-11-29
go ahead and post, it will be helpful for all

---

### Post by bxlinux on 2006-11-29
Am I supposed to type the code in the terminal program? Like I said I am new.

---

### Post by bxlinux on 2006-11-29
Oh and this is through the network directly connecting to a cable modem. Not ready for the wireless troubles just yet. :D

---

### Post by trubblemaker on 2006-11-29
yup just fire up a terminal and away you go,

 wired got it.  wireless isn't that bad, but we'll leave it for later

---

### Post by albesan on 2006-11-29
doh! I've just posted a new thread. Anyhow here is the output:

lspci|grep controller
0000:00:10.0 VGA compatible controller ATI Technologies RAGE mobility M3 AGP 2x (rev 2)


cat /etc/network/interfaces

auto lo
iface lo inet loopback
iface dsl-provider
inet ppp
provider dsl-provider

iwlist scan

lo interface doesn't support scanning
eth0 interface doesn't support scanning

ifconfig

lo	link encap: local loopback
	inet addr: 127.0.0.1 Mask: 255.0.0.0
	UP LOOPBACK RUNNING MTU:16436 Metric: 1
	RX packets: 0 errors:0 dropped:0 overuns:0 frame:0
	TX packets:0 errors:0 dropped:0 overuns:0 carrier:0
	
	collisions:0 Txquelen:0
	Rx bytes:0 (0.0b) Tx bytes:0 (0.0b)

---

### Post by bxlinux on 2006-11-29
lspci grep controller (with ethernet connected by the way)
also figured you needed the ethernet controller info if you need the vga let me know
 01:03.0 network controller: Broadcom corporation BCM4309 802.11 a/b/g (rev 03)
 01:08.0 Ethernet controller: intel corporation 82801db Pro/100 VE (mob) Ethernet controller (rev 81)

cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Iwlist scan

lo iterface doesnt support scanning

eth0 interface doesnt support scanning

eth1 no scan results
sit0 interface doesnt support scanning

ifconfig
Eth0
link encap:Ethernet  Hwaddr 00:11:43:3c:6c:f8
inet6 addr: fe80::211:43ff:fe3c:6cf8/64 Scope:Link
up Broadcast Running Multicast  MTU:1500 Metric 1
RX Packets:33314 errors:0 dropped:0 overruns:0 Frame:0
TX packets:44 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
Rx bytes:2047006 (1.9 MiB)  Tx bytes:11880 (11.6 KiB)

Lo
Link encap:Local Loopback
inet addr:127.0.0.1 mask 255.0.0.0
inet6 addr:  ::1/128 scope:Host
Up Loopback Running MTU:16436  Metric:1
RX packets:330 errors:0 dropped:0 overruns:0 Frame:0
tx packets:330 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
Rx bytes:24400 (23.8 KiB) Tx Bytes:24400 (23.8 KiB)

whew lots of typing.

---

### Post by pwall on 2006-11-29
Im also haivng a similar problem
AMD64
just installed  6.10
Wireless
The install configures the network OK - so I assume that means it finds the network at that time (I assume this as I had to drop the netgear router from 108 auto mode to G only before it would configure the  netowrk OK during the install) however when i login it has no internet access

 the lspci command shows 
05:07.0 Ethernet controller: Atheros Communications, Inc,AR5212 802.11abg NIC (REV 01)
 (ath01 is the network card I configured during the instal- so this looks to my uneducated eye)


The Interfaces file contains the secttion for loopback and the primary network interface
auto ath0
ifcase ath0 inet dhcp
    wireless-mode managed
    wireless-essid XXXXX
    wireless-key1 XXXXX

These also look OK to me 

HOWEVER the ifconfig only shows the loopback connections and the iwlist scan commad doesnt list ath0

another fact here is my xserver is failing because I run an ATI RADEON card - but i cant fix this without  downloading stuff - for which I need the network

Any help appreciated.
As an aside. The card connects fine when I boot into windows... so I know that the card works and the distance isnt too far etc etc

Any help appreciated
Ta
Phill

---

### Post by trubblemaker on 2006-11-29
> **albesan said:**
> doh! I've just posted a new thread. Anyhow here is the output:

lspci|grep controller
0000:00:10.0 VGA compatible controller ATI Technologies RAGE mobility M3 AGP 2x (rev 2)


cat /etc/network/interfaces

auto lo
iface lo inet loopback
iface dsl-provider
inet ppp
provider dsl-provider

iwlist scan

lo interface doesn't support scanning
eth0 interface doesn't support scanning

ifconfig

lo	link encap: local loopback
	inet addr: 127.0.0.1 Mask: 255.0.0.0
	UP LOOPBACK RUNNING MTU:16436 Metric: 1
	RX packets: 0 errors:0 dropped:0 overuns:0 frame:0
	TX packets:0 errors:0 dropped:0 overuns:0 carrier:0
	
	collisions:0 Txquelen:0
	Rx bytes:0 (0.0b) Tx bytes:0 (0.0b)

[quote]

k you've got a simple issue your eth0 isn't setup to configure on boot.
try this

[code]
sudo ifconfig eth0 
sudo dhclient eth0
[code] 
then see if you can get on the net.... you have some really wierd connection to you loop back interfaces.  "lo"

if that works we'll have to change your /etc/network/interface file so that it workds on boot.

---

### Post by trubblemaker on 2006-11-29
> **bxlinux said:**
> lspci grep controller (with ethernet connected by the way)
also figured you needed the ethernet controller info if you need the vga let me know
 01:03.0 network controller: Broadcom corporation BCM4309 802.11 a/b/g (rev 03)
 01:08.0 Ethernet controller: intel corporation 82801db Pro/100 VE (mob) Ethernet controller (rev 81)

cat /etc/network/interfaces

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

Iwlist scan

lo iterface doesnt support scanning

eth0 interface doesnt support scanning

eth1 no scan results
sit0 interface doesnt support scanning

ifconfig
Eth0
link encap:Ethernet  Hwaddr 00:11:43:3c:6c:f8
inet6 addr: fe80::211:43ff:fe3c:6cf8/64 Scope:Link
up Broadcast Running Multicast  MTU:1500 Metric 1
RX Packets:33314 errors:0 dropped:0 overruns:0 Frame:0
TX packets:44 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
Rx bytes:2047006 (1.9 MiB)  Tx bytes:11880 (11.6 KiB)

Lo
Link encap:Local Loopback
inet addr:127.0.0.1 mask 255.0.0.0
inet6 addr:  ::1/128 scope:Host
Up Loopback Running MTU:16436  Metric:1
RX packets:330 errors:0 dropped:0 overruns:0 Frame:0
tx packets:330 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:0
Rx bytes:24400 (23.8 KiB) Tx Bytes:24400 (23.8 KiB)

whew lots of typing.


yeah sorry about that, look like your eth0 interface is ready to go to, so if you had a wired connection plugged in you can follow just try
```
 
sudo ifup eth0

```
if you get an ip (check with ifconfig and look at eth0) then try pinging [www.google.ca](www.google.ca)
```
 ping www.google.ca 
``` 
if that works then you should try surfing.  let me know how it goes, also you have a broadcom wirless card so you can checkout my signature for how to get it up and running
|
|
|
V

---

### Post by trubblemaker on 2006-11-29
> **pwall said:**
> Im also haivng a similar problem
AMD64
just installed  6.10
Wireless
The install configures the network OK - so I assume that means it finds the network at that time (I assume this as I had to drop the netgear router from 108 auto mode to G only before it would configure the  netowrk OK during the install) however when i login it has no internet access

 the lspci command shows 
05:07.0 Ethernet controller: Atheros Communications, Inc,AR5212 802.11abg NIC (REV 01)
 (ath01 is the network card I configured during the instal- so this looks to my uneducated eye)


The Interfaces file contains the secttion for loopback and the primary network interface
auto ath0
ifcase ath0 inet dhcp
    wireless-mode managed
    wireless-essid XXXXX
    wireless-key1 XXXXX

These also look OK to me 

HOWEVER the ifconfig only shows the loopback connections and the iwlist scan commad doesnt list ath0

another fact here is my xserver is failing because I run an ATI RADEON card - but i cant fix this without  downloading stuff - for which I need the network

Any help appreciated.
As an aside. The card connects fine when I boot into windows... so I know that the card works and the distance isnt too far etc etc

Any help appreciated
Ta
Phill

open a different thread for the ati issue (all I will say on the issue try "sudo dpkg-reconfigure xorg-xserver")

ok so ath0 installed by default in 6.10 so check dmesg to see if you get any reasons why it's not coming up, I have to say you should remove the encryption until you get it running properly.  try bringing it up manually, with 
```
 sudo ifup ath0 
```  then check dmesg for more useful error output
```
 dmesg 
```

I do know off the top of my head that you have to enable the restricted drivers to get it to work. so you can google that to help yourself, if you  have time and I haven't gotten back to you.  got to run to class, talk to you later.

---

### Post by albesan on 2006-11-29
> **trubblemaker said:**
> [quote]

k you've got a simple issue your eth0 isn't setup to configure on boot.
try this

[code]
sudo ifconfig eth0 
sudo dhclient eth0
[code] 
then see if you can get on the net.... you have some really wierd connection to you loop back interfaces.  "lo"

if that works we'll have to change your /etc/network/interface file so that it workds on boot.
Thanks a lot for that, I'm finally online, writing this without having to reboot to my other OS.
Now, you mentioned having to change something on the /etc/network/interface ,
I really don't want to mess this up now, could you please explain what needs editing?
thanks again.

a.

---

### Post by trubblemaker on 2006-11-29
no worries you need edit this file with your favorite editor
"/etc/network/interfaces"

something like "sudo vim /etc/network/interfaces" or "sudo nano /etc/network/interfaces"

```

auto lo
iface lo inet loopback
#leave the stuff that you already have in the file.
#but add these lines
#  |
#  V
auto eth0
iface eth0 inet dhcp

```

then the interface will come up when you boot.

---

### Post by albesan on 2006-11-29
yes, that got it sorted, thanks again

a.

---

### Post by bxlinux on 2006-11-29
I tried the sudo ifup eth0 and I get the message that eth0 is already configured. I tried to ping [www.google.ca](www.google.ca) and get unknown host. How can I test to see if it is pulling an IP address? Ran Ifconfig and only lo comes up with 127.0.0.1 no ip for eth0.:mad:

---

### Post by bxlinux on 2006-11-29
> **trubblemaker said:**
> yeah sorry about that, look like your eth0 interface is ready to go to, so if you had a wired connection plugged in you can follow just try
```
 
sudo ifup eth0

```
if you get an ip (check with ifconfig and look at eth0) then try pinging [www.google.ca](www.google.ca)
```
 ping www.google.ca 
``` 
if that works then you should try surfing.  let me know how it goes, also you have a broadcom wirless card so you can checkout my signature for how to get it up and running
|
|
|
V

Is there a way to release and try to capture a new ip address?? ](*,)

---

### Post by trubblemaker on 2006-11-29
sure use this to get a new ip
```
 sudo dhclient eth0 
```

---

### Post by bxlinux on 2006-11-30
I tried the sudo ifconfig eth0 command but I recieve the message that No Dhcpoffers received 
no working leases in persistent databases - sleeping. Should I try a static IP address?

---

### Post by bxlinux on 2006-11-30
I am able to ping the default of 127.0.0.1 as I seen in another post I am searching to see what I can find on this matter to no avail. ](*,)

---

### Post by trubblemaker on 2006-11-30
nah static isn't any fun, (well ok if it works why not?) it's really strange that your  not getting a ip from a wired connection, do you have any securtity features turned on? 

is the wire sercurly plugged in? sometimes old ethernet cords can slide out of contact but still look plugged in.  

Can you just for a second plug directly into the net or use a ethernet cord that you know has internet working on it and try the same instruction

```

sudo dhclient eth0

```

---

### Post by bxlinux on 2006-11-30
I tried that. I know the connection works because I am using the same ethernet cable that I have connected to my desktop pc and just moving it back and forth from pc to laptop. No router connected directly to the modem.

---

### Post by bxlinux on 2006-11-30
Not sure if this helps but when I go to network tools for ethernet interface(eth0) here are the info

protocol is Ipv6 

everything under interface info is not available.

But what is crazy is that under interface statistics I am receiving bytes constantly and receiving packets. This is driving me insane.](*,)

---

### Post by bxlinux on 2006-11-30
Sorry to keep flooding but just wanted to let you guys know what I tried. I set an static ip address on my ubuntu laptop. I was unable to ping my desktop pc but my pc can ping the laptop so I know this is not a hardware issue. I even changed the static Ip and tried again and still the pc can ping the laptop but the laptop cannot see anything else. I am using a hub for this.

---

### Post by bxlinux on 2006-11-30
Please Help!!:confused: 

Is there a way to get the ipv6 and set the ethernet card to ipv4. Maybe that would work.

---

### Post by trubblemaker on 2006-12-01
that's just where I was going too. although typically you can get an address and can ping, but can't cruise to websites if ipv6 is messing you up...

regardless it's worth a shot, here's the one-liner to blacklist ipv6

```
echo 'blacklist ipv6' | sudo tee -a /etc/modprobe.d/blacklist
```

then reboot,

---

### Post by bxlinux on 2006-12-01
The frustration continues!
Blacklisted ipv6 and still a no go. I even reinstalled ubuntu 6.06. still the same issue. Still unable to get an ip address and still unable to connect.](*,) ](*,) ](*,)

---

### Post by trubblemaker on 2006-12-01
ok post output of 

```
dmesg
lspci
```

---

### Post by bxlinux on 2006-12-01
Thanks here it is

boogz@boogz-laptop:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f000 (usable)
[17179569.184000]  BIOS-e820: 000000000009f000 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001feaa000 (usable)
[17179569.184000]  BIOS-e820: 000000001feaa000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fec10000 - 00000000fec20000 (reserved)
[17179569.184000]  BIOS-e820: 00000000feda0000 - 00000000fee00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ffb00000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 510MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 130730
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 126634 pages, LIFO batch:31
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 DELL                                  ) @ 0x000fdf00
[17179569.184000] ACPI: RSDT (v001 DELL    CPi R   0x27d5040d ASL  0x00000061) @ 0x1fef0000
[17179569.184000] ACPI: FADT (v001 DELL    CPi R   0x27d5040d ASL  0x00000061) @ 0x1fef0400
[17179569.184000] ACPI: DSDT (v001 INT430 SYSFexxx 0x00001001 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:dec10000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda1 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (0140b000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1698.748 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179573.200000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179573.200000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179573.212000] Memory: 508520k/522920k available (1910k kernel code, 13844k reserved, 1070k data, 308k init, 0k highmem)
[17179573.212000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179573.292000] Calibrating delay using timer specific routine.. 3400.57 BogoMIPS (lpj=6801152)
[17179573.292000] Security Framework v1.0.0 initialized
[17179573.292000] SELinux:  Disabled at boot.
[17179573.292000] Mount-cache hash table entries: 512
[17179573.292000] CPU: After generic identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179573.292000] CPU: After vendor identify, caps: afe9f9bf 00000000 00000000 00000000 00000180 00000000 00000000
[17179573.292000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179573.292000] CPU: L2 cache: 2048K
[17179573.292000] CPU: After all inits, caps: afe9f9bf 00000000 00000000 00000040 00000180 00000000 00000000
[17179573.292000] Checking 'hlt' instruction... OK.
[17179573.308000] SMP alternatives: switching to UP code
[17179573.308000] Freeing SMP alternatives: 16k freed
[17179573.308000] checking if image is initramfs... it is
[17179573.852000] Freeing initrd memory: 5563k freed
[17179573.852000] ACPI: Core revision 20060707
[17179573.860000] ACPI: Looking for DSDT ... not found!
[17179573.860000] ACPI: setting ELCR to 0200 (from 0800)
[17179573.864000] CPU0: Intel(R) Pentium(R) M processor 1.70GHz stepping 06
[17179573.864000] SMP motherboard not detected.
[17179573.864000] Local APIC not detected. Using dummy APIC emulation.
[17179573.864000] Brought up 1 CPUs
[17179573.864000] migration_cost=0
[17179573.864000] NET: Registered protocol family 16
[17179573.864000] EISA bus registered
[17179573.864000] ACPI: bus type pci registered
[17179573.880000] PCI: PCI BIOS revision 2.10 entry at 0xfc96e, last bus=1
[17179573.880000] PCI: Using configuration type 1
[17179573.880000] Setting up standard PCI resources
[17179573.888000] ACPI: Interpreter enabled
[17179573.888000] ACPI: Using PIC for interrupt routing
[17179573.892000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.892000] PCI: Probing PCI hardware (bus 00)
[17179573.892000] ACPI: Assume root bridge [\_SB_.PCI0] bus is 0
[17179573.900000] Boot video device is 0000:00:02.0
[17179573.904000] PCI quirk: region 0800-087f claimed by ICH4 ACPI/GPIO/TCO
[17179573.904000] PCI quirk: region 0880-08bf claimed by ICH4 GPIO
[17179573.904000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179573.904000] PCI: Transparent bridge - 0000:00:1e.0
[17179573.904000] PCI: Bus #02 (-#05) is hidden behind transparent bridge #01 (-#01) (try 'pci=assign-busses')
[17179573.904000] Please report the result to linux-kernel to fix this permanently
[17179573.904000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.928000] ACPI: PCI Interrupt Link [LNKA] (IRQs 9 10 *11)
[17179573.928000] ACPI: PCI Interrupt Link [LNKB] (IRQs 5 7) *11
[17179573.928000] ACPI: PCI Interrupt Link [LNKC] (IRQs 9 10 *11)
[17179573.928000] ACPI: PCI Interrupt Link [LNKD] (IRQs 5 7 9 10 *11)
[17179573.928000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.928000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 5 6 7 9 10 *11 12 14 15)
[17179573.932000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIE._PRT]
[17179573.932000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.932000] pnp: PnP ACPI init
[17179573.960000] pnp: PnP ACPI: found 14 devices
[17179573.960000] PnPBIOS: Disabled by ACPI PNP
[17179573.960000] PCI: Using ACPI for IRQ routing
[17179573.960000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.972000] pnp: 00:02: ioport range 0x4d0-0x4d1 has been reserved
[17179573.972000] pnp: 00:02: ioport range 0x800-0x805 could not be reserved
[17179573.972000] pnp: 00:02: ioport range 0x808-0x80f could not be reserved
[17179573.972000] pnp: 00:03: ioport range 0xf400-0xf4fe has been reserved
[17179573.972000] pnp: 00:03: ioport range 0x806-0x807 has been reserved
[17179573.972000] pnp: 00:03: ioport range 0x810-0x85f could not be reserved
[17179573.972000] pnp: 00:03: ioport range 0x860-0x87f has been reserved
[17179573.972000] pnp: 00:03: ioport range 0x880-0x8bf has been reserved
[17179573.972000] pnp: 00:03: ioport range 0x8c0-0x8df has been reserved
[17179573.972000] pnp: 00:08: ioport range 0x900-0x97f has been reserved
[17179573.972000] pnp: 00:0d: ioport range 0x7b0-0x7bb has been reserved
[17179573.972000] pnp: 00:0d: ioport range 0x7c0-0x7df has been reserved
[17179573.972000] pnp: 00:0d: ioport range 0xbb0-0xbbb has been reserved
[17179573.972000] pnp: 00:0d: ioport range 0xbc0-0xbdf has been reserved
[17179573.972000] pnp: 00:0d: ioport range 0xfb0-0xfbb has been reserved
[17179573.972000] pnp: 00:0d: ioport range 0xfc0-0xfdf has been reserved
[17179573.972000] pnp: 00:0d: ioport range 0x13b0-0x13bb has been reserved
[17179573.972000] pnp: 00:0d: ioport range 0x13c0-0x13df has been reserved
[17179573.972000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179573.972000] PCI: Bus 2, cardbus bridge: 0000:01:01.0
[17179573.972000]   IO window: 0000e000-0000e0ff
[17179573.972000]   IO window: 0000e400-0000e4ff
[17179573.972000]   PREFETCH window: 30000000-31ffffff
[17179573.972000]   MEM window: 34000000-35ffffff
[17179573.972000] PCI: Bridge: 0000:00:1e.0
[17179573.972000]   IO window: e000-efff
[17179573.972000]   MEM window: fc000000-fdffffff
[17179573.972000]   PREFETCH window: 30000000-31ffffff
[17179573.972000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179573.972000] PCI: Enabling device 0000:01:01.0 (0000 -> 0003)
[17179573.972000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 11
[17179573.972000] PCI: setting IRQ 11 as level-triggered
[17179573.972000] ACPI: PCI Interrupt 0000:01:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179573.972000] NET: Registered protocol family 2
[17179574.012000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179574.012000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179574.012000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179574.012000] TCP: Hash tables configured (established 16384 bind 8192)
[17179574.012000] TCP reno registered
[17179574.012000] audit: initializing netlink socket (disabled)
[17179574.012000] audit(1165012447.012:1): initialized
[17179574.012000] VFS: Disk quotas dquot_6.5.1
[17179574.012000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179574.012000] Initializing Cryptographic API
[17179574.012000] io scheduler noop registered
[17179574.012000] io scheduler anticipatory registered
[17179574.012000] io scheduler deadline registered
[17179574.012000] io scheduler cfq registered (default)
[17179574.012000] isapnp: Scanning for PnP cards...
[17179574.364000] isapnp: No Plug & Play device found
[17179574.384000] Real Time Clock Driver v1.12ac
[17179574.384000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.384000] serial8250: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.384000] 00:0b: ttyS0 at I/O 0x3f8 (irq = 4) is a 16550A
[17179574.384000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179574.384000] PCI: setting IRQ 5 as level-triggered
[17179574.384000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179574.384000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179574.384000] mice: PS/2 mouse device common for all mice
[17179574.388000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.388000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.388000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.388000] PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179574.392000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179574.392000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.392000] EISA: Probing bus 0 at eisa.0
[17179574.392000] EISA: Detected 0 cards.
[17179574.392000] TCP bic registered
[17179574.392000] NET: Registered protocol family 1
[17179574.392000] NET: Registered protocol family 8
[17179574.392000] NET: Registered protocol family 20
[17179574.392000] Using IPI No-Shortcut mode
[17179574.392000] ACPI: (supports S0 S1 S3 S4 S5)
[17179574.392000] Freeing unused kernel memory: 308k freed
[17179574.400000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.512000] Capability LSM initialized
[17179575.540000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3] C4[C3])
[17179575.540000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179575.544000] ACPI: Thermal Zone [THM] (42 C)
[17179575.788000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179575.788000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179575.788000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179575.788000] ICH4: chipset revision 1
[17179575.788000] ICH4: not 100% native mode: will probe irqs later
[17179575.788000]     ide0: BM-DMA at 0xbfa0-0xbfa7, BIOS settings: hda:DMA, hdb:pio
[17179575.788000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:pio, hdd:pio
[17179575.788000] Probing IDE interface ide0...
[17179576.080000] hda: TOSHIBA MK4026GAX, ATA DISK drive
[17179576.752000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.800000] Probing IDE interface ide1...
[17179577.372000] hda: max request size: 128KiB
[17179577.372000] hda: 78140160 sectors (40007 MB), CHS=65535/16/63, UDMA(100)
[17179577.372000] hda: cache flushes supported
[17179577.372000]  hda: hda1 hda2 < hda5 >
[17179577.676000] Probing IDE interface ide1...
[17179577.700000] usbcore: registered new driver usbfs
[17179577.700000] usbcore: registered new driver hub
[17179577.700000] USB Universal Host Controller Interface driver v3.0
[17179577.704000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179577.704000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179577.704000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179577.704000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179577.704000] uhci_hcd 0000:00:1d.0: irq 11, io base 0x0000bf80
[17179577.704000] usb usb1: configuration #1 chosen from 1 choice
[17179577.704000] hub 1-0:1.0: USB hub found
[17179577.704000] hub 1-0:1.0: 2 ports detected
[17179577.752000] ieee1394: Initialized config rom entry `ip1394'
[17179577.808000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179577.808000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179577.808000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179577.808000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179577.808000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179577.808000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x0000bf40
[17179577.808000] usb usb2: configuration #1 chosen from 1 choice
[17179577.808000] hub 2-0:1.0: USB hub found
[17179577.808000] hub 2-0:1.0: 2 ports detected
[17179577.912000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 11
[17179577.912000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 11 (level, low) -> IRQ 11
[17179577.912000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179577.912000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179577.912000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179577.912000] uhci_hcd 0000:00:1d.2: irq 11, io base 0x0000bf20
[17179577.912000] usb usb3: configuration #1 chosen from 1 choice
[17179577.912000] hub 3-0:1.0: USB hub found
[17179577.912000] hub 3-0:1.0: 2 ports detected
[17179578.016000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 11
[17179578.016000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 11 (level, low) -> IRQ 11
[17179578.016000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179578.016000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179578.016000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179578.016000] ehci_hcd 0000:00:1d.7: debug port 1
[17179578.016000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179578.016000] ehci_hcd 0000:00:1d.7: irq 11, io mem 0xfaeffc00
[17179578.020000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.020000] usb usb4: configuration #1 chosen from 1 choice
[17179578.020000] hub 4-0:1.0: USB hub found
[17179578.020000] hub 4-0:1.0: 6 ports detected
[17179578.124000] ACPI: PCI Interrupt 0000:01:01.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179578.180000] ohci1394: fw-host0: OHCI-1394 1.1 (PCI): IRQ=[11]  MMIO=[fcfff800-fcffffff]  Max Packet=[2048]  IR/IT contexts=[4/8]
[17179578.404000] Attempting manual resume
[17179578.456000] kjournald starting.  Commit interval 5 seconds
[17179578.456000] EXT3-fs: mounted filesystem with ordered data mode.
[17179578.572000] usb 4-3: new high speed USB device using ehci_hcd and address 2
[17179578.704000] usb 4-3: configuration #1 chosen from 1 choice
[17179579.264000] usb 3-1: new full speed USB device using uhci_hcd and address 2
[17179579.448000] usb 3-1: configuration #1 chosen from 1 choice
[17179579.452000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[474fc00003cea0e1]
[17179588.684000] input: PC Speaker as /class/input/input1
[17179588.872000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.880000] agpgart: Detected an Intel 855 Chipset.
[17179588.880000] agpgart: Detected 892K stolen memory.
[17179588.888000] agpgart: AGP aperture is 128M @ 0xf0000000
[17179589.216000] parport: PnPBIOS parport detected.
[17179589.216000] parport0: PC-style at 0x378 (0x778), irq 7, dma 1 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179589.228000] input: PS/2 Mouse as /class/input/input2
[17179589.248000] input: AlpsPS/2 ALPS GlidePoint as /class/input/input3
[17179589.288000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179589.292000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179589.376000] hw_random: cannot enable RNG, aborting
[17179589.648000] ts: Compaq touchscreen protocol output
[17179589.724000] usbcore: registered new driver libusual
[17179589.780000] SCSI subsystem initialized
[17179589.784000] Initializing USB Mass Storage driver...
[17179589.784000] scsi0 : SCSI emulation for USB Mass Storage devices
[17179589.784000] usb-storage: device found at 2
[17179589.784000] usb-storage: waiting for device to settle before scanning
[17179589.784000] scsi1 : SCSI emulation for USB Mass Storage devices
[17179589.784000] usbcore: registered new driver usb-storage
[17179589.784000] USB Mass Storage support registered.
[17179589.784000] usb-storage: device found at 2
[17179589.784000] usb-storage: waiting for device to settle before scanning
[17179589.856000] ACPI: PCI Interrupt 0000:01:01.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179589.856000] Yenta: CardBus bridge found at 0000:01:01.0 [1028:0163]
[17179589.856000] Yenta: Using CSCINT to route CSC interrupts to PCI
[17179589.856000] Yenta: Routing CardBus interrupts to PCI
[17179589.856000] Yenta TI: socket 0000:01:01.0, mfunc 0x012c1222, devctl 0x64
[17179590.144000] ieee80211_crypt: registered algorithm 'NULL'
[17179590.148000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179590.148000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179590.164000] Yenta: ISA IRQ mask 0x0458, PCI irq 11
[17179590.164000] Socket status: 30000086
[17179590.164000] Yenta: Raising subordinate bus# of parent bus (#01) from #01 to #05
[17179590.164000] pcmcia: parent PCI bridge I/O window: 0xe000 - 0xefff
[17179590.164000] cs: IO port probe 0xe000-0xefff: clean.
[17179590.164000] pcmcia: parent PCI bridge Memory window: 0xfc000000 - 0xfdffffff
[17179590.164000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x31ffffff
[17179590.164000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179590.164000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179590.212000] bcm43xx driver
[17179590.252000] e100: Intel(R) PRO/100 Network Driver, 3.5.10-k2-NAPI
[17179590.252000] e100: Copyright(c) 1999-2005 Intel Corporation
[17179590.560000] cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x370-0x37f
[17179590.560000] cs: IO port probe 0x3e0-0x4ff: clean.
[17179590.560000] cs: IO port probe 0x820-0x8ff: clean.
[17179590.560000] cs: IO port probe 0xc00-0xcf7: clean.
[17179590.560000] cs: IO port probe 0xa00-0xaff: clean.
[17179590.984000] intel8x0_measure_ac97_clock: measured 55504 usecs
[17179590.984000] intel8x0: clocking to 48000
[17179590.984000] ACPI: PCI Interrupt 0000:01:03.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179590.988000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 11
[17179590.988000] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [LNKE] -> GSI 11 (level, low) -> IRQ 11
[17179591.012000] e100: eth1: e100_probe: addr 0xfcffe000, irq 11, MAC addr 00:11:43:3C:6C:F8
[17179591.164000] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
[17179591.240000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179591.248000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179591.248000] lp0: using parport0 (interrupt-driven).
[17179591.268000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179591.268000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179591.288000] Adding 1510068k swap on /dev/disk/by-uuid/a06dbe19-3d4c-4a5c-bc20-033b0b3f790e.  Priority:-1 extents:1 across:1510068k
[17179591.360000] EXT3 FS on hda1, internal journal
[17179592.240000] NET: Registered protocol family 17
[17179594.784000] usb-storage: device scan complete
[17179594.784000] usb-storage: device scan complete
[17179594.784000]   Vendor: Memorex   Model: DVD16+/-DL4RWlD2  Rev: JWS6
[17179594.784000]   Type:   CD-ROM                             ANSI SCSI revision: 00
[17179594.800000]   Vendor: SONY      Model: USB-FDU           Rev: 6.01
[17179594.800000]   Type:   Direct-Access                      ANSI SCSI revision: 00
[17179594.816000] scsi: unknown device type 31
[17179594.816000]   Vendor: SONY      Model: USB-FDU           Rev: 6.01
[17179594.816000]   Type:   Unknown                            ANSI SCSI revision: 00
[17179594.832000] scsi: unknown device type 31
[17179594.832000]   Vendor: SONY      Model: USB-FDU           Rev: 6.01
[17179594.832000]   Type:   Unknown                            ANSI SCSI revision: 00
[17179594.848000] scsi: unknown device type 31
[17179594.848000]   Vendor: SONY      Model: USB-FDU           Rev: 6.01
[17179594.848000]   Type:   Unknown                            ANSI SCSI revision: 00
[17179594.864000] scsi: unknown device type 31
[17179594.864000]   Vendor: SONY      Model: USB-FDU           Rev: 6.01
[17179594.864000]   Type:   Unknown                            ANSI SCSI revision: 00
[17179594.880000] scsi: unknown device type 31
[17179594.880000]   Vendor: SONY      Model: USB-FDU           Rev: 6.01
[17179594.880000]   Type:   Unknown                            ANSI SCSI revision: 00
[17179594.896000] scsi: unknown device type 31
[17179594.896000]   Vendor: SONY      Model: USB-FDU           Rev: 6.01
[17179594.896000]   Type:   Unknown                            ANSI SCSI revision: 00
[17179594.912000] scsi: unknown device type 31
[17179594.912000]   Vendor: SONY      Model: USB-FDU           Rev: 6.01
[17179594.912000]   Type:   Unknown                            ANSI SCSI revision: 00
[17179595.036000] sd 1:0:0:0: Attached scsi generic sg0 type 0
[17179595.036000]  1:0:0:1: Attached scsi generic sg1 type 31
[17179595.036000]  1:0:0:2: Attached scsi generic sg2 type 31
[17179595.036000]  1:0:0:3: Attached scsi generic sg3 type 31
[17179595.036000]  1:0:0:4: Attached scsi generic sg4 type 31
[17179595.036000]  1:0:0:5: Attached scsi generic sg5 type 31
[17179595.036000]  1:0:0:6: Attached scsi generic sg6 type 31
[17179595.036000]  1:0:0:7: Attached scsi generic sg7 type 31
[17179595.040000]  0:0:0:0: Attached scsi generic sg8 type 5
[17179595.072000] sd 1:0:0:0: Attached scsi removable disk sda
[17179595.100000] sr0: scsi3-mmc drive: 48x/48x writer cd/rw xa/form2 cdda tray
[17179595.100000] Uniform CD-ROM driver Revision: 3.20
[17179595.100000] sr 0:0:0:0: Attached scsi CD-ROM sr0
[17179595.956000] ACPI: AC Adapter [AC] (on-line)
[17179596.256000] ACPI: Battery Slot [BAT0] (battery present)
[17179596.256000] ACPI: Battery Slot [BAT1] (battery absent)
[17179596.268000] ACPI: Lid Switch [LID]
[17179596.268000] ACPI: Power Button (CM) [PBTN]
[17179596.268000] ACPI: Sleep Button (CM) [SBTN]
[17179596.324000] ACPI: ACPI Dock Station Driver 
[17179596.492000] ibm_acpi: ec object not found
[17179596.532000] pcc_acpi: loading...
[17179596.780000] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[17179596.780000] ACPI: Video Device [VID2] (multi-head: yes  rom: no  post: no)
[17179598.552000] [drm] Initialized drm 1.0.1 20051102
[17179598.556000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 11 (level, low) -> IRQ 11
[17179598.556000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179598.556000] [drm] Initialized i915 1.5.0 20060119 on minor 1
[17179599.544000] apm: BIOS not found.
[17179604.388000] Bluetooth: Core ver 2.8
[17179604.388000] NET: Registered protocol family 31
[17179604.388000] Bluetooth: HCI device and connection manager initialized
[17179604.388000] Bluetooth: HCI socket layer initialized
[17179604.412000] Bluetooth: L2CAP ver 2.8
[17179604.412000] Bluetooth: L2CAP socket layer initialized
[17179604.448000] Bluetooth: RFCOMM socket layer initialized
[17179604.448000] Bluetooth: RFCOMM TTY layer initialized
[17179604.448000] Bluetooth: RFCOMM ver 1.7
[17179618.200000] NET: Registered protocol family 10
[17179618.200000] lo: Disabled Privacy Extensions
[17179618.200000] IPv6 over IPv4 tunneling driver
[17179628.504000] eth0: no IPv6 routers present
[17180319.372000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17180319.376000] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
[17180320.280000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[17180331.124000] eth0: no IPv6 routers present
[17195655.376000] e100: eth0: e100_watchdog: link down
[17195665.376000] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
[17195697.376000] e100: eth0: e100_watchdog: link down
[17195707.376000] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
[17195723.376000] e100: eth0: e100_watchdog: link down
[17195737.376000] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
[17195759.376000] e100: eth0: e100_watchdog: link down
[17195771.376000] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
[17200019.376000] e100: eth0: e100_watchdog: link down
[17200097.376000] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
[17200269.376000] e100: eth0: e100_watchdog: link down
[17200305.376000] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
[17200365.376000] e100: eth0: e100_watchdog: link down
[17200383.376000] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
[17201184.100000] usb 4-3: USB disconnect, address 2

---

### Post by bxlinux on 2006-12-02
Here is the lspci

00:00.0 Host bridge: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.1 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:00.3 System peripheral: Intel Corporation 82852/82855 GM/GME/PM/GMV Processor to I/O Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DBM (ICH4-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DBM (ICH4-M) IDE Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
00:1f.6 Modem: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Modem Controller (rev 01)
01:01.0 CardBus bridge: Texas Instruments PCI4510 PC card Cardbus Controller (rev 02)
01:01.1 FireWire (IEEE 1394): Texas Instruments PCI4510 IEEE-1394 Controller
01:03.0 Network controller: Broadcom Corporation BCM4309 802.11a/b/g (rev 03)
01:08.0 Ethernet controller: Intel Corporation 82801DB PRO/100 VE (MOB) Ethernet Controller (rev 81)

---

### Post by trubblemaker on 2006-12-02
> [17179591.012000] e100: eth1: e100_probe: addr 0xfcffe000, irq 11, MAC addr 00:11:43:3C:6C:F8
[17179591.164000] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
[17179591.240000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[17179591.248000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
this is the intersting stuff, so you haven't setup your broad come card yet. and ```

[17180319.372000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17180319.376000] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
[17180320.280000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
```
isn't good means you tried to do something before the driver was ready.

found another post with similar error this was [the solution post]("http://www.ubuntuforums.org/showpost.php?p=159853&postcount=5")

looks like it was a irq issue.

another option is to get your bcm card setup to do that check the howto's in my signature.  Hope this helps

---

### Post by bxlinux on 2006-12-02
Will try this again maybe I missed something.

---

### Post by bxlinux on 2006-12-02
Oh and no wireless router so I am not doing my wireless card just yet.:evil:

---

### Post by bxlinux on 2006-12-02
Tried again to reinstall with the noapic nolapic command but still no ip address showing up for the eth0. I am however now getting transmitted packets so I am getting closer. they are steadily rising. Protocol is still Ipv6 and turned that off in firefox but still not getting any ip address. Cannot ping anything outside of the ethernet card. 

i quit for the night tomorrow is a new day

---

### Post by trubblemaker on 2006-12-02
it's not really re-installing so much as booting with noapic as an option.  do you have a spare nic, hanging around? that you can swap in?  if you're getting packets can you ping the router or ping anything else? lets disable ipv6 as it's not really necessary:

```
echo 'blacklist ipv6' | sudo tee -a /etc/modprobe.d/blacklist
```

now can you try this, boot up, 
```

dmesg | grep eth0
ifconfig
sudo ifconfig eth0 up
sudo dhclient wlan0
dmesg | grep eth0
route
cat /etc/network/interfaces

```

also lets

---

### Post by bxlinux on 2006-12-02
OK I blacklisted ipv6 and still cannot ping anything. I also ran the other codes and still unable to pull an IP address. I do not have any spare ethernet cards as this is a laptop that I am using. Do you need to see the results of the codes I ran? Everything looks good as far as I can tell.

---

### Post by trubblemaker on 2006-12-02
yeah it'd help me figure out where we're at.

---

### Post by bxlinux on 2006-12-02
Ok Here is the motherload of infor

badnewz@boogz-laptop:~$ dmesg | grep eth0
[17179586.096000] e100: eth0: e100_probe: addr 0xfcffe000, irq 11, MAC addr 00:11:43:3C:6C:F8
[17179586.228000] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
badnewz@boogz-laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:3C:6C:F8  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1452 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:96966 (94.6 KiB)  TX bytes:2052 (2.0 KiB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5964 (5.8 KiB)  TX bytes:5964 (5.8 KiB)

badnewz@boogz-laptop:~$ sudo ifconfig eth0 up
Password:
badnewz@boogz-laptop:~$ sudo dhclient wlan0
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
wlan0: ERROR while getting interface flags: No such device
wlan0: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
badnewz@boogz-laptop:~$ dmesg | grep eth0
[17179586.096000] e100: eth0: e100_probe: addr 0xfcffe000, irq 11, MAC addr 00:11:43:3C:6C:F8
[17179586.228000] e100: eth0: e100_watchdog: link up, 100Mbps, half-duplex
badnewz@boogz-laptop:~$ route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
badnewz@boogz-laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet dhcp

auto eth2
iface eth2 inet dhcp

auto ath0
iface ath0 inet dhcp

auto wlan0
iface wlan0 inet dhcp

badnewz@boogz-laptop:~$ ping [www.google.com](www.google.com)
ping: unknown host [www.google.com](www.google.com)
badnewz@boogz-laptop:~$ ping 66.65.87.244
connect: Network is unreachable
badnewz@boogz-laptop:~$ sudo lshw -C network
  *-network:0 DISABLED    
       description: Wireless interface
       product: BCM4309 802.11a/b/g
       vendor: Broadcom Corporation
       physical id: 3
       bus info: pci@01:03.0
       logical name: eth1
       version: 03
       serial: 00:0b:7d:20:f5:6f
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master ethernet physical wireless
       configuration: broadcast=yes driver=bcm43xx driverversion=2.6.17-10-generic link=no multicast=yes wireless=IEEE 802.11b/g
       resources: iomemory:fcffc000-fcffdfff irq:5
  *-network:1
       description: Ethernet interface
       product: 82801DB PRO/100 VE (MOB) Ethernet Controller
       vendor: Intel Corporation
       physical id: 8
       bus info: pci@01:08.0
       logical name: eth0
       version: 81
       serial: 00:11:43:3c:6c:f8
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegociation
       configuration: autonegociation=on broadcast=yes driver=e100 driverversion=3.5.10-k2-NAPI duplex=half firmware=N/A link=yes multicast=yes port=MII speed=100MB/s
       resources: iomemory:fcffe000-fcffefff ioport:ecc0-ecff irq:11

---

### Post by trubblemaker on 2006-12-02
stupid me I was thinking my nic, i need you to use 

```
sudo dhclient [COLOR="Red"]eth0[/COLOR]
dmesg | grep eth0
route

```

---

### Post by bxlinux on 2006-12-02
Trubblemkr I appreciate all the help you have been given me and everyone else on the boards. It reads as follows.

There is already a pid file /var/run/dhclient.pid with pid 134993416
Internet systems Consortium DHCP Client V3.0.4

Listening on LPF/eth0/00:11:43:3c:6c:f8
sending on LPF/eth0/00:11:43:3c:6c:f8
sending on Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 14
No DHCPOFFERS received
No working leases in persistent database - sleeping

dmesg | grep eth0
[17179586.096000] e100: eth0: e100_probe: addr 0xfxffe000, irq 11, MAC addr 00:11:43:3c:6c:f8
[1719586.228000] e100: eth0: e100_watchdog: link up, 100mbps. half duplex

route
Kernel IP routing table
Destination    Gatewy   Genmask     flags metric ref use Iface

There it is. How do I change from half duplex to full. Not sure that would help anyway.

---

### Post by bxlinux on 2006-12-02
While waiting I entered in a static ip address. Again my windows pc can ping the linux laptop with no problem. BUT my linux laptop cannot ping anything still. I am so frustrated! :confused:

---

### Post by trubblemaker on 2006-12-02
Sorry studying for finals

I've seen this before
> [COLOR="Red"]There is already a pid file /var/run/dhclient.pid with pid 134993416[/COLOR]
Internet systems Consortium DHCP Client V3.0.4

try:

```
cp /var/run/dhclient.pid /home/your-slick-username
rm /var/run/dhclient.pid 
sudo dhclient eth0
```

if no change don't think it matters if pid is missing, think it will just make another but if it messes you up just mv it back.

---

### Post by bxlinux on 2006-12-02
still no dhcp offers. I tried to ping my other pc and network still unavailable.

---

### Post by bxlinux on 2006-12-03
I am starting to think it may be a hardware issue. Although what I dont understand is how it can detect the ethernet card with no problem and also when I set static I get a reply back from my windows pc which to me means that the hardware is working. I tried to run another version of linux live cd and the same issue happened. Maybe it just isnt compatible with linux. I dont know. ](*,)

---

### Post by trubblemaker on 2006-12-03
ok found your exact card with the exact driver and the same issue, it looks like an IRQ issue so there is what you need to do.  We talked about it before but I don't know to what extent you looked into it.

edit your boot configuration:

sudo vim /boot/grub/menu.lst

[COLOR="Red"]look for this in the file[/COLOR]

```


## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=ffff5849-1790-47d2-8888-aaaaaaaaaaa ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-386
[COLOR="Red"]savedefault[/COLOR]
boot

title           Ubuntu, kernel 2.6.17-10-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=fe4d5849-1790-47d2-8a6f-a17dc8719a78 ro single
initrd          /boot/initrd.img-2.6.17-10-386
boot

```
this tells you which entry is used to boot by default

then you need to[COLOR="Red"] add this [/COLOR]to your default entry:
(you need to scroll the panel below to see it.)
```

title           Ubuntu, kernel 2.6.17-10-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-386 root=UUID=ffff5849-1790-47d2-8888-aaaaaaaaaaa ro quiet splash [COLOR="Red"]noapic[/COLOR]
initrd          /boot/initrd.img-2.6.17-10-386
savedefault
boot

```

this is a common addition as a boot parameter for hardware that kinda works but breaks alot, I've had to do this for my cdrom in old hp machines.

It would explain why it can be pinged but then not work properly.

---

### Post by bxlinux on 2006-12-04
So I am just to add that and not delete anything. By the way when I did load windows it worked fine got to the internet right away so it is not an issue with the hardware. Can I do this with live cd just to test?

---

### Post by bxlinux on 2006-12-04
when I ran that command I do not see any of the above mentioned. Should I just add it?

---

### Post by bxlinux on 2006-12-04
I do see what you are talking about but for some reason I am unable to edit it at all. How can I add that info. Let me tell you what it says though.

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
quiet
boot

---

### Post by trubblemaker on 2006-12-04
try 

sudo nano /boot/grub/menu.lst

sudo gedit /boot/grub/menu.lst

sorry vim is an editor and takes some getting used to....

---

### Post by bxlinux on 2006-12-04
Ok i typed it in but and rebooted. Still unable to pull an ip address or ping anything. I also tried the ifdown eth0 and ifup eth0. No dhcpoffers received. Tried again with a static ip and my pc can ping the linux machine but not the other way around. Maybe I should just wrap it up on linux with this machine and see what happens when I build another.

---

### Post by trubblemaker on 2006-12-05
can you post :

```

cat /boot/grub/menu.lst

``` 

so  I can check it?

---

### Post by 1Ank1 on 2006-12-05
try doing what bsherman outlines in this thread [http://ubuntuforums.org/showthread.php?t=2620](http://ubuntuforums.org/showthread.php?t=2620) and see how you go, that is if you haven't already tried it:-k

---

### Post by msd79m on 2006-12-09
Hi,
I had this problem but finally solved it today!

I have two operating systems on my PC: Win XP and Ubuntu. Although I hadn't any problem on Win XP, Ubuntu could not connect to LAN. I found out my PC can't get IP address from DHCP server (no DHCPoffres received).
I tested all of suggested methods by other guys, but no result. Even I installed some other linux  distros on my PC, but they had this problem, too.

Reason:
Ubuntu's hostname was different from Win XP's! I think when my PC requests an IP from DHCP server, the server checks the MAC address (physical address) of my PC and when it detects that this MAC address has been registered for another hostname, it rejects the request.

I hope this helps you to solve your problem.

---

### Post by msd79m on 2006-12-12
I can not connect to the network using Ubuntu after hibernating Win XP. I think Win XP has a bug in Hibernation! it does not release the network connection.

---

### Post by bxlinux on 2006-12-12
Hey guys I am back for more punishment. I tried bshermans thread but to no avail. Again I am working off of a laptop. I uninstalled xp and reinstalled ubuntu again. So now ubuntu is the only os on my laptop. I tried everything once again that was mentioned in this thread and by the way thank you all for your help. I am sure eventually I will get it and enjoy unix. If there are any other ideas that anyone may have I will be glad to listen. If I should start a new thread please let me know just didnt want guys to put down steps already mentioned.

---

### Post by trubblemaker on 2006-12-12
glad to see you back, I saw in another thread someones router was being really secure so if it saw a different user name with the same nic it wouldn't let the user get an ip.  Might be something you should check out.

---

### Post by trubblemaker on 2006-12-12
start with making the change to you /boot/grub/menu.lst.  did the network connection get detected on installation?

---

### Post by bxlinux on 2006-12-12
I did the change but I am still unable to get an ip address if thats what you mean???

---

### Post by bxlinux on 2006-12-13
If anyone has anything that I can possibly try please let me know. ](*,)

---

### Post by bxlinux on 2006-12-13
I checked out this thread about wired ethernet [http://doc.gwos.org/index.php/Wired_Ethernet_Troubleshooting](http://doc.gwos.org/index.php/Wired_Ethernet_Troubleshooting). I tried all of the steps but still unable to get my ethernet card to get any IP address. My ifconfig reads as follows:

ifconfig
Eth0
link encap:Ethernet Hwaddr 00:11:43:3c:6c:f8
inet6 addr: fe80::211:43ff:fe3c:6cf8/64 Scope:Link
up Broadcast Running Multicast MTU:1500 Metric 1
RX Packets:33314 errors:0 dropped:0 overruns:0 Frame:0
TX packets:44 errors:0 dropped:0 overruns:0 carrier:0 collisions:0 txqueuelen:1000
Rx bytes:2047006 (1.9 MiB) Tx bytes:11880 (11.6 KiB)

---

### Post by bxlinux on 2006-12-13
Well I have been at this linux thing for about 3 weeks and still havent been able to resolve an issue. I even tried different distros with the same issue. Maybe its just this laptop but I cant phathom why it would be so difficult to get some internet access for an intel ethernet card. WOW! I really liked the idea of putting ubuntu on my laptop to get away from windows but i guess its just not for this machine. I did get some great assistance and have learned alot none of (which worked) steps in troubleshooting. And I did appreciate the help. Wish you all well but back to windows for me.

---

### Post by urk_nono on 2006-12-13
> **bxlinux said:**
> Well I have been at this linux thing for about 3 weeks and still havent been able to resolve an issue. I even tried different distros with the same issue. Maybe its just this laptop but I cant phathom why it would be so difficult to get some internet access for an intel ethernet card. WOW! I really liked the idea of putting ubuntu on my laptop to get away from windows but i guess its just not for this machine. I did get some great assistance and have learned alot none of (which worked) steps in troubleshooting. And I did appreciate the help. Wish you all well but back to windows for me.

Sorry to hear, wish I could supply you with some good guidance, but unfortunately I'm a nooblet.

---

### Post by wpshooter on 2006-12-13
Which distribution of of Ubuntu were you trying to install, Dapper or Edgy and were you trying to install from the DESKTOP CD or from the ALTERNATE CD ?

If you have not given the ALTERNATE CD a try, I would suggest that you try it.  I believe it is better at hardware configuration than the DESKTOP (Live CD) version.

---

### Post by drphilngood on 2006-12-13
> **wpshooter said:**
> Which distribution of of Ubuntu were you trying to install, Dapper or Edgy and were you trying to install from the DESKTOP CD or from the ALTERNATE CD ?

If you have not given the ALTERNATE CD a try, I would suggest that you try it.  I believe it is better at hardware configuration than the DESKTOP (Live CD) version.

I´ll second that.  I´ve seen many that were ready to quit become happy Ubuntu users after installing from the Alternate installer CD; it´s all I ever use.

---

### Post by bxlinux on 2006-12-14
I believe it was the edgy. How can I tell?

---

### Post by macogw on 2006-12-14
Dapper = 6.06
Edgy = 6.10

Also, you may want to try getting the driver and saving it on a floppy or cd then installing it with ndiswrapper

---

### Post by unisol on 2006-12-14
what are you laptops system specs?

---

### Post by az on 2006-12-14
In windows, did you have to provide a username and password when you initially set up your internet connection?

You say cable, but is it in fact DSL?

If that is so, you need to connect using pppoe.

sudo pppoeconf


Also, can you run the live cd on your desktop and use the internet?

---

### Post by az on 2006-12-14
> **bxlinux said:**
> Well I have been at this linux thing for about 3 weeks and still havent been able to resolve an issue. I even tried different distros with the same issue. Maybe its just this laptop but I cant phathom why it would be so difficult to get some internet access for an intel ethernet card. WOW! I really liked the idea of putting ubuntu on my laptop to get away from windows but i guess its just not for this machine. I did get some great assistance and have learned alot none of (which worked) steps in troubleshooting. And I did appreciate the help. Wish you all well but back to windows for me.

I dove into you other thread.

---

### Post by deadgobby on 2006-12-14
Are you using DLS or cable modem? Do you have a WIFI card?
Gobby

---

### Post by aysiu on 2006-12-14
> **azz said:**
> I dove into you other thread.
There's no need to have two threads on the same support request. I've merged the two threads.

---

### Post by bxlinux on 2006-12-14
I am using a cable modem. I will have to try running the live cd to see if my desktop can connect. The specs of my laptop are 512 ram 1.8 ghz.

---

### Post by bxlinux on 2006-12-14
I do have a wireless card but want to connect directly through my ethernet.

---

### Post by bxlinux on 2006-12-16
Here is where I am now. I installed a linux driver for my pro 100 ve ethernet card. When I enter a static ip I now get info for the interface information under ipv4 such as linkspeed and state active. I am also getting recieved bytes and packets and it does transmit. But I am still unable to ping anything. Any other ideas I can try?

---

### Post by az on 2006-12-16
Just try running the live cd on your Desktop machine and see if it can get on the net.

---

### Post by cstronach on 2006-12-16
bxlinux - I might have the same or a very similar problem.

I have a small network with three dual booting machines. The laptop that I recently tried to upgrade to Edgy lost it's ability to connect to/ping anything on my LAN, including the router - so no internet. It was connecting under Dapper and XP previously, but going back to either now doesn't work. Live CDs don't help either. Eventually, I also thought it must be a hardware problem, but I find that if I plug the laptop straight into the modem I can connect just fine. I can't figure out why the laptop can't see my router to which the other two machines are connected. I've tried everything suggested here and all the hardware swapping around that is possible and it seems that all the individual components work.

I wish you luck with finding a solution, and have also appreciated the help you've been getting. This problem is also driving me nuts.

If I can add anything to help - of course I will.

---

### Post by bxlinux on 2006-12-16
It has been a pain in the you know what but still duking it out. I did try to connect directly to the modem but to no avail.

---

### Post by az on 2006-12-16
> **bxlinux said:**
> It has been a pain in the you know what but still duking it out. I did try to connect directly to the modem but to no avail.

What do you mean?  You previously said:

[QUOTE=bxlinux]I tried that. I know the connection works because I am using the same ethernet cable that I have connected to my desktop pc and just moving it back and forth from pc to laptop. No router connected directly to the modem.[/QUOTE]

Now, are you using a router or not?

To be clear, your first step is to determine whether your desktop machine can connect to the internet while running Ubuntu.  Use the live cd.  Once we can establish how your internet provider connects you to the internet, we can proceed to get your laptop to connect.

---

### Post by bxlinux on 2006-12-17
By switching the ethernet cable that was connected directly to my PC that is able to go online and has xp on it to the laptop that doesnt connect with ubuntu. NO ROUTER. Just moving the ethernet cable back and forth.

---

### Post by az on 2006-12-17
> **bxlinux said:**
> By switching the ethernet cable that was connected directly to my PC that is able to go online and has xp on it to the laptop that doesnt connect with ubuntu. NO ROUTER. Just moving the ethernet cable back and forth.

Yeah, so?  When you boot the live cd on that *desktop machine*, can you go online from Ubuntu?

In other words:  Is the problem that your ISP doe not connect using DHCP or is it really the laptop's ethernet card?

---

### Post by bigspring on 2006-12-18
I'm having a similar problem, however it gets stranger.  Everything worked fine a day or two ago and now I can ping 127.0.0.1, and my GUI claims that I'm connected to my network however nothing else works, wired and wireless.  I'm using Dapper and the only recent changes to my laptop have been the automatic updates.

Edit: All other machines on the network continue to work perfectly.

---

### Post by bxlinux on 2006-12-18
Ok I was able to boot the live cd on my pc and it was able to connect to the internet just fine. It went in immediately connected directly to the cable modem. ](*,)

---

### Post by bxlinux on 2006-12-18
When researching dell laptops with linux I found this. 
Setup the order of the ethX interfaces : 
Installation of ifrename 
Configuration of /etc/iftab and /etc/network/interfaces for ifrename. On my setup : eth0 is not used, eth1 for the wired ethernet adapter, eth2 for the wifi one 
blacklist eth1394 in hotplug for it not to use eth0 

Can someone please explain what is going on here and what steps I would take to try this?

---

### Post by bxlinux on 2006-12-18
I also noticed something. When I booted off the live cd on my home pc I would get that the broadcast was 255.255.255.255. When I boot my laptop an enter a static IP I get the broadcast as 66.65.87.255. Why would that be?

---

### Post by bxlinux on 2006-12-18
Any ideas?

---

### Post by az on 2006-12-18
This laptop is reported to work fine in UBuntu Breezy.  [https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD505](https://wiki.ubuntu.com/LaptopTestingTeam/DellLatitudeD505)


Perhaps the ethernet card on your's is broken?  Did it work in windows?

---

### Post by trubblemaker on 2006-12-22
if the live cd works then you need to copy the settings over,  you might have a corrupt interface file.  copy the live interfaces file over your "static" one and see if that helps to work out, I don't suggest using a static ip if you can avoid it in this situation with getting internet.  It's clear from using your live cd that dhcp is working.  So keep going with that.

---

### Post by bxlinux on 2006-12-30
Yes it works on my windows I am on it now. Tried to boot the live cd using virtual pc but it will not load properly or it takes forever for what ever reason. Will partition the drive and see what happens that way.

---

### Post by bxlinux on 2006-12-30
Oh by the way both my ethernet and wireless works with windows. I also added a wireless router.

---

### Post by trubblemaker on 2006-12-31
no need for a virtual machine just pop in the disk and reboot. fyi.

---

### Post by bxlinux on 2007-01-01
Well after running the live cd I am still unable to connect to the net with ubuntu. I know there is not an issue with the hardware as I am able to connect wirelessly and wired while in xp. I will have to check to see if there is a linux driver for the intel chipset that I can install.

---

