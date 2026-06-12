---
title: "Wireless card partially recognized"
date: 2006-09-12
forum: Networking &amp; Wireless
---

### Post by sheine on 2006-09-12
Device Manager sees my wireless card. But when I go to "Network settings" there is no recognition of my wireless card and therefore I cannot configure it. How do I proceed? With another OS, which has harddrake, I can configure it through harddrake.

---

### Post by spd106 on 2006-09-12
What does hardware manager report the card as?
Maybe also post the output from **lspci** and **iwconfig**.

---

### Post by sheine on 2006-09-12
Device Manager; Under USB 1.0 Controller, subheading OHCI Host Controller.
IEEE 802.11b Prism3 USB
USB Vendor Specific Interface: Vendor AirVast
Network Interface:
    Device type net.80203
    Capabilities  net.net.80203

lspci
Various devices including modem and ethernet correctly identified as Realtek.

iwconfig: no to everything

---

### Post by spd106 on 2006-09-13
Ok, **lsusb** should tell you a bit more information about the device. 

Try using ndiswrapper and the supplied CD's windows driver.
[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by tturrisi on 2006-09-13
v240:/home/tonyt# lsusb
Bus 004 Device 003: ID 124a:4025 AirVast
Bus 004 Device 001: ID 0000:0000
Bus 002 Device 003: ID 045e:00b9 Microsoft Corp. Wireless Optical Mouse 3.0
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000

I have a Winbook notebook w/ built in wifi.  It's the Airvast shown above.  However, linux does not recognize it enough to be able to use it, thus I use several different pcmcia wifi cards.

According to the queries I made to Winbook tech support the Airvast uses a Prism3 chipset, but I have never been able to get it to work, nor do I need it.

---

### Post by sheine on 2006-09-13
lsusb- The only line with non-zero entries is:
Bus 002 Device 002:ID 124a:268b Air Vast

In response to tturrisi:
On the same laptop, I can make an internet connection with Windows and pclinuxos. Surely, there is a way for Ubuntu to do it too.

---

### Post by tturrisi on 2006-09-14
make certain this is installed:
[http://packages.ubuntu.com/dapper/admin/linux-wlan-ng](http://packages.ubuntu.com/dapper/admin/linux-wlan-ng)

---

### Post by sheine on 2006-09-14
make certain this is installed:
[http://packages.ubuntu.com/dapper/admin/linux-wlan-ng](http://packages.ubuntu.com/dapper/admin/linux-wlan-ng)

Good suggestion, but. It is not installed on my laptop, but I cannot download it there because I have no internet connection. I downloaded it on my desktop with the intention of transferring it by a CD-RW. But, I cannot get permission to transfer it to my CD despite trying sudo with everything. Any help would be welcome.

---

### Post by sheine on 2006-09-14
OK. I found a way to download the wlan package. Ndetwork setup shows an active wireless connection. But, I still can't connect to the internet. Now what?

---

### Post by sheine on 2006-09-14
More information. "Network settings" recognizes my router, NETGEAR, hence information is being received by my computer via wireless. Information:
Network name: Netgear
Key Type: Hexadecimal
Configuration: DHCP

Since I still can't connect to the internet, something needs to be configured or changed. I do not know what.

---

### Post by tturrisi on 2006-09-14
Do you have encryption enabled on the router?  If yes, then net-admin can only use wep, not wpa. If using encryption on router then turn it off & try to connect (after a reboot) using:
Network name: Netgear
Key Type: Plain
Configuration: DHCP

post the result of commands:
iwconfig
iwlist

---

### Post by sheine on 2006-09-14
The clue is in iwconfig.
Bit Rate 2Mb/s 
Link Quality=0/92  Signal level=-100dBm
Noise level=-100dbm

On a different partition of the same laptop, pclinuxos is installed. Its iwconfig gives:
Bit Rate 11Mb/s
Link Quality=26/92  Signal Level=-65dBm
Noise=-92dBm

Now, how do I use this information to correct the problem?

---

### Post by tturrisi on 2006-09-15
boot to pclinux & copy the text of the file:
/var/log/dmesg to see what drivers are being loaded at boot.
also copy txt of /etc/network/interfaces
also copy-compare txt of iwconfig, iwlist, lshw on both

---

### Post by sheine on 2006-09-15
> **tturrisi said:**
> boot to pclinux & copy the text of the file:
/var/log/dmesg to see what drivers are being loaded at boot.
also copy txt of /etc/network/interfaces
also copy-compare txt of iwconfig, iwlist, lshw on both

First, I want to sincerely thank tturrisi for his help. He has changed the problem from no wlan to a weak connection.

I have looked at the requested files and there is simply too much information to copy given my time constraints. Therefore, unless there is very specific information asked, I shall play with it on my own as time allows. If I make any progress, I shall report it here.

---

### Post by sheine on 2006-09-16
One additional question. When I go to networking and configure my wireless connection, WEP key is highlighted. I have been leaving it blank because my router is set for no encryption. Should something be entered?

---

### Post by sheine on 2006-09-16
> **sheine said:**
> One additional question. When I go to networking and configure my wireless connection, WEP key is highlighted. I have been leaving it blank because my router is set for no encryption. Should something be entered?

Although it is peculiar, I no longer think that encryption is the problem. When I do iwconfig, I get the report as described above, but with no encryption information. But, when I do sudo iwconfig wlan0, I get the same information with an additional line, encryption:off. Since the encryption is turned off in my router, this is correct.

Another peculiarity, sometimes I get a weak signal level, 4 or 5, but mostly zero.

---

### Post by tturrisi on 2006-09-17
> **sheine said:**
> First, I want to sincerely thank tturrisi for his help. He has changed the problem from no wlan to a weak connection.

I have looked at the requested files and there is simply too much information to copy given my time constraints. Therefore, unless there is very specific information asked, I shall play with it on my own as time allows. If I make any progress, I shall report it here.
You're welcome...trying to help is one way I learn!

as for posting requested txt:

post the results of these comparisons from pclinux & ubuntu:

/var/log/dmesg near the bottom of the file will be the wifi drivers.

---

### Post by sheine on 2006-09-17
With Ubuntu the relevant line is "prism2_usb 0;0.2.2 Loaded".

With pclinuxos, it is more complicated since I have to reconfigure on each use. Therefore, it is not surprising that there is nothing in /var/log/dmesg. I know from my configuring that it uses the prism2_usb driver.

---

### Post by tturrisi on 2006-09-18
you need the wlan-ng drivers
[http://www.linux-wlan.org/](http://www.linux-wlan.org/)

---

### Post by sheine on 2006-09-18
> **tturrisi said:**
> you need the wlan-ng drivers
[http://www.linux-wlan.org/](http://www.linux-wlan.org/)

For a long time, I have tried to get the driver from:  ftp.linux-wlan.org/pub/linux-wlan-ng and can never get connected. When I just tried it, after a long wait the response was: 550 Could not accept passive data connection- timed out.

Either I am jinxed or there is a trick that I do not know.

---

### Post by tturrisi on 2006-09-18
see if available using Synaptic in Ubuntu.  First enable the Universe-Multi--Universe repositories.  Else here's the download at one of my servers:
[wlan-ng]("http://www.idealorg.com/tonyt/linux-wlan-ng-0.2.3.tar.gz")

---

### Post by sheine on 2006-09-19
I am trying something bold. I am replacing Dapper Drake with the new Edgy Ubuntu. Maybe it will work.

---

### Post by sheine on 2006-09-19
With Edgy things are worse than with Dapper Drake. After installing Edgy, I used my DSL connection to install all wlan and ndis packages. The result is that while Device Manager sees my modem, neither Networking or iwconfig sees my wireless internet connection. What is new is that in iwconfig the third choice wlan0 has been replaced by sit0.

Is it time to say sayonara?

---

### Post by happy-and-lost on 2006-09-19
Install "wifi-radar" (sudo apt-get install wifi-radar)

---

### Post by sheine on 2006-09-19
> **happy-and-lost said:**
> Install "wifi-radar" (sudo apt-get install wifi-radar)

sudo apt-get install wifi-radar cannot find this package. Nor is it in synaptic.

---

### Post by wajvpitt on 2006-09-19
Just found the same thing - I just did a search and downloaded it - works fine but I'm still having problems.

---

### Post by sheine on 2006-09-20
Not a surprise. I downloaded wifi-radar from the WIFI Radar site and installed it. It found no wireless connections. Just to make sure, I loaded pclinuxos on the same laptop and made a wireless internet connection. wifi-radar is not the solution to my problem.

---

### Post by tormod on 2006-09-20
Sheine, you said your device's USB ID was 124a:268b. The listing on [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb) only has 124a:168b. Is your card recognized by the prism2 driver? You can check this using "dmesg" after plugging in the card.

The prism2 drivers (and linux-wlan-ng) are not supported in Edgy, at least for the moment. If anyone wants a package made for Edgy, tell me, and I can mail it or put it on a web server.

---

### Post by sheine on 2006-09-20
> **tormod said:**
> Sheine, you said your device's USB ID was 124a:268b. The listing on [https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb](https://help.ubuntu.com/community/WifiDocs/Driver/prism2_usb) only has 124a:168b. Is your card recognized by the prism2 driver? You can check this using "dmesg" after plugging in the card.

The prism2 drivers (and linux-wlan-ng) are not supported in Edgy, at least for the moment. If anyone wants a package made for Edgy, tell me, and I can mail it or put it on a web server.

It is 124a:168b.
There is nothing about it in dmesg.
It is working for windows (excellent signal) and pclinuxos.

If Edgy does not support prism2 that would explain everything except why Dapper Drake did and Edgy doesn't.

---

### Post by tturrisi on 2006-09-20
again:
I posted a link to direct download the latest wlan-ng drivers.
here it is again:
[wlan-ng]("http://www.idealorg.com/tonyt/linux-wlan-ng-0.2.3.tar.gz")

---

### Post by tormod on 2006-09-20
tturrisi, your 0.2.3 version is pretty old. The dapper version is newer. The debian testing package is even newer.

I'll post some new prism2 drivers and linux-wlan-ng packages for edgy later today, in the Edgy forum.

---

### Post by sheine on 2006-09-20
> **tormod said:**
> tturrisi, your 0.2.3 version is pretty old. The dapper version is newer. The debian testing package is even newer.

I'll post some new prism2 drivers and linux-wlan-ng packages for edgy later today, in the Edgy forum.

I am trying to understand this. I have installed the linux-wlan-ng that I obtained using synaptic in Edgy. Are they inadequate?

---

### Post by tormod on 2006-09-20
> **sheine said:**
> I am trying to understand this. I have installed the linux-wlan-ng that I obtained using synaptic in Edgy. Are they inadequate?

No, it's just not up-to-date, and there are no kernel modules for the prism2 cards. See my post in the Edgy forum: [http://ubuntuforums.org/showthread.php?p=1523110](http://ubuntuforums.org/showthread.php?p=1523110)

---

### Post by sheine on 2006-09-21
Now the ultimate frustration. I have installed the new packages of tormod to my Edgy installation and learned that I had to use the generic not 386 version of Ubuntu in grub. When I did all this, I configured the wireless connection and iwconfig showed a very useable signal strength of 32/92. However, whenever I reboot, iwconfig now shows a signal strength of zero. Wifi-radar shows a strong signal in the opening screen but in the text underneath it, it shows no active connection.
The result of all this is that I still cannot get on to the internet.

---

### Post by tturrisi on 2006-09-21
the wlan-ng I posted was the latest version from the originators of it (at the time I posted it):
[http://www.linux-wlan.com/linux-wlan/index.html#Download](http://www.linux-wlan.com/linux-wlan/index.html#Download)
[ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/](ftp://ftp.linux-wlan.org/pub/linux-wlan-ng/)
the latest version is 0.2.5 (20 sept 06)

---

### Post by tormod on 2006-09-21
> **sheine said:**
> However, whenever I reboot, iwconfig now shows a signal strength of zero. Wifi-radar shows a strong signal in the opening screen but in the text underneath it, it shows no active connection.
I am not sure how this relates to your comments in the Edgy forum, where it apparently works. Anyway, if you are using Edgy now, this Dapper forum is not the best place for us to continue the discussion.

---

### Post by sheine on 2006-09-21
> **tormod said:**
> I am not sure how this relates to your comments in the Edgy forum, where it apparently works. Anyway, if you are using Edgy now, this Dapper forum is not the best place for us to continue the discussion.

When I switched the login to generic and got wireless to work, I immediately posted the information in the Edgy forum because I felt that you were entitled to know that your new package worked for someone. However, after the posting, with subsequent reboots of the computer, I was back to the inability to connect to the internet as described. I am getting a signal as indicated by wifi-radar but it is not being used. The reason I posted here is because it is not an Edgy problem but the same problem as with Dapper Drake.

---

### Post by tormod on 2006-09-21
> **sheine said:**
> When I switched the login to generic and got wireless to work, I immediately posted the information in the Edgy forum because I felt that you were entitled to know that your new package worked for someone. However, after the posting, with subsequent reboots of the computer, I was back to the inability to connect to the internet as described. I am getting a signal as indicated by wifi-radar but it is not being used. The reason I posted here is because it is not an Edgy problem but the same problem as with Dapper Drake.

Thanks for the explanation, it was getting complicated. The best thing would be if you could provide some detailed technical info - can you for instance attach the output from dmesg, lsmod, iwconfig and /etc/network/interfaces? Personally I never used wifi-radar so I can not interpret that you have a signal indicated by it.

You can also try:
sudo modprobe -r prism2_usb
sudo modprobe prism2_usb prism2_doreset=1

sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=disable
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=disable
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable
sudo wlanctl-ng wlan0 lnxreq_ifstate ifstate=enable

Those repeated enable/disable things are a little magic, but you can try, they helped at least for some intermittent problems in older drivers.
And please attach dmesg output from trying this out too.

---

### Post by sheine on 2006-09-21
It wasn't easy because other things are flaky in Edgy. Here it is. All other suggested things gave nothing.




dmesg

[17179569.184000] Linux version 2.6.17-7-generic (root@rothera) (gcc version 4.1.2 20060903 (prerelease) (Ubuntu 4.1.1-13ubuntu1)) #2 SMP Wed Sep 6 17:56:40 UTC 2006 (Ubuntu 2.6.17-7.20-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000ec000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000015ff0000 (usable)
[17179569.184000]  BIOS-e820: 0000000015ff0000 - 0000000015ff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000015ff8000 - 0000000016000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 351MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 90096
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 86000 pages, LIFO batch:15
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000faf70
[17179569.184000] ACPI: RSDT (v001 AMIINT SiS740XX 0x00001000 MSFT 0x0100000b) @ 0x15ff0000
[17179569.184000] ACPI: FADT (v001 AMIINT SiS740XX 0x00000011 MSFT 0x0100000b) @ 0x15ff0030
[17179569.184000] ACPI: DSDT (v001    SiS      740 0x00000100 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 16000000:e9ee0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda4 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (012ca000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1195.114 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179572.244000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179572.244000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179572.264000] Memory: 345524k/360384k available (1840k kernel code, 14276k reserved, 1078k data, 308k init, 0k highmem)
[17179572.264000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179572.344000] Calibrating delay using timer specific routine.. 2392.23 BogoMIPS (lpj=4784471)
[17179572.344000] Security Framework v1.0.0 initialized
[17179572.344000] SELinux:  Disabled at boot.
[17179572.344000] Mount-cache hash table entries: 512
[17179572.344000] CPU: After generic identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.344000] CPU: After vendor identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179572.344000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179572.344000] CPU: L2 Cache: 256K (64 bytes/line)
[17179572.344000] CPU: After all inits, caps: 0383f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[17179572.344000] Checking 'hlt' instruction... OK.
[17179572.360000] SMP alternatives: switching to UP code
[17179572.360000] Freeing SMP alternatives: 16k freed
[17179572.360000] checking if image is initramfs... it is
[17179573.460000] Freeing initrd memory: 7354k freed
[17179573.464000] ACPI: Looking for DSDT ... not found!
[17179573.464000] ACPI: setting ELCR to 0200 (from 0c20)
[17179573.580000] CPU0: AMD mobile AMD Athlon(tm) 4 stepping 02
[17179573.580000] SMP motherboard not detected.
[17179573.580000] Local APIC not detected. Using dummy APIC emulation.
[17179573.580000] Brought up 1 CPUs
[17179573.580000] migration_cost=0
[17179573.580000] NET: Registered protocol family 16
[17179573.580000] EISA bus registered
[17179573.580000] ACPI: bus type pci registered
[17179573.580000] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=2
[17179573.580000] Setting up standard PCI resources
[17179573.584000] ACPI: Subsystem revision 20060127
[17179573.588000] ACPI: Interpreter enabled
[17179573.588000] ACPI: Using PIC for interrupt routing
[17179573.592000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179573.592000] PCI: Probing PCI hardware (bus 00)
[17179573.596000] Uncovering SIS962 that hid as a SIS503 (compatible=0)
[17179573.596000] Enabling SiS 96x SMBus.
[17179573.596000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179573.596000] Boot video device is 0000:01:00.0
[17179573.596000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179573.600000] ACPI: Power Resource [URP1] (off)
[17179573.600000] ACPI: Power Resource [URP2] (off)
[17179573.600000] ACPI: Power Resource [FDDP] (off)
[17179573.600000] ACPI: Power Resource [LPTP] (off)
[17179573.600000] ACPI: Embedded Controller [EC0] (gpe 22) interrupt mode.
[17179573.604000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[17179573.604000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179573.604000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[17179573.604000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179573.608000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *10 11 12 14 15)
[17179573.608000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179573.608000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179573.608000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179573.608000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179573.608000] pnp: PnP ACPI init
[17179573.612000] pnp: PnP ACPI: found 9 devices
[17179573.612000] PnPBIOS: Disabled by ACPI PNP
[17179573.612000] PCI: Using ACPI for IRQ routing
[17179573.612000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179573.616000] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[17179573.616000] PCI: Bridge: 0000:00:01.0
[17179573.616000]   IO window: a000-afff
[17179573.616000]   MEM window: cfd00000-cfefffff
[17179573.616000]   PREFETCH window: bfa00000-cfbfffff
[17179573.616000] NET: Registered protocol family 2
[17179573.644000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179573.644000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179573.644000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179573.644000] TCP: Hash tables configured (established 16384 bind 8192)
[17179573.644000] TCP reno registered
[17179573.644000] audit: initializing netlink socket (disabled)
[17179573.644000] audit(1158800793.644:1): initialized
[17179573.644000] VFS: Disk quotas dquot_6.5.1
[17179573.644000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179573.644000] Initializing Cryptographic API
[17179573.644000] io scheduler noop registered
[17179573.644000] io scheduler anticipatory registered
[17179573.644000] io scheduler deadline registered
[17179573.644000] io scheduler cfq registered (default)
[17179573.644000] isapnp: Scanning for PnP cards...
[17179574.000000] isapnp: No Plug & Play device found
[17179574.040000] Real Time Clock Driver v1.12ac
[17179574.040000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179574.040000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179574.040000] PCI: setting IRQ 10 as level-triggered
[17179574.040000] ACPI: PCI Interrupt 0000:00:02.6[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179574.040000] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[17179574.040000] mice: PS/2 mouse device common for all mice
[17179574.040000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179574.040000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179574.040000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179574.040000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179574.044000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179574.044000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179574.044000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179574.044000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179574.044000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179574.044000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179574.044000] EISA: Probing bus 0 at eisa.0
[17179574.044000] EISA: Detected 0 cards.
[17179574.044000] TCP bic registered
[17179574.044000] NET: Registered protocol family 1
[17179574.044000] NET: Registered protocol family 8
[17179574.044000] NET: Registered protocol family 20
[17179574.044000] Using IPI No-Shortcut mode
[17179574.044000] ACPI wakeup devices: 
[17179574.044000] PCI0 USB1 USB2 USB4  LAN  MDM  AUD CRD1 CRD2 
[17179574.044000] ACPI: (supports S0 S1 S3 S4 S5)
[17179574.044000] Freeing unused kernel memory: 308k freed
[17179574.652000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179575.208000] Capability LSM initialized
[17179576.124000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179576.124000] SIS5513: chipset revision 0
[17179576.124000] SIS5513: not 100% native mode: will probe irqs later
[17179576.124000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179576.124000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[17179576.124000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
[17179576.124000] Probing IDE interface ide0...
[17179576.412000] hda: HITACHI_DK23FB-40, ATA DISK drive
[17179576.748000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179576.752000] Probing IDE interface ide1...
[17179577.488000] hdc: MATSHITADVD-ROM SR-8178, ATAPI CD/DVD-ROM drive
[17179577.824000] ide1 at 0x170-0x177,0x376 on irq 15
[17179577.836000] hda: max request size: 128KiB
[17179577.848000] hda: 78140160 sectors (40007 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(33)
[17179577.852000] hda: cache flushes supported
[17179577.852000]  hda: hda1 hda2 < hda5 hda6 hda7 > hda3 hda4
[17179577.932000] hdc: ATAPI 24X DVD-ROM drive, 256kB Cache, UDMA(33)
[17179577.932000] Uniform CD-ROM driver Revision: 3.20
[17179578.352000] usbcore: registered new driver usbfs
[17179578.352000] usbcore: registered new driver hub
[17179578.356000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[17179578.356000] PCI: setting IRQ 5 as level-triggered
[17179578.356000] ACPI: PCI Interrupt 0000:00:03.3[D] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[17179578.356000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[17179578.356000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[17179578.356000] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[17179578.356000] ehci_hcd 0000:00:03.3: irq 5, io mem 0xcfffb000
[17179578.356000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179578.356000] usb usb1: configuration #1 chosen from 1 choice
[17179578.356000] hub 1-0:1.0: USB hub found
[17179578.356000] hub 1-0:1.0: 6 ports detected
[17179578.368000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179578.476000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[17179578.476000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[17179578.476000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179578.476000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[17179578.496000] ohci_hcd 0000:00:03.0: irq 10, io mem 0xcfff9000
[17179578.552000] usb usb2: configuration #1 chosen from 1 choice
[17179578.552000] hub 2-0:1.0: USB hub found
[17179578.552000] hub 2-0:1.0: 3 ports detected
[17179578.804000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 5
[17179578.804000] ACPI: PCI Interrupt 0000:00:03.1[B] -> Link [LNKF] -> GSI 5 (level, low) -> IRQ 5
[17179578.804000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179578.804000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[17179578.828000] ohci_hcd 0000:00:03.1: irq 5, io mem 0xcfffa000
[17179578.884000] usb usb3: configuration #1 chosen from 1 choice
[17179578.884000] hub 3-0:1.0: USB hub found
[17179578.884000] hub 3-0:1.0: 3 ports detected
[17179579.080000] Attempting manual resume
[17179579.100000] EXT3-fs: INFO: recovery required on readonly filesystem.
[17179579.100000] EXT3-fs: write access will be enabled during recovery.
[17179579.292000] usb 3-2: new full speed USB device using ohci_hcd and address 2
[17179579.504000] usb 3-2: configuration #1 chosen from 1 choice
[17179581.300000] kjournald starting.  Commit interval 5 seconds
[17179581.300000] EXT3-fs: recovery complete.
[17179581.300000] EXT3-fs: mounted filesystem with ordered data mode.
[17179590.988000] prism2usb_init: prism2_usb.o: 0.2.4 Loaded
[17179590.988000] prism2usb_init: dev_info is: prism2_usb
[17179590.988000] usbcore: registered new driver prism2_usb
[17179591.232000] parport: PnPBIOS parport detected.
[17179591.232000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179591.712000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x1d6eb1, caps: 0xa04713/0x4006
[17179591.748000] input: SynPS/2 Synaptics TouchPad as /class/input/input1
[17179591.752000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179592.068000] input: PC Speaker as /class/input/input2
[17179592.240000] r8169 Gigabit Ethernet driver 2.2LK loaded
[17179592.244000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179592.244000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179592.244000] eth0: Identified chip type is 'RTL8169s/8110s'.
[17179592.244000] eth0: RTL8169 at 0xd68a6f00, 00:11:5b:57:99:27, IRQ 5
[17179592.348000] Linux agpgart interface v0.101 (c) Dave Jones
[17179592.352000] agpgart: Detected SiS 740 chipset
[17179592.360000] agpgart: AGP aperture is 64M @ 0xd0000000
[17179592.488000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[17179593.192000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.216000] ts: Compaq touchscreen protocol output
[17179593.220000] hfa384x_usbin_rx: Received frame on unsupported port=4
[17179593.220000] ident: nic h/w: id=0x8026 1.0.0
[17179593.220000] ident: pri f/w: id=0x15 1.1.3
[17179593.224000] ident: sta f/w: id=0x1f 1.5.6
[17179593.224000] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
[17179593.228000] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
[17179593.228000] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
[17179593.232000] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/10
[17179593.232000] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[17179593.236000] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[17179593.240000] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
[17179593.248000] Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00
[17179593.592000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.636000] r8169: eth0: link down
[17179593.920000] ieee80211_crypt: registered algorithm 'NULL'
[17179593.924000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179593.924000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179593.948000] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179594.672000] NET: Registered protocol family 17
[17179594.772000] intel8x0_measure_ac97_clock: measured 55164 usecs
[17179594.772000] intel8x0: clocking to 48000
[17179596.456000] lp0: using parport0 (interrupt-driven).
[17179596.576000] Adding 931728k swap on /dev/disk/by-uuid/9056a13f-2891-464b-a0aa-3e1ed1c70acb.  Priority:-1 extents:1 across:931728k
[17179596.772000] EXT3 FS on hda4, internal journal
[17179604.624000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179604.676000] NTFS volume version 3.1.
[17179604.816000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17179604.816000] SGI XFS Quota Management subsystem
[17179604.872000] XFS mounting filesystem hda5
[17179605.012000] Ending clean XFS mount for filesystem: hda5
__________________________________________________________

sidney@sidney-laptop:~$ locate lsmod
/bin/lsmod
/bin/lsmod.modutils
/sbin/lsmod
/sbin/lsmod.modutils
/usr/bin/enchant-lsmod
/usr/share/man/man8/lsmod.8.gz
sidney@sidney-laptop:~$ lsmod
Module                  Size  Used by
ipv6                  271520  8 
binfmt_misc            12424  1 
rfcomm                 40404  0 
l2cap                  25632  5 rfcomm
bluetooth              51652  4 rfcomm,l2cap
powernow_k7             8008  0 
cpufreq_userspace       4608  0 
cpufreq_stats           6848  0 
freq_table              5216  2 powernow_k7,cpufreq_stats
cpufreq_powersave       2048  0 
cpufreq_ondemand        8012  1 
cpufreq_conservative     8008  0 
video                  16292  0 
tc1100_wmi              7460  0 
sony_acpi               5644  0 
pcc_acpi               13440  0 
hotkey                 10500  0 
dev_acpi               11492  0 
container               4768  0 
button                  6992  0 
acpi_sbs               22636  0 
battery                10436  1 acpi_sbs
i2c_acpi_ec             5376  1 acpi_sbs
ac                      5508  1 acpi_sbs
xfs                   628824  1 
ext2                   71272  2 
nls_utf8                2336  1 
ntfs                  111764  1 
lp                     12484  0 
af_packet              22888  4 
ieee80211              34952  0 
ieee80211_crypt         6592  1 ieee80211
shpchp                 41472  0 
pci_hotplug            32092  1 shpchp
joydev                 10336  0 
i2c_sis96x              5860  0 
i2c_core               22752  2 i2c_acpi_ec,i2c_sis96x
snd_intel8x0           34172  1 
snd_ac97_codec         97376  1 snd_intel8x0
snd_ac97_bus            2528  1 snd_ac97_codec
snd_pcm_oss            46272  0 
snd_mixer_oss          18592  1 snd_pcm_oss
sis_agp                 8996  1 
agpgart                33992  1 sis_agp
tsdev                   8320  0 
evdev                  10496  1 
snd_pcm                82916  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_timer              24324  1 snd_pcm
snd                    56644  8 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_timer
soundcore              10272  1 snd
snd_page_alloc         10536  2 snd_intel8x0,snd_pcm
r1000                  16992  0 
r8169                  31240  0 
parport_pc             36996  1 
parport                38408  2 lp,parport_pc
pcspkr                  3392  0 
prism2_usb             78980  0 
p80211                 33100  1 prism2_usb
psmouse                40360  0 
serio_raw               7524  0 
ext3                  142632  1 
jbd                    60980  1 ext3
ohci_hcd               21796  0 
ehci_hcd               34088  0 
usbcore               134432  4 prism2_usb,ohci_hcd,ehci_hcd
ide_generic             1600  0 
ide_cd                 32928  0 
cdrom                  38336  1 ide_cd
ide_disk               17728  7 
sis5513                14632  1 
generic                 4900  0 
thermal                14056  0 
processor              27560  2 powernow_k7,thermal
fan                     4804  0 
fbcon                  41664  0 
tileblit                2976  1 fbcon
font                    8480  1 fbcon
bitblit                 6464  1 fbcon
softcursor              2336  1 bitblit
vesafb                  8412  0 
capability              5064  0 
commoncap               7648  1 capability
______________________________________________________________
sidney@sidney-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"Netgear"  Nickname:"Netgear"
          Mode:Auto  Channel:0  Access Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:2346 dBm   
          Retry min limit:8   RTS thr:off   Fragment thr:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

sit0      no wireless extensions.

______________________________________________________________


sidney@sidney-laptop:~$ more  /etc/network/interfaces
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
wireless-essid Netgear

---

### Post by tormod on 2006-09-22
From your dmesg output it looks like you booted with the card/stick inserted. Can you try unplugging and replugging the device after the boot has finished? Then wait a little, and if there's no network, try those commands I told you. Please run dmesg afterwards and attach the output. Please use the **Manage Attachments** button instead of pasting into your message.

"*All other suggested things gave nothing.*" Was there nothing showing up in dmesg?

There is one suspicious message in your dmesg output:
hfa384x_usbin_rx: Received frame on unsupported port=4
Maybe a firmware upload can help you. I can post some firmware packages for Edgy later, but I'll have to test them myself first.

---

### Post by sheine on 2006-09-22
Nothing is plugged into my computer. Signal strength is still zero.Two sudo modprobes get no response. Carried out wlanctl's and signal strength is still zero.
I tried "manage attachments" and the response to /var/log/dmesg was "invalid file". I turned it into a .txt file, which is allowed, and still got the response invalid file. Here it is;

[17179569.184000] Linux version 2.6.17-7-generic (root@rothera) (gcc version 4.1.2 20060903 (prerelease) (Ubuntu 4.1.1-13ubuntu1)) #2 SMP Wed Sep 6 17:56:40 UTC 2006 (Ubuntu 2.6.17-7.20-generic)
[17179569.184000] BIOS-provided physical RAM map:
[17179569.184000]  BIOS-e820: 0000000000000000 - 000000000009fc00 (usable)
[17179569.184000]  BIOS-e820: 000000000009fc00 - 00000000000a0000 (reserved)
[17179569.184000]  BIOS-e820: 00000000000ec000 - 0000000000100000 (reserved)
[17179569.184000]  BIOS-e820: 0000000000100000 - 0000000015ff0000 (usable)
[17179569.184000]  BIOS-e820: 0000000015ff0000 - 0000000015ff8000 (ACPI data)
[17179569.184000]  BIOS-e820: 0000000015ff8000 - 0000000016000000 (ACPI NVS)
[17179569.184000]  BIOS-e820: 00000000ffee0000 - 00000000fff00000 (reserved)
[17179569.184000]  BIOS-e820: 00000000fffc0000 - 0000000100000000 (reserved)
[17179569.184000] 0MB HIGHMEM available.
[17179569.184000] 351MB LOWMEM available.
[17179569.184000] On node 0 totalpages: 90096
[17179569.184000]   DMA zone: 4096 pages, LIFO batch:0
[17179569.184000]   Normal zone: 86000 pages, LIFO batch:15
[17179569.184000] DMI 2.3 present.
[17179569.184000] ACPI: RSDP (v000 AMI                                   ) @ 0x000faf70
[17179569.184000] ACPI: RSDT (v001 AMIINT SiS740XX 0x00001000 MSFT 0x0100000b) @ 0x15ff0000
[17179569.184000] ACPI: FADT (v001 AMIINT SiS740XX 0x00000011 MSFT 0x0100000b) @ 0x15ff0030
[17179569.184000] ACPI: DSDT (v001    SiS      740 0x00000100 MSFT 0x0100000e) @ 0x00000000
[17179569.184000] ACPI: PM-Timer IO Port: 0x808
[17179569.184000] Allocating PCI resources starting at 20000000 (gap: 16000000:e9ee0000)
[17179569.184000] Built 1 zonelists
[17179569.184000] Kernel command line: root=/dev/hda4 ro quiet splash
[17179569.184000] Local APIC disabled by BIOS (or by default) -- you can enable it with "lapic"
[17179569.184000] mapped APIC to ffffd000 (012ca000)
[17179569.184000] Enabling fast FPU save and restore... done.
[17179569.184000] Enabling unmasked SIMD FPU exception support... done.
[17179569.184000] Initializing CPU#0
[17179569.184000] PID hash table entries: 2048 (order: 11, 8192 bytes)
[17179569.184000] Detected 1195.103 MHz processor.
[17179569.184000] Using pmtmr for high-res timesource
[17179569.184000] Console: colour VGA+ 80x25
[17179569.376000] Dentry cache hash table entries: 65536 (order: 6, 262144 bytes)
[17179569.376000] Inode-cache hash table entries: 32768 (order: 5, 131072 bytes)
[17179569.396000] Memory: 345524k/360384k available (1840k kernel code, 14276k reserved, 1078k data, 308k init, 0k highmem)
[17179569.396000] Checking if this processor honours the WP bit even in supervisor mode... Ok.
[17179569.476000] Calibrating delay using timer specific routine.. 2392.22 BogoMIPS (lpj=4784444)
[17179569.476000] Security Framework v1.0.0 initialized
[17179569.476000] SELinux:  Disabled at boot.
[17179569.476000] Mount-cache hash table entries: 512
[17179569.476000] CPU: After generic identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179569.476000] CPU: After vendor identify, caps: 0383f9ff c1c3f9ff 00000000 00000000 00000000 00000000 00000000
[17179569.476000] CPU: L1 I Cache: 64K (64 bytes/line), D cache 64K (64 bytes/line)
[17179569.476000] CPU: L2 Cache: 256K (64 bytes/line)
[17179569.476000] CPU: After all inits, caps: 0383f9ff c1c3f9ff 00000000 00000420 00000000 00000000 00000000
[17179569.476000] Checking 'hlt' instruction... OK.
[17179569.492000] SMP alternatives: switching to UP code
[17179569.492000] Freeing SMP alternatives: 16k freed
[17179569.492000] checking if image is initramfs... it is
[17179570.592000] Freeing initrd memory: 7354k freed
[17179570.596000] ACPI: Looking for DSDT ... not found!
[17179570.596000] ACPI: setting ELCR to 0200 (from 0c20)
[17179570.712000] CPU0: AMD mobile AMD Athlon(tm) 4 stepping 02
[17179570.712000] SMP motherboard not detected.
[17179570.712000] Local APIC not detected. Using dummy APIC emulation.
[17179570.712000] Brought up 1 CPUs
[17179570.712000] migration_cost=0
[17179570.712000] NET: Registered protocol family 16
[17179570.712000] EISA bus registered
[17179570.712000] ACPI: bus type pci registered
[17179570.712000] PCI: PCI BIOS revision 2.10 entry at 0xfdb01, last bus=2
[17179570.712000] Setting up standard PCI resources
[17179570.716000] ACPI: Subsystem revision 20060127
[17179570.720000] ACPI: Interpreter enabled
[17179570.720000] ACPI: Using PIC for interrupt routing
[17179570.724000] ACPI: PCI Root Bridge [PCI0] (0000:00)
[17179570.724000] PCI: Probing PCI hardware (bus 00)
[17179570.728000] Uncovering SIS962 that hid as a SIS503 (compatible=0)
[17179570.728000] Enabling SiS 96x SMBus.
[17179570.728000] PCI: Ignoring BAR0-3 of IDE controller 0000:00:02.5
[17179570.728000] Boot video device is 0000:01:00.0
[17179570.728000] ACPI: PCI Interrupt Routing Table [\_SB_.PCI0._PRT]
[17179570.732000] ACPI: Power Resource [URP1] (off)
[17179570.732000] ACPI: Power Resource [URP2] (off)
[17179570.732000] ACPI: Power Resource [FDDP] (off)
[17179570.732000] ACPI: Power Resource [LPTP] (off)
[17179570.732000] ACPI: Embedded Controller [EC0] (gpe 22) interrupt mode.
[17179570.736000] ACPI: PCI Interrupt Link [LNKA] (IRQs 3 4 5 7 10 *11 12 14 15)
[17179570.736000] ACPI: PCI Interrupt Link [LNKB] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179570.736000] ACPI: PCI Interrupt Link [LNKC] (IRQs 3 4 5 7 *10 11 12 14 15)
[17179570.736000] ACPI: PCI Interrupt Link [LNKD] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179570.740000] ACPI: PCI Interrupt Link [LNKE] (IRQs 3 4 5 7 *10 11 12 14 15)
[17179570.740000] ACPI: PCI Interrupt Link [LNKF] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179570.740000] ACPI: PCI Interrupt Link [LNKG] (IRQs 3 4 5 7 10 11 12 14 15) *0, disabled.
[17179570.740000] ACPI: PCI Interrupt Link [LNKH] (IRQs 3 4 *5 7 10 11 12 14 15)
[17179570.740000] Linux Plug and Play Support v0.97 (c) Adam Belay
[17179570.740000] pnp: PnP ACPI init
[17179570.744000] pnp: PnP ACPI: found 9 devices
[17179570.744000] PnPBIOS: Disabled by ACPI PNP
[17179570.744000] PCI: Using ACPI for IRQ routing
[17179570.744000] PCI: If a device doesn't work, try "pci=routeirq".  If it helps, post a report
[17179570.748000] PCI: Ignore bogus resource 6 [0:0] of 0000:01:00.0
[17179570.748000] PCI: Bridge: 0000:00:01.0
[17179570.748000]   IO window: a000-afff
[17179570.748000]   MEM window: cfd00000-cfefffff
[17179570.748000]   PREFETCH window: bfa00000-cfbfffff
[17179570.748000] NET: Registered protocol family 2
[17179570.776000] IP route cache hash table entries: 4096 (order: 2, 16384 bytes)
[17179570.776000] TCP established hash table entries: 16384 (order: 5, 131072 bytes)
[17179570.776000] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[17179570.776000] TCP: Hash tables configured (established 16384 bind 8192)
[17179570.776000] TCP reno registered
[17179570.776000] audit: initializing netlink socket (disabled)
[17179570.776000] audit(1158865069.776:1): initialized
[17179570.776000] VFS: Disk quotas dquot_6.5.1
[17179570.776000] Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[17179570.776000] Initializing Cryptographic API
[17179570.776000] io scheduler noop registered
[17179570.776000] io scheduler anticipatory registered
[17179570.776000] io scheduler deadline registered
[17179570.776000] io scheduler cfq registered (default)
[17179570.776000] isapnp: Scanning for PnP cards...
[17179571.132000] isapnp: No Plug & Play device found
[17179571.172000] Real Time Clock Driver v1.12ac
[17179571.172000] Serial: 8250/16550 driver $Revision: 1.90 $ 4 ports, IRQ sharing enabled
[17179571.172000] ACPI: PCI Interrupt Link [LNKC] enabled at IRQ 10
[17179571.172000] PCI: setting IRQ 10 as level-triggered
[17179571.172000] ACPI: PCI Interrupt 0000:00:02.6[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179571.172000] ACPI: PCI interrupt for device 0000:00:02.6 disabled
[17179571.172000] mice: PS/2 mouse device common for all mice
[17179571.172000] RAMDISK driver initialized: 16 RAM disks of 65536K size 1024 blocksize
[17179571.172000] Uniform Multi-Platform E-IDE driver Revision: 7.00alpha2
[17179571.172000] ide: Assuming 33MHz system bus speed for PIO modes; override with idebus=xx
[17179571.172000] PNP: PS/2 Controller [PNP0303:PS2K,PNP0f03:PS2M] at 0x60,0x64 irq 1,12
[17179571.176000] i8042.c: Detected active multiplexing controller, rev 1.1.
[17179571.176000] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[17179571.176000] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[17179571.176000] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[17179571.176000] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[17179571.176000] serio: i8042 KBD port at 0x60,0x64 irq 1
[17179571.176000] EISA: Probing bus 0 at eisa.0
[17179571.176000] EISA: Detected 0 cards.
[17179571.176000] TCP bic registered
[17179571.176000] NET: Registered protocol family 1
[17179571.176000] NET: Registered protocol family 8
[17179571.176000] NET: Registered protocol family 20
[17179571.176000] Using IPI No-Shortcut mode
[17179571.176000] ACPI wakeup devices: 
[17179571.176000] PCI0 USB1 USB2 USB4  LAN  MDM  AUD CRD1 CRD2 
[17179571.176000] ACPI: (supports S0 S1 S3 S4 S5)
[17179571.176000] Freeing unused kernel memory: 308k freed
[17179571.784000] input: AT Translated Set 2 keyboard as /class/input/input0
[17179572.340000] Capability LSM initialized
[17179573.268000] SIS5513: IDE controller at PCI slot 0000:00:02.5
[17179573.268000] SIS5513: chipset revision 0
[17179573.268000] SIS5513: not 100% native mode: will probe irqs later
[17179573.268000] SIS5513: SiS 962/963 MuTIOL IDE UDMA133 controller
[17179573.268000]     ide0: BM-DMA at 0xff00-0xff07, BIOS settings: hda:DMA, hdb:DMA
[17179573.268000]     ide1: BM-DMA at 0xff08-0xff0f, BIOS settings: hdc:DMA, hdd:DMA
[17179573.268000] Probing IDE interface ide0...
[17179573.556000] hda: HITACHI_DK23FB-40, ATA DISK drive
[17179573.892000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14
[17179573.896000] Probing IDE interface ide1...
[17179574.632000] hdc: MATSHITADVD-ROM SR-8178, ATAPI CD/DVD-ROM drive
[17179574.968000] ide1 at 0x170-0x177,0x376 on irq 15
[17179574.980000] hda: max request size: 128KiB
[17179574.996000] hda: 78140160 sectors (40007 MB) w/8192KiB Cache, CHS=65535/16/63, UDMA(33)
[17179574.996000] hda: cache flushes supported
[17179574.996000]  hda: hda1 hda2 < hda5 hda6 hda7 > hda3 hda4
[17179575.072000] hdc: ATAPI 24X DVD-ROM drive, 256kB Cache, UDMA(33)
[17179575.072000] Uniform CD-ROM driver Revision: 3.20
[17179575.448000] usbcore: registered new driver usbfs
[17179575.448000] usbcore: registered new driver hub
[17179575.448000] ACPI: PCI Interrupt Link [LNKH] enabled at IRQ 5
[17179575.448000] PCI: setting IRQ 5 as level-triggered
[17179575.448000] ACPI: PCI Interrupt 0000:00:03.3[D] -> Link [LNKH] -> GSI 5 (level, low) -> IRQ 5
[17179575.448000] ehci_hcd 0000:00:03.3: EHCI Host Controller
[17179575.448000] ehci_hcd 0000:00:03.3: new USB bus registered, assigned bus number 1
[17179575.448000] PCI: cache line size of 64 is not supported by device 0000:00:03.3
[17179575.448000] ehci_hcd 0000:00:03.3: irq 5, io mem 0xcfffb000
[17179575.448000] ehci_hcd 0000:00:03.3: USB 2.0 started, EHCI 1.00, driver 10 Dec 2004
[17179575.452000] usb usb1: configuration #1 chosen from 1 choice
[17179575.452000] hub 1-0:1.0: USB hub found
[17179575.452000] hub 1-0:1.0: 6 ports detected
[17179575.464000] ohci_hcd: 2005 April 22 USB 1.1 'Open' Host Controller (OHCI) Driver (PCI)
[17179575.572000] ACPI: PCI Interrupt Link [LNKE] enabled at IRQ 10
[17179575.572000] ACPI: PCI Interrupt 0000:00:03.0[A] -> Link [LNKE] -> GSI 10 (level, low) -> IRQ 10
[17179575.572000] ohci_hcd 0000:00:03.0: OHCI Host Controller
[17179575.572000] ohci_hcd 0000:00:03.0: new USB bus registered, assigned bus number 2
[17179575.592000] ohci_hcd 0000:00:03.0: irq 10, io mem 0xcfff9000
[17179575.648000] usb usb2: configuration #1 chosen from 1 choice
[17179575.648000] hub 2-0:1.0: USB hub found
[17179575.648000] hub 2-0:1.0: 3 ports detected
[17179575.900000] ACPI: PCI Interrupt Link [LNKF] enabled at IRQ 5
[17179575.900000] ACPI: PCI Interrupt 0000:00:03.1[B] -> Link [LNKF] -> GSI 5 (level, low) -> IRQ 5
[17179575.900000] ohci_hcd 0000:00:03.1: OHCI Host Controller
[17179575.900000] ohci_hcd 0000:00:03.1: new USB bus registered, assigned bus number 3
[17179575.924000] ohci_hcd 0000:00:03.1: irq 5, io mem 0xcfffa000
[17179575.980000] usb usb3: configuration #1 chosen from 1 choice
[17179575.980000] hub 3-0:1.0: USB hub found
[17179575.980000] hub 3-0:1.0: 3 ports detected
[17179576.176000] Attempting manual resume
[17179576.204000] kjournald starting.  Commit interval 5 seconds
[17179576.204000] EXT3-fs: mounted filesystem with ordered data mode.
[17179576.388000] usb 3-2: new full speed USB device using ohci_hcd and address 2
[17179576.600000] usb 3-2: configuration #1 chosen from 1 choice
[17179586.680000] parport: PnPBIOS parport detected.
[17179586.680000] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,ECP,DMA]
[17179586.724000] prism2usb_init: prism2_usb.o: 0.2.4 Loaded
[17179586.724000] prism2usb_init: dev_info is: prism2_usb
[17179586.724000] usbcore: registered new driver prism2_usb
[17179586.868000] input: PC Speaker as /class/input/input1
[17179587.516000] Synaptics Touchpad, model: 1, fw: 5.9, id: 0x1d6eb1, caps: 0xa04713/0x4006
[17179587.548000] input: SynPS/2 Synaptics TouchPad as /class/input/input2
[17179587.552000] psmouse.c: TouchPad at isa0060/serio4/input0 lost sync at byte 1
[17179588.120000] r8169 Gigabit Ethernet driver 2.2LK loaded
[17179588.120000] ACPI: PCI Interrupt Link [LNKB] enabled at IRQ 5
[17179588.120000] ACPI: PCI Interrupt 0000:00:07.0[A] -> Link [LNKB] -> GSI 5 (level, low) -> IRQ 5
[17179588.124000] eth0: Identified chip type is 'RTL8169s/8110s'.
[17179588.124000] eth0: RTL8169 at 0xd6862f00, 00:11:5b:57:99:27, IRQ 5
[17179588.244000] Linux agpgart interface v0.101 (c) Dave Jones
[17179588.332000] agpgart: Detected SiS 740 chipset
[17179588.340000] agpgart: AGP aperture is 64M @ 0xd0000000
[17179588.548000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179588.552000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179588.616000] sis96x_smbus 0000:00:02.1: SiS96x SMBus base address: 0x0c00
[17179588.696000] ts: Compaq touchscreen protocol output
[17179588.728000] ieee80211_crypt: registered algorithm 'NULL'
[17179588.756000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[17179588.756000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[17179589.344000] ACPI: PCI Interrupt 0000:00:02.7[C] -> Link [LNKC] -> GSI 10 (level, low) -> IRQ 10
[17179589.696000] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[17179589.696000] prism2sta_getcardinfo: Failed to retrieve NICIDENTITY
[17179589.696000] prism2sta_getcardinfo: Failed, result=-5
[17179589.696000] prism2sta_ifstate: prism2sta_getcardinfo() failed,result=-5
[17179590.164000] intel8x0_measure_ac97_clock: measured 55182 usecs
[17179590.164000] intel8x0: clocking to 48000
[17179590.312000] hfa384x_usbin_rx: Received frame on unsupported port=4
[17179590.768000] ident: nic h/w: id=0x8026 1.0.0
[17179590.768000] ident: pri f/w: id=0x15 1.1.3
[17179590.772000] ident: sta f/w: id=0x1f 1.5.6
[17179590.772000] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
[17179590.776000] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
[17179590.776000] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
[17179590.780000] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/10
[17179590.780000] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[17179590.784000] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[17179590.784000] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
[17179590.788000] Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00
[17179590.836000] r8169: eth0: link up
[17179591.884000] NET: Registered protocol family 17
[17179593.704000] lp0: using parport0 (interrupt-driven).
[17179593.820000] Adding 931728k swap on /dev/disk/by-uuid/9056a13f-2891-464b-a0aa-3e1ed1c70acb.  Priority:-1 extents:1 across:931728k
[17179594.032000] EXT3 FS on hda4, internal journal
[17179594.520000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179594.576000] NTFS volume version 3.1.
[17179594.712000] SGI XFS with ACLs, security attributes, realtime, large block numbers, no debug enabled
[17179594.712000] SGI XFS Quota Management subsystem
[17179594.744000] XFS mounting filesystem hda5
[17179594.880000] Ending clean XFS mount for filesystem: hda5
[17179597.408000] NET: Registered protocol family 10
[17179597.408000] lo: Disabled Privacy Extensions
[17179597.408000] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[17179597.408000] IPv6 over IPv4 tunneling driver

---

### Post by tormod on 2006-09-22
> **sheine said:**
> Nothing is plugged into my computer.
I am slowly getting it - you have a built-in USB card... :)

> I tried "manage attachments" and the response to /var/log/dmesg was "invalid file". I turned it into a .txt file, which is allowed, and still got the response invalid file.
Ok, must be a bug in the forum attachments handling. But do not attach or post /var/log/dmesg - that one is only saved once at boot-up. Run "dmesg > dmesg.txt" and give us dmesg.txt.

> [17179589.696000] hfa384x_usbctlx_complete_sync: CTLX[3] error: state(Request failed)
[17179589.696000] prism2sta_getcardinfo: Failed to retrieve NICIDENTITY
[17179589.696000] prism2sta_getcardinfo: Failed, result=-5
[17179589.696000] prism2sta_ifstate: prism2sta_getcardinfo() failed,result=-5
[17179590.312000] hfa384x_usbin_rx: Received frame on unsupported port=4
[17179590.768000] ident: nic h/w: id=0x8026 1.0.0
[17179590.768000] ident: pri f/w: id=0x15 1.1.3
[17179590.772000] ident: sta f/w: id=0x1f 1.5.6
[17179590.772000] MFI:SUP:role=0x00:id=0x01:var=0x01:b/t=1/1
[17179590.776000] CFI:SUP:role=0x00:id=0x02:var=0x02:b/t=1/1
[17179590.776000] PRI:SUP:role=0x00:id=0x03:var=0x01:b/t=1/4
[17179590.780000] STA:SUP:role=0x00:id=0x04:var=0x01:b/t=1/10
[17179590.780000] PRI-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[17179590.784000] STA-CFI:ACT:role=0x01:id=0x02:var=0x02:b/t=1/1
[17179590.784000] STA-MFI:ACT:role=0x01:id=0x01:var=0x01:b/t=1/1
[17179590.788000] Prism2 card SN: \x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00\x00

The firmware (1.5.6) indeed seems a little old, so I would be optimistic an update might help.


Update: Does this mean you only looked in /var/log/dmesg after trying out different things? Try again and run the "dmesg" command.

---

### Post by sheine on 2006-09-22
I think that the real clue is here. I am sending you iwconfig from pclinuxos and Ubuntu. Note the Access Point difference as well as the strong pclinuxos signal with the laptop in the same location.

pclinuxos

wlan0     IEEE 802.11-b  ESSID:"NETGEAR" 
Nickname:"NETGEAR"
          Mode:Managed  Frequency:2.462 GHz  Access
Point: 00:0F:B5:A0:6A:B4
          Bit Rate:11 Mb/s   Tx-Power:2346 dBm
          Retry min limit:8   RTS thr:off   Fragment
thr:off
          Encryption key:off
          Link Quality=57/92  Signal level=-34 dBm 
Noise level=-92 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx
invalid frag:0
          Tx excessive retries:0  Invalid misc:0  
Missed beacon:0

Ubuntu

sidney@sidney-laptop:~$ iwconfig
lo        no wireless extensions.

wlan0     IEEE 802.11-DS  ESSID:"Netgear" 
Nickname:"Netgear"
          Mode:Auto  Frequency:2.484 GHz  Access
Point: Not-Associated   
          Bit Rate:2 Mb/s   Tx-Power:2346 dBm   
          Retry min limit:8   RTS thr:off   Fragment
thr:off
          Link Quality:0  Signal level:0  Noise
level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx
invalid frag:0
          Tx excessive retries:0  Invalid misc:0  
Missed beacon:0

eth0      no wireless extensions.

---

### Post by tormod on 2006-09-22
Well, the clue I get here is that you use "NETGEAR" in one, and "Netgear" in the other.

---

### Post by sheine on 2006-09-22
Believe it or not, changing from Netgear to NETGEAR solved the problem. It is now better than pclinuxos where I have to configure with each new boot.

Thank you tormod for your patience and help.

---

### Post by tormod on 2006-09-22
I perfectly believe it, ESSIDs are case sensitive. What I can't believe is that you obviously happened to type in correctly "NETGEAR" once (the first time you tried the new packages in Edgy and everything worked) and then all the other times "Netgear"...

Things like this is easy to overlook if you don't think about them,
that's why we ask for file copies and verbatim tech output, not just your own interpretation of it ;)

---

### Post by sheine on 2006-09-22
In my defense, pclinuxos found "NETGEAR" on its own. I am not quite sure how a person is to know what to install among NETGEAR, Netgear, and netgear without help. Using wifi-radar, the default is not a version of Netgear but ssid. Shouldn't Ubuntu find it in the same way that pclinuxos does? After all, it did recognize the connection with Netgear but reported a zero signal.

---

### Post by tormod on 2006-09-22
The Networking tool in Ubuntu lists the available networks and let you just pick the right one when you click the drop-down menu, without any typing. This should at least work when there is nothing set up in /etc/network/interfaces. Otherwise it is a bug, to be reported :)

Edit: The bug is [https://launchpad.net/bugs/59159](https://launchpad.net/bugs/59159)

---

