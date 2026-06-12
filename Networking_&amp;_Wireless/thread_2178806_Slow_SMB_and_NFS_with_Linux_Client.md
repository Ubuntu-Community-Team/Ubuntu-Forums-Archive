---
title: "Slow SMB and NFS with Linux Client"
date: 2013-10-05
forum: Networking &amp; Wireless
---

### Post by Tos_Phoenix on 2013-10-05
Hi!

I've a really annoying problem, which i was unable to figure out over the last..i don't know, months..

First, i have an Ubuntu Server 13.04 Installation on my Home Server. I use SMB and NFS to share folders in my Network.
Some time ago i noticied slow Transfer Speeds (about 2-3Mb/s) on my Laptop using Kubuntu 13.04. At first i thought of poor wifi support for my Intel card, but i also noticed considerable slow performance when connected via cable. The problem hower does NOT exist when using Windows.
What's also interesting, using FTP i get normal Performance (~80MB/s over LAN and ~14Mb/s over Wifi).

What i've tried so far:
- I read some posts using various socket options (TCP_NODELAY, SO_RCVBUF, etc) but none of these helped
- I tried other Linux Distributions (Arch, Suse,...) on my laptop with other Kernels back to 3.2, but this didn't help eather
- Since i read something about poor support for Realtek network cards i bought an Intel card for the server: no effect
- Used several mounting options mentioned, but with no effect

A few thoughts:

- It can't be a problem with the raid, since i'm getting pretty decent transfer speeds with windows and FTP?
- Therefor the network configuration should also be ok?
- I can't go back to more older kernels, since the hardware is rather new..

I'm not sure what can be of help, so i'm posting standard stuff which could be interesting. If you need more information, please don't hesitate to ask.
I'm also not really sure where the problem might be (Laptop, Server, Network, Hardware, Software, etc).

Any help is appreciated.

Thanks

Server

lspci
```

00:00.0 Host bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor DRAM Controller (rev 09)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.4 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 5 (rev c4)
00:1c.6 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation Z77 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series/C210 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Intel Corporation 82574L Gigabit Network Connection
03:00.0 SATA controller: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
03:00.1 IDE interface: JMicron Technology Corp. JMB363 SATA/IDE Controller (rev 03)
04:00.0 PCI bridge: ASMedia Technology Inc. ASM1083/1085 PCIe to PCI Bridge (rev 03)

```

cat /proc/mdstat

```
md3 : active raid5 sdc1[3] sdd1[0] sda1[4] sdb1[1]      5860535808 blocks super 1.2 level 5, 512k chunk, algorithm 2 [4/4] [UUUU]
      
unused devices: <none>

```

cat /proc/version

```

Linux version 3.8.0-31-generic (buildd@panlong) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013

```

ethtool eth0

```
Settings for eth0:        Supported ports: [ TP ]
        Supported link modes:   10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Supported pause frame use: No
        Supports auto-negotiation: Yes
        Advertised link modes:  10baseT/Half 10baseT/Full 
                                100baseT/Half 100baseT/Full 
                                1000baseT/Full 
        Advertised pause frame use: No
        Advertised auto-negotiation: Yes
        Speed: 1000Mb/s
        Duplex: Full
        Port: Twisted Pair
        PHYAD: 1
        Transceiver: internal
        Auto-negotiation: on
        MDI-X: off
        Supports Wake-on: pumbg
        Wake-on: g
        Current message level: 0x00000007 (7)
                               drv probe link
        Link detected: yes

```

samba is configured with the standard configuration and just one share at the moment

```

[Series]
        path = /raid5/Series
        browseable = yes
        writeable = no
        guest ok = yes

```

Laptop:

lspci

```

00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Core Processor PCI Express x16 Root Port (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:19.0 Ethernet controller: Intel Corporation 82577LM Gigabit Network Connection (rev 06)
00:1a.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 06)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 06)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 06)
00:1c.3 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 (rev 06)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 06)
00:1d.0 USB controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 06)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a6)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 06)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 06)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 06)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 06)
01:00.0 VGA compatible controller: NVIDIA Corporation GT218M [NVS 3100M] (rev ff)
03:00.0 Network controller: Intel Corporation Centrino Ultimate-N 6300 (rev 35)
05:00.0 USB controller: Fresco Logic FL1000G USB 3.0 Host Controller (rev 01)
0d:00.0 SD Host controller: Ricoh Co Ltd MMC/SD Host Controller (rev 01)
0d:00.1 System peripheral: Ricoh Co Ltd R5U2xx (R5U230 / R5U231 / R5U241) [Memory Stick Host Controller] (rev 01)
ff:00.0 Host bridge: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers (rev 02)
ff:00.1 Host bridge: Intel Corporation Core Processor QuickPath Architecture System Address Decoder (rev 02)
ff:02.0 Host bridge: Intel Corporation Core Processor QPI Link 0 (rev 02)
ff:02.1 Host bridge: Intel Corporation Core Processor QPI Physical 0 (rev 02)
ff:02.2 Host bridge: Intel Corporation Core Processor Reserved (rev 02)
ff:02.3 Host bridge: Intel Corporation Core Processor Reserved (rev 02)

```

cat /proc/version

```

Linux version 3.8.0-31-generic (buildd@panlong) (gcc version 4.7.3 (Ubuntu/Linaro 4.7.3-1ubuntu1) ) #46-Ubuntu SMP Tue Sep 10 20:03:44 UTC 2013

```

All data is transferred via a Linksys E4200 Router/Switch with DD-WRT with build 20888 installed

---

### Post by SeijiSensei on 2013-10-05
I can't help with Samba, but adding "async" to the options defined for the share in the NFS server's /etc/exports file made a big difference for me.  It exposes you to the possibility for file corruption during writes if the server crashes, but mine is on a UPS and has run reliably 24/7 for years now.  Increasing the rsize and wsize parameters in the options used on the client also helps.  I generally set them to 32768 for wifi connections, and 65536 for wired ones.

---

### Post by Tos_Phoenix on 2013-10-06
Sadly that didn't help much.
I already had the async option on the server and tried wsize/rsize from 8192 to 65536, but i never got more then 3,5Mb/s..

---

### Post by erling@eph.dk on 2013-10-19
I have a similar isue.
My lan setup:
1 fileserver ubuntu server 12.04 samba "5 shares 6 users".
1 old laptop ibm thinkpad wifi multiboot win7 / Kubuntu 12.04
1 "new" laptop Packard bell wifi or wired multiboot win7 / kubuntu 12.04
1 tower desktop "homebrew" wired kubuntu 12.04
1 wifi router bgn mixed mode

Samba performance:
When using windovs I get fine performance both up /down to from server all shares.
No matter what machine no matter if it is wired or wifi.
When i use kubuntu i get fine performance downloading from server to any client.
But when I am uploading to server it won't go over 2.5 MB/s

sftp performance:
In the top on any device in any direction.

ftp performance:
proftpd
in the top on any device in any direction

I have spendt to days googling for a solution.
Tried several solutions inclusive changing hardware on the server.
Nothing seems to do the magic..
;)

the day is full of questions. I don't have all the answers.
/erling

[LIST]
[*] 	 		 			:wink: 		
 	
[/LIST]

---

### Post by Tos_Phoenix on 2013-11-08
Ok it seems i have found the issue.

My "problem" was, that i have only tested distributions with KDE and no other desktop environments..otherwise i had found this problem probably sooner.
Nevertheless, the problem lies within KDE, more especially the kio slave. Here is a bug report: [https://bugs.kde.org/show_bug.cgi?id=291835](https://bugs.kde.org/show_bug.cgi?id=291835)

Mounting the samba folders via cifs or copying files with smbclient works as expected.
This problem was really driving me nuts the last few months, but now i have at least a workaround

---

