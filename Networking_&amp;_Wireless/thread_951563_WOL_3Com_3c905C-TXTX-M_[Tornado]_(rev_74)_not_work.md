---
title: "WOL 3Com 3c905C-TX/TX-M [Tornado] (rev 74) not working"
date: 2008-10-18
forum: Networking &amp; Wireless
---

### Post by c.monty on 2008-10-18
hi!

I'm trying to configure WOL on Ubuntu 8.04 LTS server.
I've read several threads and apparently something is strange in output of lspci and cat /proc/acpi/wakeup:
```
user@server:~$ cat /proc/acpi/wakeup
Device	S-state	  Status   Sysfs node
SLPB	  S5	*enabled   
PCI0	  S5	 disabled  no-bus:pci0000:00
USB0	  S4	 disabled  pci:0000:00:07.2
USB1	  S4	 disabled  pci:0000:00:07.3
UAR1	  S4	 disabled  pnp:00:08
```

```
user@server:~$ lspci
00:00.0 Host bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] System Controller (rev 13)
00:01.0 PCI bridge: Advanced Micro Devices [AMD] AMD-760 [IGD4-1P] AGP Bridge
00:07.0 ISA bridge: VIA Technologies, Inc. VT82C686 [Apollo Super South] (rev 40)
00:07.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:07.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 16)
00:07.4 SMBus: VIA Technologies, Inc. VT82C686 [Apollo Super ACPI] (rev 40)
00:09.0 VGA compatible controller: Matrox Graphics, Inc. MGA 1064SG [Mystique] (rev 03)
00:0a.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 74)
00:0c.0 Network controller: AVM Audiovisuelles MKTG & Computer System GmbH Fritz!PCI v2.0 ISDN (rev 01)
00:0d.0 RAID bus controller: Silicon Image, Inc. SiI 3114 [SATALink/SATARaid] Serial ATA Controller (rev 02)
00:0f.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:10.0 Mass storage controller: Promise Technology, Inc. PDC20265 (FastTrak100 Lite/Ultra100) (rev 02)
```

why is NIC "3Com Corporation 3c905C-TX/TX-M" not listed in /proc/acpi/wakeup?

```
ifconfig -a
eth1      Link encap:Ethernet  HWaddr 00:01:02:f0:e7:8c  
          inet addr:192.168.100.10  Bcast:192.168.100.255  Mask:255.255.255.0
          inet6 addr: fe80::201:2ff:fef0:e78c/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17007 errors:0 dropped:0 overruns:1 frame:0
          TX packets:9792 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:23237609 (22.1 MB)  TX bytes:773202 (755.0 KB)
          Interrupt:12 Base address:0xa000
```

```
user@server:~$ ethtool eth1
Settings for eth1:
Cannot get device settings: Operation not permitted
Cannot get wake-on-lan settings: Operation not permitted
	Current message level: 0x00000001 (1)
Cannot get link status: Operation not permitted
thomas@pc0-ubuntu:~$ sudo ethtool eth1
[sudo] password for thomas: 
Settings for eth1:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 24
	Transceiver: internal
	Auto-negotiation: on
	Current message level: 0x00000001 (1)
	Link detected: yes

```

I've added "3c59x global_enable_wol=1" to /etc/modprobe.d/network:
```
user@server:~$ cat /etc/modprobe.d/network 
options 3c59x global_enable_wol=1
```

```
user@server:~$ lsmod
Module                  Size  Used by
af_packet              23684  0 
nfsd                  228464  13 
auth_rpcgss            43424  1 nfsd
exportfs                6016  1 nfsd
ipv6                  272804  20 
nfs                   261900  0 
lockd                  67720  3 nfsd,nfs
nfs_acl                 4608  2 nfsd,nfs
sunrpc                185372  11 nfsd,auth_rpcgss,nfs,lockd,nfs_acl
iptable_filter          3840  0 
ip_tables              14820  1 iptable_filter
x_tables               16132  1 ip_tables
ac                      6916  0 
lp                     12324  0 
loop                   19076  0 
joydev                 12992  0 
serio_raw               7940  0 
psmouse                40208  0 
button                  9232  0 
hisax_fcpcipnp         12800  0 
hisax_isac              9108  1 hisax_fcpcipnp
hisax                 501760  2 hisax_fcpcipnp,hisax_isac
i2c_viapro              9876  0 
crc_ccitt               3072  1 hisax
i2c_core               24832  1 i2c_viapro
isdn                  139232  1 hisax
amd_k7_agp              9612  1 
parport_pc             36644  1 
parport                37704  2 lp,parport_pc
via686a                15244  0 
slhc                    7040  1 isdn
shpchp                 34452  0 
agpgart                34760  1 amd_k7_agp
pci_hotplug            30880  1 shpchp
evdev                  12928  5 
pcspkr                  4224  0 
ext3                  136584  11 
jbd                    48404  1 ext3
mbcache                 9600  1 ext3
sr_mod                 17828  0 
cdrom                  37280  1 sr_mod
ide_disk               17536  3 
pata_via               13316  0 
sg                     36496  0 
sd_mod                 30720  4 
usbhid                 32128  0 
hid                    38784  1 usbhid
ata_generic             8324  0 
8139cp                 25088  0 
floppy                 59332  0 
pdc202xx_old            8064  0 [permanent]
ide_core              114252  2 ide_disk,pdc202xx_old
sata_sil               12296  4 
pata_acpi               8320  0 
8139too                27776  0 
uhci_hcd               27152  0 
3c59x                  46248  0 
mii                     6400  3 8139cp,8139too,3c59x
libata                159344  4 pata_via,ata_generic,sata_sil,pata_acpi
scsi_mod              151180  4 sr_mod,sg,sd_mod,libata
usbcore               146028  3 usbhid,uhci_hcd
dm_mirror              24704  0 
dm_snapshot            19620  0 
dm_mod                 62532  21 dm_mirror,dm_snapshot
thermal                16796  0 
processor              37000  1 thermal
fan                     5636  0 
fbcon                  42656  0 
tileblit                3456  1 fbcon
font                    9472  1 fbcon
bitblit                 6784  1 fbcon
softcursor              3072  1 bitblit
fuse                   50580  1 
```

```
user@server:~$ lsmod | grep mii
mii                     6400  3 8139cp,8139too,3c59x
```


any ideas???

---

### Post by sammeme on 2009-01-22
I was also in your situation, but finally found the missing bits yesterday.

Two critical parts:


[LIST=1]
[*] Before halt module 3c59x needs to be removed and then reload

**Without it, the system will not respond to the wol packet**


[*] Use pci-config (sudo apt-get install nictools-pci) to put the nic into sleep mode

**This will force the system to supply the power to the card when it's switched off, very very important!!!**

You need to know the bus and device index for your nic. First you do a "lspci -nn" (without the quote) and looking for the line contains "3Com Corporation 3c905C-TX/TX-M [Tornado]". Here is a sample of mine
```
01:0c.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 78)
```

The 2 digit at the beginning of the line means the pci bus it's on, in my case 01, i.e. it's on pci bus 1. So write down that pci bus number you just found.

At the end of the line just before "(rev 78 )", there will be some strings looks like "[10b7:9200]" this is the vendor:model number which you also need to write it down.

Now you need to use pci-config to find out the device index of your nic. Issue 
```
sudo pci-config -B $BUS
```
where you need to replace $BUS by the one (digit) you wrote down previously, in my case it's 1. 
```

Device #1 at bus 1 device/function 7/0, 036e109e.
Device #2 at bus 1 device/function 7/1, 0878109e.
Device #3 at bus 1 device/function 8/0, 880014f1.
Device #4 at bus 1 device/function 8/2, 880214f1.
Device #5 at bus 1 device/function 12/0, 920010b7.

```
If you compare the above result at the end of the line with the model:vendor (please be aware the position between model and vendor has been switched for the output of pci-config) you written previously you will find the device index is 5 for my system , i.e. 920010b7 -> 10b7:9200.

Now you should have the command to execute just before halt,

```
pci-config -B $BUS -#$INDEX -S
```
where you need to replace $BUS and $INDEX by the bus number and device index you found out.

To put 1) and 2) together you should add the following line to /etc/init.d/halt just before "halt -d -f $netdown $poweroff $hddown"
```

rmmod 3c59x                   
sleep 0.5                     
modprobe 3c59x                        
sleep 0.5                             
pci-config -B $BUS -#$INDEX -S              
sleep 0.5

```
where you need to replace $BUS and $INDEX by the bus number and device index you found out.

[/LIST]

There are other stuff I have changed but not sure they are critical, but my system is working with them, so I will just list them for your reference
[LIST]
[*] Add the following to /etc/default/halt
```

NETDOWN=no

```
[*] Append the following to /etc/modprobe.d/options
```

options 3c59x enable_wol=1 global_enable_wol=1

```
[*] Update initramfs
```

update-initramfs -t -u -k 'uname -r'

```
[*] Use acpi in kernel (acpid was installed)
[/LIST]

After you have done all the changes shut down your machine by execute
```

sudo halt

```

If the light on your router which corresponding to the port connected to nic still on when the pc is switched off then there will be a good chance the wol will work, if not start it up and then shut it down by execute command "sudo halt" and try it again.

---

### Post by jakj on 2009-11-24
I'd like to confirm this works perfectly for me on the Dell Latitude C640 with this ethernet card. (Confirmed the problem still exists as of 9.10.)  I have no idea which package this bug should be applied against. The ethernet driver? The halt script? Modprobe? This solution seems to touch against so many subsystems.

---

### Post by rjcj99 on 2009-11-29
I can confirm the following are the steps for a one-time WOL from a fresh install of 8.04 LTS Server (motherboard: Asus P2bf, nic: 3c905b-tx):

sudo apt-get install nictools-pci
rmmod 3c59x
modprobe 3c59x enable_wol=1 global_enable_wol=1
pci-config -B $BUS -#$INDEX -S  (as described above)

No need to adjust halt script if the above is executed before shutdown.  As long as the above is executed, one could use a different shutdown command, like shutdown -h now.

---

### Post by JCarles on 2010-06-30
I can confirm what rjcj99 says. It works in s HP VL400 with the BIOS updated to IP.01.08 version, doesn't work with earlier BIOS version.
I add the following lines to /etc/init.d/halt just before "halt -d -f $netdown $poweroff $hddown"
 
rmmod 3c59x
sleep 0.5 
modprobe 3c59x enable_wol=1 global_enable_wol=1
sleep 0.5 
pci-config -B $BUS -#$INDEX -S (as described above)
sleep 0.5 
 
Now I can WOL my server, thanks a lot!

---

### Post by qseb on 2010-09-09
Thank you so much for this HOWTO !!!
I just registered to this board to post my config:

asus M3N78-VM for a home box server with integrated geforce 8200 NIC and a 3C905C-TX-M on external PCI with PCI rizer. Ubuntu 10.04 server.
I have been trying so many NIC in conjunction with the integrated NIC, that I was desesperate : Dlink DGE-528TX DGE-528T(4 different revisions) could not work properly from time integrated NIC was enabled. Because of IRQ APCI MSI bad combinations....

I finally tried a last card, a 3C905C-TX-M, and bingo thanks to this thread!!!!
I use sleepd to monitor activity, and pm-suspend to sleep to S3. To work with pm-suspend, I edited /etc/pm/sleep.d/3com with your nictools-pci commands.

Thank you again :KS

---

### Post by ItEndsWithTens on 2012-09-12
I'm not normally one to dig up old threads, but in this case I thought it was important to add my voice to the chorus that's had success with sammeme's technique. I can also confirm that this isn't limited to 3Com cards. As detailed at [http://ubuntuforums.org/showthread.php?t=2054623](http://ubuntuforums.org/showthread.php?t=2054623), I found that this approach was the only thing that worked for me using a CNet Pro200WL network adapter on an MSI K7T266Pro2 R2.0 motherboard.

To paraphrase what I wrote in the other thread, I modified the halt script as detailed here, but didn't need the NETDOWN=no change, the enable_wol or global_enable_wol options (which the dmfe driver, used by my card's Davicom chipset, doesn't recognize), or update-initramfs. I also noticed that the card has all its wakeup modes activated. I'm able to live with it since it's only physical activity and magic packet, but people using hardware that can wake on broadcast activity are in for what I suspect will seem like random boots of their system. I have yet to figure out how to choose only one wakeup mode, unfortunately, so if anyone out there has any insight I'm sure I'm not the only one who'd appreciate the advice.

I don't know if anyone who's participated in this thread over the years is still reading, but thank you all for the help, I was pulling my hair out before I found this solution!

---

### Post by nothingspecial on 2012-09-12
> **ItEndsWithTens said:**
> I'm not normally one to dig up old threads

Good, because I wont have to close them like this one.

---

