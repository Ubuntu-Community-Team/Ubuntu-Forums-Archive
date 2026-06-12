---
title: "fwcutter or ndis prefered for broadcom wirelesss cards?"
date: 2006-10-30
forum: Networking &amp; Wireless
---

### Post by VCSkier on 2006-10-30
Basically, I'm planning on installing ubuntu edgy on my fiance's laptop, and the broadcom wireless [wiki page]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper") references both an "ndis" method and an "fwcutter" method.  I was wondering which method is preferred for broadcom wireless cards.  

Thanks.

edit:  Also, the wiki page says that it is for Dapper, is there anything different for Edgy?

---

### Post by VCSkier on 2006-11-02
I wanted to bump this, and add some more info.  The card is a Broadcom 4306, and I've come across many guides for it.  I'm basically just wondering if there is a preferred way to do it.  Thanks!

---

### Post by bakegoodz on 2006-11-15
I found the fwcutter to be flaky in my wireless, a bc4306 in a Dell Inspiron 5150. It would connect for a couple minites then lose connection. The ndis seems to be working fine.

---

### Post by trubblemaker on 2006-11-15
depends, the native driver aka bcm43xx aka firmware-cutter-method has some nice features and shows you more access points.  the downside is that it runs at 11Mb/sec or possibly 22Mb/sec if you **manually** crank it higher than that it starts to become unstable.  If you want faster speeds use ndiswrapper 54Mb/sec.  But I suggest building it from source see the last link in my sig.  Recently if you upgraded from dapper it killed ndiswrapper.  If your doing a clean install shouldn't be an issues to install from repository as long as you have the drivers.  Hope this helps.

---

### Post by Javaddiction on 2006-11-15
I've got a Dell Inspiron 8500 with a Truemobile 1300 b/g internal card. When this thing was running Dapper, ndiswrapper was pretty much the only thing that would work, and it was pretty darn reliable (though i'm not sure whether  or not it ever *really* got 54Mbs speeds. My network's running WPA and the laptop currently dual-boots into windows as well.

I upgraded to Edgy over a week ago and went to great lengths to get the wireless working again with ndiswrapper, only to find that it was considerably less stable and would leave ubuntu without a wireless connection for up to an hour at a time (though booting in to windows seemed to work just fine).

I decided to back out the ndiswrapper route and tried the fwcutter method again, having been through a couple versions since the previous attempt several months ago. This time it went pretty darn flawless. It's solid, stable, and I even was able to use the drivers from the Dell website (not the most recent version, but the next oldest in the driver archive worked).

fwcutter seems to be coming along, and so far my only complaint is the truth in the reported connection speed of 11Mbs.

---

### Post by trubblemaker on 2006-11-15
yeah alot of people suffered through the recent upgrade with ndiswrapper, so far as I can tell, the plackage in the repository breaks when it moves up to edgy, the most common solution is to unintstall ***everything*** and re-install  ***everything***

it apparently isn't a big deal if you start with edgy and then install. it's only the upgrade that hurts.

fyi, you can get a little more speed out of the driver.  I believe I could stabily get 22M/sec with the following command:
```
 sudo iwconfig eth1 rate 22M 
``` 
when I regularly used the driver, (I have it installed but blacklisted currently) I would run with it at 36 or 33Mb/sec.  The reliability was good with only the occasional loss of connectivity.  11 and 22 where solid.  I switched back to ndiswrapper, only for increased speed.  I still occasionally have reasons to use the native driver, especially when I'm somewhere I need a connection without the password.

---

### Post by VCSkier on 2006-11-20
Thank you so much for the advice.  I have it running with fwcutter, and I'm very happy with it.  Unfortunately, when I tried "sudo iwconfig eth1 rate 22M" the output was as follows.
```
Error for wireless request "Set Bit Rate" (8B20) :
    SET failed on device eth1 ; Invalid argument.
```What could I be doing wrong?

---

### Post by trubblemaker on 2006-11-20
you have to check the valid rates, they will get listed with

```
 iwlist scan 
```

usually 22M is good you could also try 36M but thats tops for bcm4318 users and I found it a little unstable at times

---

### Post by VCSkier on 2006-11-21
Actually, after a reboot, I'm back to no wireless.  i don't know what i could have done wrong...  Network Manager isn't even detecting my wireless port...  I followed the steps on the wiki exactly.

---

### Post by trubblemaker on 2006-11-21
no worries 
```
 modprobe bcm43xx 
```
and you should then be able to see it in your wireless manager. if that does work 'bcm43xx' at the bottom of '/etc/modules' and it will load the module at boot for you

---

### Post by LeAstrale on 2006-11-21
i would definately prefer using ndiswrapper because its possible to do without an internet connection. and then because after trying to do it in edgy it worked first time. but in dapper i had quite some trouble with my broadcom 4306, actually never got it to work.

the other way around i think that the fwcutter way is pretty complicated... and did never seem to work for me, and then its slow :(

---

### Post by trubblemaker on 2006-11-21
eh, it's as complicated as ndiswrapper. My signature(bcm howto_ for a script that does all the work for you.

---

### Post by VCSkier on 2006-11-21
hrm...  Still no luck.  I ran "modprobe bcm43xx" with no luck, then added "bcm43xx" to a new line on my /etc/modules, and still nothing.  Maybe I should try the ndis method; I didn't want to, because it seemed more hackish to me than the fwcutter method, which seemes more long-term and like a more permanent solution.

Thanks for being patient everyone!

---

### Post by VCSkier on 2006-11-21
It seems to me like this should be working, maybe network-manager just isn't recognizing it?  Maybe this might help with troubleshooting...```
toni@lappy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Megyesi"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

toni@lappy:~$ sudo iwlist eth1 scan
Password:
eth1      Scan completed :
          Cell 01 - Address: 00:16:B6:38:EA:27
                    ESSID:"Megyesi"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-37 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 216ms ago
          Cell 02 - Address: 00:16:B6:38:EC:19
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-82 dBm  
                    Extra: Last beacon: 60ms ago
          Cell 03 - Address: 00:D0:9E:B6:69:81
                    ESSID:"2WIRE560"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Quality=100/100  Signal level=-82 dBm  
                    Extra: Last beacon: 804ms ago
          Cell 04 - Address: 00:13:10:82:6A:76
                    ESSID:"volunteers"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-81 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP 
                        Pairwise Ciphers (1) : TKIP 
                        Authentication Suites (1) : PSK  
                    Extra: Last beacon: 32ms ago
          Cell 05 - Address: 00:0F:3D:50:38:5A
                    ESSID:"Scott"
                    Protocol:IEEE 802.11g
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-73 dBm  
                    Extra: Last beacon: 28ms ago
          Cell 06 - Address: 00:14:BF:38:25:50
                    ESSID:"kitty"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:off
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-82 dBm  
                    Extra: Last beacon: 624ms ago
          Cell 07 - Address: 00:16:B6:45:EE:2B
                    ESSID:"RivesFamily"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-84 dBm  
                    Extra: Last beacon: 1376ms ago
          Cell 08 - Address: 00:0C:41:C1:35:71
                    ESSID:"<hidden>"
                    Protocol:IEEE 802.11b
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Quality=100/100  Signal level=-87 dBm  
                    Extra: Last beacon: 8684ms ago
          Cell 09 - Address: 00:18:39:C3:F6:B6
                    ESSID:"david"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Channel:6
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=100/100  Signal level=-84 dBm  
                    Extra: Last beacon: 12096ms ago

toni@lappy:~$ 

```

---

### Post by trubblemaker on 2006-11-22
OK you are really close.

the driver is loading  and don't worry about the gui till later hate to say it but commandline is better for some things like troubleshooting.

try

```
sudo iwconfig eth1 ap any
iwconfig
```

if the Invalid went away try.

```
sudo iwconfig eth1 essid <your-essid>
sudo dhclient wlan0

```

---

### Post by VCSkier on 2006-11-22
After "sudo iwconfig eth1 ap any", "iwconfig" still returns "Access Point: Invalid"...```
toni@lappy:~$ sudo iwconfig eth1 ap any
toni@lappy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Megyesi"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.484 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

toni@lappy:~$ 
```

---

### Post by trubblemaker on 2006-11-22
just to double check you never had ndiswrapper installed did you?

---

### Post by VCSkier on 2006-11-22
nope.

---

### Post by trubblemaker on 2006-11-23
How's your dmesg after you try the 
```
 to change the ap to any? 
```

any notes about the driver?

---

### Post by VCSkier on 2006-11-23
:/
```
toni@lappy:~$ dmesg
[17179569.184000] Linux version 2.6.17-10-generic (root@vernadsky) (gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)) #2 SMP Fri Oct 13 18:45:35 UTC 2006 (Ubuntu 2.6.17-10.33-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009f800 (usable)
[17179569.184000]  BIOS-e820: 000000000009f800 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000ce000 - 00000000000d0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000dc000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 000000001dee0000 (usable)
[17179569.184000]  BIOS-e820: 000000001dee0000 - 000000001deeb000 (ACPI data)
[17179569.184000]  BIOS-e820: 000000001deeb000 - 000000001df00000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 000000001df00000 - 0000000020000000 (reserved)
[17179569.184000]  BIOS-e820: 00000000ff800000 - 00000000ffc00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffffc00 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 478MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 122592
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 118496 pages, LIFO batch:31
[17179569.184000] DMI present.
[17179569.184000] ACPI: RSDP (v000 PTLTD                                 ) @ 0x000f7780
[17179569.184000] ACPI: RSDT (v001 PTLTD  ManiaDth 0x06040000  LTP 0x00000000) @ 0x1dee69cd
[17179569.184000] ACPI: FADT (v001 INTEL  MONTARA  0x06040000 PTL  0x00000050) @ 0x1deeaec4
[17179569.184000] ACPI: BOOT (v001 PTLTD  $SBFTBL$ 0x06040000  LTP 0x00000001) @ 0x1deeafd8
[17179569.184000] ACPI: SSDT (v001 INTEL  CPU0CST  0x00000001 INTL 0x20030224) @ 0x1dee6dfd
[17179569.184000] ACPI: DSDT (v001 INTEL  MONTARAG 0x06040000 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x1008
[17179569.184000] Allocating PCI resources starting at 30000000 (gap: 20000000:df800000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda2 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (013ca000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1395.658 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179570.804000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179570.804000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179570.824000] Memory: 476264k/490368k available (1910k kernel code, 13584k reserved, 1070k data, 308k init, 0k highmem)
[17179570.824000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179570.904000] Calibrating delay using timer specific routine.. 2793.51 BogoMIPS (lpj=5587028)
[17179570.904000] Security Framework v1.0.0 initialized
[17179570.904000] SELinux:  Disabled at boot.
[17179570.904000] Mount-cache hash table entries: 512
[17179570.904000] CPU: After generic identify, caps: afe9f9ff 00100000 00000000 00000000 00000000 00000000 00000000
[17179570.904000] CPU: After vendor identify, caps: afe9f9ff 00100000 00000000 00000000 00000000 00000000 00000000
[17179570.904000] CPU: L1 I cache: 32K, L1 D cache: 32K
[17179570.904000] CPU: L2 cache: 1024K
[17179570.904000] CPU: After all inits, caps: afe9f9ff 00100000 00000000 00000040 00000000 00000000 00000000
[17179570.904000] Checking 'hlt' instruction... OK.
[17179570.920000] SMP alternatives: switching to UP code
[17179570.920000] Freeing SMP alternatives: 16k freed
[17179570.920000] checking if image is initramfs... it is
[17179571.580000] Freeing initrd memory: 5563k freed
[17179571.580000] ACPI: Core revision 20060707
[17179571.580000] ACPI: Looking for DSDT ... not found!
[17179571.584000] ACPI: setting ELCR to 0200 (from 0c28)
[17179571.600000] CPU0: Intel(R) Celeron(R) M processor         1.40GHz stepping 08
[17179571.600000] SMP motherboard not detected.
[17179571.600000] Local APIC not detected. Using dummy APIC emulation.
[17179571.600000] Brought up 1 CPUs
[17179571.600000] migration_cost=0
[17179571.600000] NET: Registered protocol family 16
[17179571.600000] EISA bus registered
[17179571.600000] ACPI: bus type pci registered
[17179571.600000] PCI: PCI BIOS revision 2.10 entry at 0xfd932, last bus=2
[17179571.600000] PCI: Using configuration type 1
[17179571.600000] Setting up standard PCI resources
[17179571.608000] ACPI: Interpreter enabled
[17179571.608000] ACPI: Using PIC for interrupt routing
[17179571.608000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179571.608000] PCI: Probing PCI hardware (bus 00)
[17179571.612000] Boot video device is 0000:00:02.0
[17179571.612000] PCI quirk: region 1000-107f claimed by ICH4 ACPI/GPIO/TCO
[17179571.612000] PCI quirk: region 1180-11bf claimed by ICH4 GPIO
[17179571.612000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:1f.1
[17179571.612000] PCI: Transparent bridge - 0000:00:1e.0
[17179571.612000] PCI: Bus #03 (-#06) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179571.612000] Please report the result to linux-kernel to fix this permanently
[17179571.612000] PCI: Bus #07 (-#0a) is hidden behind transparent bridge #02 (-#02) (try 'pci=assign-busses')
[17179571.612000] Please report the result to linux-kernel to fix this permanently
[17179571.612000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179571.616000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0.PCIB._PRT]
[17179571.616000] ACPI: PCI Interrupt Link [LNKA] (IRQs *5)
[17179571.616000] ACPI: PCI Interrupt Link [LNKB] (IRQs *10)
[17179571.616000] ACPI: PCI Interrupt Link [LNKC] (IRQs *10)
[17179571.616000] ACPI: PCI Interrupt Link [LNKD] (IRQs *11)
[17179571.616000] ACPI: PCI Interrupt Link [LNKE] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[17179571.616000] ACPI: PCI Interrupt Link [LNKF] (IRQs 1 3 4 5 6 7 11 12 14 15) *0, disabled.
[17179571.616000] ACPI: PCI Interrupt Link [LNKG] (IRQs 1 3 4 5 6 7 10 12 14 15) *0, disabled.
[17179571.616000] ACPI: PCI Interrupt Link [LNKH] (IRQs 1 *3 4 5 6 7 11 12 14 15)
[17179571.620000] ACPI: Embedded Controller [EC] (gpe 28) interrupt mode.
[17179571.620000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179571.620000] pnp: PnP ACPI init
[17179571.620000] pnp: PnP ACPI: found 8 devices
[17179571.620000] PnPBIOS: Disabled by ACPI PNP
[17179571.620000] PCI: Using ACPI for IRQ routing
[17179571.620000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179571.628000] PCI: Ignore bogus resource 6 [0:0] of 0000:00:02.0
[17179571.628000] PCI: Bus 3, cardbus bridge: 0000:02:07.0
[17179571.628000]   IO window: 00003400-000034ff
[17179571.628000]   IO window: 00003800-000038ff
[17179571.628000]   PREFETCH window: 30000000-31ffffff
[17179571.628000]   MEM window: 36000000-37ffffff
[17179571.628000] PCI: Bus 7, cardbus bridge: 0000:02:07.1
[17179571.628000]   IO window: 00003c00-00003cff
[17179571.628000]   IO window: 00001400-000014ff
[17179571.628000]   PREFETCH window: 32000000-33ffffff
[17179571.628000]   MEM window: 38000000-39ffffff
[17179571.628000] PCI: Bridge: 0000:00:1e.0
[17179571.628000]   IO window: 3000-3fff
[17179571.628000]   MEM window: e0200000-e02fffff
[17179571.628000]   PREFETCH window: 30000000-33ffffff
[17179571.628000] PCI: Setting latency timer of device 0000:00:1e.0 to 64
[17179571.628000] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 11
[17179571.628000] PCI: setting IRQ 11 as level-triggered
[17179571.628000] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179571.628000] PCI: Setting latency timer of device 0000:02:07.0 to 64
[17179571.628000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 10
[17179571.628000] PCI: setting IRQ 10 as level-triggered
[17179571.628000] ACPI: PCI Interrupt 0000:02:07.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179571.628000] PCI: Setting latency timer of device 0000:02:07.1 to 64
[17179571.628000] NET: Registered protocol family 2
[17179571.668000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179571.668000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179571.668000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179571.668000] TCP: Hash tables configured (established 16384 bind 8192)
[17179571.668000] TCP reno registered
[17179571.668000] Simple Boot Flag at 0x36 set to 0x1
[17179571.668000] audit: initializing netlink socket (disabled)
[17179571.668000] audit(1164279221.668:1): initialized
[17179571.668000] VFS: Disk quotas dquot_6.5.1
[17179571.668000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179571.668000] Initializing Cryptographic API
[17179571.668000] io scheduler noop registered
[17179571.668000] io scheduler anticipatory registered
[17179571.668000] io scheduler deadline registered
[17179571.668000] io scheduler cfq registered (default)
[17179571.668000] isapnp: Scanning for PnP cards...
[17179572.020000] isapnp: No Plug & Play device found
[17179572.048000] Real Time Clock Driver v1.12ac
[17179572.048000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179572.048000] ACPI: PCI Interrupt 0000:00:1f.6[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179572.048000] ACPI: PCI interrupt for device 0000:00:1f.6 disabled
[17179572.048000] mice: PS/2 mouse device common for all mice
[17179572.052000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179572.052000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179572.052000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179572.052000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[17179572.056000] serio: i8042 AUX port at 0x60,0x64 irq 12
[17179572.056000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179572.060000] EISA: Probing bus 0 at eisa.0
[17179572.060000] Cannot allocate resource for EISA slot 1
[17179572.060000] Cannot allocate resource for EISA slot 2
[17179572.060000] Cannot allocate resource for EISA slot 3
[17179572.060000] EISA: Detected 0 cards.
[17179572.060000] TCP bic registered
[17179572.060000] NET: Registered protocol family 1
[17179572.060000] NET: Registered protocol family 8
[17179572.060000] NET: Registered protocol family 20
[17179572.060000] Using IPI No-Shortcut mode
[17179572.060000] ACPI: (supports S0 S3 S4 S5)
[17179572.060000] Freeing unused kernel memory: 308k freed
[17179572.288000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179573.192000] Capability LSM initialized
[17179573.228000] ACPI: CPU0 (power states: C1[C1] C2[C2] C3[C3])
[17179573.228000] ACPI: Processor [CPU0] (supports 8 throttling states)
[17179573.228000] ACPI: Thermal Zone [THRM] (38 C)
[17179573.560000] ICH4: IDE controller at PCI slot 0000:00:1f.1
[17179573.560000] PCI: Enabling device 0000:00:1f.1 (0005 -> 0007)
[17179573.560000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179573.560000] ACPI: PCI Interrupt 0000:00:1f.1[A] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179573.560000] ICH4: chipset revision 3
[17179573.560000] ICH4: not 100% native mode: will probe irqs later
[17179573.560000]     ide0: BM-DMA at 0x1810-0x1817, BIOS settings: hda:DMA, hdb:pio
[17179573.560000]     ide1: BM-DMA at 0x1818-0x181f, BIOS settings: hdc:DMA, hdd:pio
[17179573.560000] Probing IDE interface ide0...
[17179573.848000] hda: FUJITSU MHT2040AT, ATA DISK drive
[17179574.520000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179574.592000] Probing IDE interface ide1...
[17179575.328000] hdc: HL-DT-STCD-RW/DVD DRIVE GCC-4243N, ATAPI CD/DVD-ROM drive
[17179575.664000] ide1 at 0x170-0x177,0x376 on irq 15
[17179575.672000] hda: max request size: 128KiB
[17179575.680000] hda: 78140160 sectors (40007 MB) w/2048KiB Cache, CHS=65535/16/63, UDMA(100)
[17179575.680000] hda: cache flushes supported
[17179575.680000]  hda: hda1 hda2 hda3
[17179575.760000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 2048kB Cache, UDMA(33)
[17179575.760000] Uniform CD-ROM driver Revision: 3.20
[17179576.148000] usbcore: registered new driver usbfs
[17179576.148000] usbcore: registered new driver hub
[17179576.148000] USB Universal Host Controller Interface driver v3.0
[17179576.152000] ACPI: PCI Interrupt Link [LNKA] enabled at IRQ 5
[17179576.152000] PCI: setting IRQ 5 as level-triggered
[17179576.152000] ACPI: PCI Interrupt 0000:00:1d.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[17179576.152000] PCI: Setting latency timer of device 0000:00:1d.0 to 64
[17179576.152000] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[17179576.152000] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 1
[17179576.152000] uhci_hcd 0000:00:1d.0: irq 5, io base 0x00001820
[17179576.152000] usb usb1: configuration #1 chosen from 1 choice
[17179576.152000] hub 1-0:1.0: USB hub found
[17179576.152000] hub 1-0:1.0: 2 ports detected
[17179576.224000] ieee1394: Initialized config rom entry `ip1394'
[17179576.256000] ACPI: PCI Interrupt 0000:00:1d.1[B] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179576.256000] PCI: Setting latency timer of device 0000:00:1d.1 to 64
[17179576.256000] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[17179576.256000] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 2
[17179576.256000] uhci_hcd 0000:00:1d.1: irq 11, io base 0x00001840
[17179576.256000] usb usb2: configuration #1 chosen from 1 choice
[17179576.256000] hub 2-0:1.0: USB hub found
[17179576.256000] hub 2-0:1.0: 2 ports detected
[17179576.360000] ACPI: PCI Interrupt 0000:00:1d.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179576.360000] PCI: Setting latency timer of device 0000:00:1d.2 to 64
[17179576.360000] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[17179576.360000] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 3
[17179576.360000] uhci_hcd 0000:00:1d.2: irq 10, io base 0x00001860
[17179576.360000] usb usb3: configuration #1 chosen from 1 choice
[17179576.360000] hub 3-0:1.0: USB hub found
[17179576.360000] hub 3-0:1.0: 2 ports detected
[17179576.464000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 3
[17179576.464000] PCI: setting IRQ 3 as level-triggered
[17179576.464000] ACPI: PCI Interrupt 0000:00:1d.7[D] -> Link [LNKH] -> GSI 3 (level, low) -> IRQ 3
[17179576.464000] PCI: Setting latency timer of device 0000:00:1d.7 to 64
[17179576.464000] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[17179576.464000] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 4
[17179576.464000] ehci_hcd 0000:00:1d.7: debug port 1
[17179576.464000] PCI: cache line size of 32 is not supported by device 0000:00:1d.7
[17179576.464000] ehci_hcd 0000:00:1d.7: irq 3, io mem 0xe0100000
[17179576.468000] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179576.468000] usb usb4: configuration #1 chosen from 1 choice
[17179576.468000] hub 4-0:1.0: USB hub found
[17179576.468000] hub 4-0:1.0: 6 ports detected
[17179576.572000] ACPI: PCI Interrupt 0000:02:07.2[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179576.632000] ohci1394: fw-host0: OHCI-1394 1.0 (PCI): IRQ=[10]  MMIO=[e0202000-e02027ff]  Max Packet=[2048]  IR/IT contexts=[4/4]
[17179576.680000] Attempting manual resume
[17179576.692000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179576.692000] EXT3-fs: write access will be enabled during recovery.
[17179577.912000] ieee1394: Host added: ID:BUS[0-00:1023]  GUID[00032521350372ec]
[17179579.412000] kjournald starting.  Commit interval 5 seconds
[17179579.412000] EXT3-fs: recovery complete.
[17179579.412000] EXT3-fs: mounted filesystem with ordered data mode.
[17179593.612000] Linux agpgart interface v0.101 (c) Dave Jones
[17179593.616000] agpgart: Detected an Intel 855 Chipset.
[17179593.616000] agpgart: Detected 32636K stolen memory.
[17179593.624000] agpgart: AGP aperture is 128M @ 0xe8000000
[17179594.900000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179595.148000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179595.160000] hw_random: RNG not detected
[17179595.368000] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKD] -> GSI 11 (level, low) -> IRQ 11
[17179595.368000] Yenta: CardBus bridge found at 0000:02:07.0 [161f:203a]
[17179595.448000] 8139too Fast Ethernet driver 0.9.27
[17179595.484000] ieee80211_crypt: registered algorithm 'NULL'
[17179595.488000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179595.488000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179595.592000] Yenta: ISA IRQ mask 0x0090, PCI irq 11
[17179595.592000] Socket status: 30000006
[17179595.592000] Yenta: Raising subordinate bus# of parent bus (#02) from #02 to #06
[17179595.592000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179595.592000] cs: IO port probe 0x3000-0x3fff: clean.
[17179595.592000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179595.592000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179595.592000] bcm43xx driver
[17179595.592000] ACPI: PCI Interrupt 0000:00:1f.5[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179595.592000] PCI: Setting latency timer of device 0000:00:1f.5 to 64
[17179595.592000] ACPI: PCI Interrupt 0000:02:07.1[B] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179595.592000] Yenta: CardBus bridge found at 0000:02:07.1 [161f:203a]
[17179595.720000] Yenta: ISA IRQ mask 0x0090, PCI irq 10
[17179595.720000] Socket status: 30000006
[17179595.720000] Yenta: Raising subordinate bus# of parent bus (#02) from #06 to #0a
[17179595.720000] pcmcia: parent PCI bridge I/O window: 0x3000 - 0x3fff
[17179595.720000] cs: IO port probe 0x3000-0x3fff: clean.
[17179595.720000] pcmcia: parent PCI bridge Memory window: 0xe0200000 - 0xe02fffff
[17179595.720000] pcmcia: parent PCI bridge Memory window: 0x30000000 - 0x33ffffff
[17179595.816000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x23aeb3, caps: 0xa04713/0x10008
[17179595.856000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179595.872000] ts: Compaq touchscreen protocol output
[17179596.252000] cs: IO port probe 0x100-0x3af: clean.
[17179596.252000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179596.252000] cs: IO port probe 0x820-0x8ff: clean.
[17179596.256000] cs: IO port probe 0xc00-0xcf7: clean.
[17179596.256000] cs: IO port probe 0xa00-0xaff: clean.
[17179596.268000] cs: IO port probe 0x100-0x3af: clean.
[17179596.268000] cs: IO port probe 0x3e0-0x4ff: excluding 0x4d0-0x4d7
[17179596.268000] cs: IO port probe 0x820-0x8ff: clean.
[17179596.272000] cs: IO port probe 0xc00-0xcf7: clean.
[17179596.272000] cs: IO port probe 0xa00-0xaff: clean.
[17179596.412000] intel8x0_measure_ac97_clock: measured 55406 usecs
[17179596.412000] intel8x0: clocking to 48000
[17179596.412000] ACPI: PCI Interrupt 0000:02:08.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179596.412000] eth0: RealTek RTL8139 at 0xde992800, 00:03:25:29:06:ee, IRQ 10
[17179596.412000] eth0:  Identified 8139 chip type 'RTL-8101'
[17179596.420000] ACPI: PCI Interrupt 0000:02:09.0[A] -> Link [LNKB] -> GSI 10 (level, low) -> IRQ 10
[17179596.424000] 8139cp: 10/100 PCI Ethernet driver v1.2 (Mar 22, 2004)
[17179596.800000] eth0: link down
[17179596.868000] lp: driver loaded but no devices found
[17179596.900000] SCSI subsystem initialized
[17179596.900000] ieee1394: sbp2: Driver forced to serialize I/O (serialize_io=1)
[17179596.900000] ieee1394: sbp2: Try serialize_io=0 for better performance
[17179596.952000] Adding 522104k swap on /dev/disk/by-uuid/400beeed-303c-4e2a-b815-82a458a2c11c.  Priority:-1 extents:1 across:522104k
[17179597.076000] EXT3 FS on hda2, internal journal
[17179597.156000] SoftMAC: Open Authentication completed with 00:16:b6:38:ea:27
[17179597.300000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179597.380000] NTFS volume version 3.1.
[17179597.788000] NET: Registered protocol family 17
[17179601.804000] ACPI: AC Adapter [AC] (on-line)
[17179601.852000] ACPI: Battery Slot [BAT0] (battery present)
[17179601.876000] ACPI: Power Button (FF) [PWRF]
[17179601.876000] ACPI: Lid Switch [LID0]
[17179601.876000] ACPI: Sleep Button (CM) [SLPB]
[17179601.876000] ACPI: Power Button (CM) [PWRB]
[17179602.032000] ibm_acpi: ec object not found
[17179602.068000] pcc_acpi: loading...
[17179602.212000] ACPI: Video Device [GFX0] (multi-head: yes  rom: yes  post: no)
[17179604.560000] [drm] Initialized drm 1.0.1 20051102
[17179604.564000] ACPI: PCI Interrupt 0000:00:02.0[A] -> Link [LNKA] -> GSI 5 (level, low) -> IRQ 5
[17179604.568000] [drm] Initialized i915 1.5.0 20060119 on minor 0
[17179604.568000] [drm] Initialized i915 1.5.0 20060119 on minor 1
[17179605.776000] apm: BIOS not found.
[17179611.796000] NET: Registered protocol family 10
[17179611.796000] lo: Disabled Privacy Extensions
[17179611.796000] ADDRCONF(NETDEV_UP): eth0: link is not ready
[17179611.796000] ADDRCONF(NETDEV_UP): eth1: link is not ready
[17179611.796000] IPv6 over IPv4 tunneling driver
[17179612.524000] Bluetooth: Core ver 2.8
[17179612.524000] NET: Registered protocol family 31
[17179612.524000] Bluetooth: HCI device and connection manager initialized
[17179612.524000] Bluetooth: HCI socket layer initialized
[17179612.556000] Bluetooth: L2CAP ver 2.8
[17179612.556000] Bluetooth: L2CAP socket layer initialized
[17179612.608000] Bluetooth: RFCOMM socket layer initialized
[17179612.608000] Bluetooth: RFCOMM TTY layer initialized
[17179612.608000] Bluetooth: RFCOMM ver 1.7
[17179670.992000] SoftMAC: Authentication response received from 00:0c:f1:44:9e:56 but no queue item exists.
[17179670.996000] SoftMAC: Authentication response received from 00:16:b6:38:ea:27 but no queue item exists.
[17179759.200000] SoftMAC: Authentication response received from 00:0f:3d:50:38:5a but no queue item exists.
[17179759.508000] SoftMAC: Authentication response received from 00:0f:3d:50:38:5a but no queue item exists.
[17179766.060000] SoftMAC: Authentication response received from 00:0f:3d:50:38:5a but no queue item exists.
[17179766.060000] SoftMAC: Authentication response received from 00:0f:3d:50:38:5a but no queue item exists.
[17179766.804000] SoftMAC: Authentication response received from 00:0f:3d:50:38:5a but no queue item exists.
[17179806.224000] SoftMAC: Authentication response received from 00:0f:3d:50:38:5a but no queue item exists.
[17179812.712000] SoftMAC: Authentication response received from 00:0c:f1:44:9e:56 but no queue item exists.
[17179812.716000] SoftMAC: Authentication response received from 00:16:b6:38:ea:27 but no queue item exists.
[17179813.348000] SoftMAC: Authentication response received from 00:0f:3d:50:38:5a but no queue item exists.
[17179813.780000] SoftMAC: Authentication response received from 00:0f:3d:50:38:5a but no queue item exists.
[17179817.236000] SoftMAC: Authentication response received from 00:0f:3d:50:38:5a but no queue item exists.
[17179850.220000] SoftMAC: Authentication response received from 00:16:b6:38:ec:19 but no queue item exists.
[17179850.220000] SoftMAC: Authentication response received from 00:16:b6:38:ec:19 but no queue item exists.
[17179850.224000] SoftMAC: Authentication response received from 00:16:b6:38:ec:19 but no queue item exists.
[17179850.228000] SoftMAC: Authentication response received from 00:16:b6:38:ec:19 but no queue item exists.
[17179850.240000] SoftMAC: Authentication response received from 00:16:b6:38:ec:19 but no queue item exists.
[17180043.632000] SoftMAC: Authentication response received from 00:0c:f1:44:9e:56 but no queue item exists.
[17180043.636000] SoftMAC: Authentication response received from 00:16:b6:38:ea:27 but no queue item exists.
[17180147.632000] SoftMAC: Authentication response received from 00:90:4b:db:22:4d but no queue item exists.
[17180147.636000] SoftMAC: Authentication response received from 00:16:b6:38:ea:27 but no queue item exists.
toni@lappy:~$ 

```It's there, about 75% down...  It's on a line by itself, with no other details.  "[17179595.592000] bcm43xx driver"

---

### Post by trubblemaker on 2006-11-23
here use this [script I wrote a long time ago]("http://ubuntuforums.org/showpost.php?p=899926&postcount=24") see if it get's you up and running:

just use the script don't do the rest of the post, if the script works then think about doing the entire post

---

### Post by VCSkier on 2006-11-23
still no luck... here's what the script put out.```
Bringing network down
Bringing network back up
Changing to any
Changing to rate to 11M
acquiring IP
There is already a pid file /var/run/dhclient.pid with pid 6022
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.4
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth1/00:90:4b:fd:ae:f4
Sending on   LPF/eth1/00:90:4b:fd:ae:f4
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 12
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 16
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15

```

---

### Post by trubblemaker on 2006-11-23
and does you ap still say invalid in "iwconfig" ?  that's the thing we need to go away. try :

```
 sudo iwconfig eth1 essid any 
sudo iwconfig eth1 ap any 
```
post iwconfig
```
 sudo iwconfig eth1 essid your-essid 
```
post iwconfig

you have to do this just to get it initialized then it starts working but I can't remeber the specific steps, but your reall close

---

### Post by VCSkier on 2006-11-24
my essid is wpa protected, if that might be effecting anything...

---

### Post by VCSkier on 2006-11-24
here's what i have...```
toni@lappy:~$ sudo iwconfig eth1 essid any
toni@lappy:~$ sudo iwconfig eth1 ap any
toni@lappy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"linksys"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

toni@lappy:~$ sudo iwconfig eth1 essid Megyesi
toni@lappy:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      IEEE 802.11b/g  ESSID:"Megyesi"  Nickname:"Broadcom 4306"
          Mode:Managed  Frequency=2.437 GHz  Access Point: Invalid   
          Bit Rate=1 Mb/s   Tx-Power=19 dBm   
          RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.

toni@lappy:~$ 

```

---

### Post by trubblemaker on 2006-11-24
Serouisly? ok, lets go with K.I.S.S.  Yes, that totally affects it.  Please do this unencrypted first then add in Security.  Go unencrypted and repeat previous posts.

---

### Post by VCSkier on 2006-11-25
I'm so sorry i didn't mention that earlier...  I don't really have access to a consistent non-encrypted connection here; the signal is too weak.  I guess I'll try again when I get back to school from Thanksgiving break.  Thanks and sorry again.

---

### Post by VCSkier on 2006-11-25
Actually, I did just get a valid access point from one of the weak signals floating around (apparently i stole it from the neighbors :).  It's a series of six two-character sets, separated by colons.  Does that mean it works, or do I still need to do some more configuration?

---

### Post by trubblemaker on 2006-11-25
Awesome ! that means it works! now you need to setup the enxrypted part of it.  That's not my speciallty search this forum for help and i think that the howto in my signature might have some suggestions to het you started.

---

### Post by spd106 on 2006-11-25
Whoa, seven+ wireless networks all on the same channel (6), that's probably not a good idea. If I were you I'd change to a different channel ASAP. If channel 11 is available, put it on that one.

With all those networks around it's also very important to get encryption on quickly as well. WEP will do, it's better than nothing and think about using network-manager too.

---

