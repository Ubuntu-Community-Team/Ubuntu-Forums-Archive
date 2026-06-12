---
title: "WoL not working"
date: 2020-04-26
forum: Networking &amp; Wireless
---

### Post by bak2bak on 2020-04-26
Hi guys,

First post, long time reader of the forum to help solving my problems, needing your support this time.

I am successfully powering on my home made Ubuntu Server 18.04 NAS1 from my PC1 Linux Mint 19.2 Build (Ubuntu 18.04 based).
Both have their IP addresses reserved in my router according to their MAC Addresses and are on the same subnet.
When NAS1 has been shut down (with sudo shutdown - h now), I can turn it on from PC1 by sending wake-on-lan (WoL) magic packets to it either with the powerwake or wakeonlan command.

I showed this to a friend and it ended up with him wanting the same solution, so I made him one similar Ubuntu Server 18.04 build, let's call it NAS2.
As you may guess, NAS2 is not responding to WoL, no way to power it on remotely. :(

NAS1 and NAS2 components are very similar, and both are based on the very same motherboard, an Asrock J3455-ITX.
One difference though is that NAS1 has got an 1.40 UEFI version while NAS2 is on a 1.60 UEFI version.
Both have the following UEFI setup that, to my understanding, should enable WoL:
```

Onboard LAN            :  Enabled
Deep S5                :  Disabled
PCIE Devices Power On  :  Enabled
Boot From Onboard LAN  :  Enabled
Secure Boot            :  Disabled
```

For NAS2, here is what [COLOR=#0000ff][FONT=courier new]$ sudo dmidecode | less[/FONT][/COLOR] shows me for the network card:
```
# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 3.0.0 present.
Table at 0x6DC50000.

Handle 0x0009, DMI type 9, 17 bytes
System Slot Information
        Designation: mPCIE
        Type: x1 PCI Express
        Current Usage: Available
        Length: Short
        ID: 33
        Characteristics:
                3.3 V is provided
                Opening is shared
**                PME signal is supported***
        Bus Address: 0000:ff:1f.7

```
[I]***P**ower **M**anagement **E**vents, which include WOL

[/I]For your information, other NAS2 parts are:
- Kingston Value RAM 8GB, DDR3L-1600, SODIMM 204 (KVR16LS11/8 which is on the [memory compatible list of the Asrock J3455-ITX]("https://asrock.com/mb/Intel/J3455-ITX/#Memory"))
- Micron SSD - 256GB
- WD 4TB Red HDD (not connected yet)
- Seagate 4TB Ironwolf HDD (not connected yet)
- Silverstone ST30SF 300W SFX PSU

This is what [COLOR=#0000ff][FONT=courier new]$ sudo inxi -Fxz[/FONT][/COLOR] tells for NAS2:
```
System:    Host: NAS2 Kernel: 4.15.0-96-generic x86_64 bits: 64 gcc: 7.5.0 Desktop: MATE
           Distro: Ubuntu 18.04.4 LTS
Machine:   Device: desktop Mobo: ASRock model: J3455-ITX serial: <filter> UEFI: American Megatrends v: P1.60 date: 01/16/2018
CPU:       Quad core Intel Celeron J3455 (-MCP-) arch: N/A cache: 1024 KB
           flags: (lm nx sse sse2 sse3 sse4_1 sse4_2 ssse3 vmx) bmips: 11980
           clock speeds: max: 2300 MHz 1: 1697 MHz 2: 1135 MHz 3: 1206 MHz 4: 1637 MHz
Graphics:  Card: Intel Device 5a85 bus-ID: 00:02.0
           Display Server: X.Org 1.19.6 driver: i915 Resolution: 2560x1080@60.00hz
           OpenGL: renderer: llvmpipe (LLVM 9.0, 128 bits) version: 3.3 Mesa 19.2.8 Direct Render: Yes
Network:   Card: Realtek RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
           driver: r8169 v: 2.3LK-NAPI port: e000 bus-ID: 01:00.0
           IF: enp1s0 state: up speed: 1000 Mbps duplex: full mac: <filter>
Drives:    HDD Total Size: 256.1GB (1.8% used)
           ID-1: /dev/sda model: MTFDDAK256MAM size: 256.1GB temp: 0C
Partition: ID-1: / size: 234G used: 4.4G (2%) fs: ext4 dev: /dev/sda2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 31.0C mobo: N/A
           Fan Speeds (in rpm): cpu: N/A
For your information. nfo:      Processes: 142 Uptime: 6 min Memory: 168.8/7637.8MB Init: Other NAS2 parts aresystemd runlevel: 5 Gcc sys: N/A
           Client: Shell (sudo) inxi: 2.3.56

```

NAS2 IP Address has also been reserved according to its MAC Address in my router.
[COLOR=#0000ff]$[/COLOR] [COLOR=#0000ff][FONT=courier new]ifconfig -a[/FONT][/COLOR] shows:
```
enp1s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.1.39  netmask 255.255.255.0  broadcast 192.168.1.255
        inet6 fe80::7285:c2ff:fe7f:4412  prefixlen 64  scopeid 0x20<link>
        ether a1:b2:c3:d4:44:12  txqueuelen 1000  (Ethernet)
        RX packets 37320  bytes 50510413 (50.5 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 20378  bytes 1703704 (1.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0


lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 679  bytes 238416 (238.4 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 679  bytes 238416 (238.4 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

On the NAS2 itself, the enp1s0 network controller is set for DHCP, [COLOR=#0000ff][FONT=courier new]$ nano /etc/netplan/01-netcfg.yaml[/FONT][/COLOR]:
```
# This file describes the network interfaces available on your system
# For more information, see netplan(5).
network:
  version: 2
  renderer: networkd
  ethernets:
    enp1s0:
      dhcp4: yes

```


That's it for the system I think, if you need some more info please let me know.


With NAS2 turned on, I am able to check for incoming packets using ngrep or netcat, when sending Magic Packets from PC1 with [FONT=courier new][COLOR=#0000ff]$ wakeonlan a1:b2:c3:d4:44:12[/COLOR][/FONT].
For instance with netcat [FONT=courier new][COLOR=#0000ff]$ sudo nc -ul -p 9[/COLOR][/FONT], I get:
```
*Some binary code *

```

Or with ngrep [FONT=courier new][COLOR=#0000ff]$ sudo ngrep '\xff{6}(.{6})\1{15}' -x port 9[/COLOR][/FONT], I get:
```
interface: enp1s0 (192.168.1.0/255.255.255.0)
filter: ( port 9 ) and ((ip || ip6) || (vlan && (ip || ip6)))
match: \xff{6}(.{6})\1{15}
#
U 192.168.1.31:40566 -> 255.255.255.255:9 #1
  ff ff ff ff ff ff a1 b2    c3 d4 44 12 a1 b2 c3 d4    ......p...D.p...
  44 12 a1 b2 c3 d4 44 12    a1 b2 c3 d4 44 12 a1 b2    D.p...D.p...D.p.
  c3 d4 44 12 a1 b2 c3 d4    44 12 a1 b2 c3 d4 44 12    ..D.p...D.p...D.
  a1 b2 c3 d4 44 12 a1 b2    c3 d4 44 12 a1 b2 c3 d4    p...D.p...D.p...
  44 12 a1 b2 c3 d4 44 12    a1 b2 c3 d4 44 12 a1 b2    D.p...D.p...D.p.
  c3 d4 44 12 a1 b2 c3 d4    44 12 a1 b2 c3 d4 44 12    ..D.p...D.p...D.
  a1 b2 c3 d4 44 12                                    p...D.

```

Strangely, I get nothing when trying to send packets with [FONT=courier new][COLOR=#0000ff]$ powerwake a1b2c3d44412[/COLOR][/FONT].
However I experience exactly the same with my working NAS1, even though a wakeonlan or powerwake command is able to power it on.

And I don't know if that indicates something, but with [FONT=courier new][COLOR=#0000ff]$ sudo etherwake a1:b2:c3:d4:44:12 -i enp1s0[/COLOR][/FONT], I see this (on both NAS though):
```
SIOCGIFHWADDR on enp1s0 failed: No such device

```


So finally, as said above after shutting it down with [FONT=courier new][COLOR=#0000ff]$ sudo shutdown -h now[/COLOR][/FONT], impossible to turn it back on either with [FONT=courier new][COLOR=#0000ff]$ wakeonlan a1:b2:c3:d4:44:12[/COLOR][/FONT] or with [FONT=courier new][COLOR=#0000ff]$ powerwake a1b2c3d44412[/COLOR][/FONT].
And this even though the results of the above tests seem to point to an available WoL functionnality.

Am I missing something? 
Are there other tools that could help me point out where the problem is?

Lastly, I tried to change the OS to Ubuntu 18.04 Desktop, Linux Mint 19.3, and I even tried to clone the NAS1 OS SSD to check it on NAS2. But all attempts to power on the build with WoL failed.
Which makes me think, especially because of the cloned SSD, that the problem comes from the UEFI of NAS2, or an hardware problem on this motherboard.

I am very interested in seeing what you think about all this!
Thanks for reading, I was rather long!

---

### Post by CatKiller on 2020-04-26
It's quite a while since I've needed to set it up, and I can't remember all the details since it's something you tend to just set up and then never touch it again, but I can remember that you can use ```
sudo ethtool <nic>
``` where <nic> would be enp1s0 in this case, to see what the system thinks the wake-on-LAN status of the card is. You're looking for a **g** and, if it isn't there, then there's a command that will put it there. The other thing is that - for wake-on-LAN to work - you want the system to power down but leave the network card powered (so it can listen for the magic packet). Some systems just power down everything. I remember that for one machine (recently deceased) I had to find the script that powered down the machine and tell it to turn the network card back on just before shutdown.

I hope these vague recollections will point you somewhere towards a solution.

---

### Post by bak2bak on 2020-04-27
Thanx a lot CatKiller!

> **CatKiller said:**
> 
you can use ```
sudo ethtool <nic>
``` where <nic> would be enp1s0 in this case, to see what the system thinks the wake-on-LAN status of the card is. You're looking for a **g** and, if it isn't there, then there's a command that will put it there


My bad, ethtool results were actually supposed to be part of my first post...
This is what I get with [FONT=&quot][COLOR=#0000FF]$ sudo ethtool enp1s0[/COLOR][/FONT]:
```
Settings for enp1s0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Half 1000baseT/Full 
	Supported pause frame use: No
	Supports auto-negotiation: Yes
	Supported FEC modes: Not reported
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	                        1000baseT/Full 
	Advertised pause frame use: Symmetric Receive-only
	Advertised auto-negotiation: Yes
	Advertised FEC modes: Not reported
	Link partner advertised link modes:  10baseT/Half 10baseT/Full 
	                                     100baseT/Half 100baseT/Full 
	                                     1000baseT/Half 1000baseT/Full 
	Link partner advertised pause frame use: Symmetric Receive-only
	Link partner advertised auto-negotiation: Yes
	Link partner advertised FEC modes: Not reported
	Speed: 1000Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 0
	Transceiver: internal
	Auto-negotiation: on
	**Supports Wake-on: pumbg**
**	Wake-on: g**
	Current message level: 0x00000033 (51)
			       drv probe ifdown ifup
	Link detected: yes

```

So the wanted 'Wake-on: g' is here, even after rebooting the system, which is good I guess.


> **CatKiller said:**
> 
The other thing is that - for wake-on-LAN to work - you want the system to power down but leave the network card powered (so it can listen for the magic packet). Some systems just power down everything. I remember that for one machine (recently deceased) I had to find the script that powered down the machine and tell it to turn the network card back on just before shutdown.

Very interesting. I already read here and there that the network card had to stay powered, but thought this was ok with the J3455-ITX motherboard since NAS1 was responding to WoL properly. Actually even with no sign of network activity on the lights of its RJ45 port! :-k

Maybe the UEFI 1.60 differs in that with the UEFI 1.40, so I will look for such a script and try to be sure the network card always stays powered.

Do you think a powered network card will in any case have its activity LEDs on or not always?

---

### Post by CatKiller on 2020-04-27
> **bak2bak said:**
> Do you think a powered network card will in any case have its activity LEDs on or not always?

I don't think they do.

As I mentioned, the computer that I recall having that particular issue with died, and I'd set it to turn on again anyway, so I can't check but as I (hazily) recall there was an internal LED that remained lit when it was powered and turned off when it wasn't, which is what helped me track down the issue.

---

### Post by bak2bak on 2020-05-07
> **CatKiller said:**
> I don't think they do.

Thanx, that seems on par with NAS1 responding to magic packets while there is no LED turned on.

> **CatKiller said:**
> 
As I mentioned, the computer that I recall having that particular issue with died, and I'd set it to turn on again anyway, so I can't check but as I (hazily) recall there was an internal LED that remained lit when it was powered and turned off when it wasn't, which is what helped me track down the issue.
Unfortunately there is no internal LED at all on that ITX mobo.


I followed a promising track with [FONT=courier new][COLOR=#0000ff]$ lspci[/COLOR][/FONT]:
```
00:00.0 Host bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Host Bridge (rev 0b)
00:02.0 VGA compatible controller: Intel Corporation Device 5a85 (rev 0b)
00:0f.0 Communication controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Trusted Execution Engine (rev 0b)
00:12.0 SATA controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SATA AHCI Controller (rev 0b)
00:13.0 PCI bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A #1 (rev fb)
00:13.1 PCI bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A #2 (rev fb)
00:13.2 PCI bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A #3 (rev fb)
00:13.3 PCI bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series PCI Express Port A #4 (rev fb)
00:15.0 USB controller: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series USB xHCI (rev 0b)
00:1f.0 ISA bridge: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series Low Pin Count Interface (rev 0b)
00:1f.1 SMBus: Intel Corporation Celeron N3350/Pentium N4200/Atom E3900 Series SMBus Controller (rev 0b)
**01:00.0 **Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 11)
03:00.0 SATA controller: ASMedia Technology Inc. ASM1062 Serial ATA Controller (rev 02)

```

and checking my wakeup capable devices with [COLOR=#0000ff][FONT=courier new]$ acpitool -w[/FONT][/COLOR]:
```
Device    S-state      Status   Sysfs node
  ---------------------------------------
  1. SIO1      S3    *disabled  pnp:00:00
  2. PS2K      S4    *disabled
  3. PS2M      S4    *disabled
  4. UAR1      S4    *disabled  pnp:00:01
  5. UR11      S4    *disabled
  6. UR12      S4    *disabled
  7. UR13      S4    *disabled
  8. UR14      S4    *disabled
  9. HDAS      S3    *disabled
  10. XHC      S4    *enabled   pci:0000:00:15.0
  11. XDCI      S4    *disabled
  12. BRCM      S0    *disabled
  13. RP01      S4    *disabled
  14. PXSX      S4    *disabled
  15. RP02      S4    *disabled
  16. PXSX      S4    *disabled
  17. RP03      S4    *enabled   pci:0000:00:13.0
  **18**. PXSX      S4    ***disabled**  **pci:0000:01:00.0**
  19. RP04      S4    *enabled   pci:0000:00:13.1
  20. PXSX      S4    *disabled
  21. RP05      S4    *enabled   pci:0000:00:13.2
  22. PXSX      S4    *disabled  pci:0000:03:00.0
  23. RP06      S4    *enabled   pci:0000:00:13.3
  24. PXSX      S4    *disabled
  25. PWRB      S4    *enabled   platform:PNP0C0C:00

```

Which seems to show that my Ethernet controller has got its wakeup status as disabled.

So I tried to enable it with [FONT=courier new][COLOR=#0000ff]$ acpitool -W 18[/COLOR][/FONT]:
```
Changed status for wakeup device #18 (PXSX)



```

But even though the above message, [COLOR=#0000FF][FONT=&amp]$ acpitool -w[/FONT][/COLOR] still shows:
```
18. PXSX      S4    *disabled  pci:0000:01:00.0
```

And anyway, looking at NAS1 I see that pci:0000:01:00.0 is also disabled without preventing WoL to work properly... :-s

Still searching...

---

### Post by kurt18947 on 2020-05-07
You've probably checked this and I didn't see it but usually there's a WOL setting in motherboard UEFI. Maybe that keeps the network card powered or not. Just something easy to check if you haven't.

---

### Post by bak2bak on 2020-05-08
Hi kurt18947, thank you for your input!

You can see my UEFI settings related to WoL on the first post, which are:
```
Onboard LAN            :  Enabled
Deep S5                :  Disabled
PCIE Devices Power On  :  Enabled
Boot From Onboard LAN  :  Enabled
Secure Boot            :  Disabled
```
The 'Boot from Onboard LAN' should imply that the network card is kept powered on.
Is it what you were referring to?

---

### Post by Tadaen_Sylvermane on 2020-05-09
When I was first setting up WoL on my lan a few of my machines were about the dumbest thing ever. They had an option to enable wake on lan in the bios. But that alone didn't do it. I had to enable a few other settings buried in other parts of the bios. EFI / bios, either way go through all of it. It may be similar. Drove me nuts. Now out of habit I check every single part of the bios / efi and I've usually had it work first time after all that each time.

---

