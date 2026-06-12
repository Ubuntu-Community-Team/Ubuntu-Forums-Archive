---
title: "Cisco aironet wireless card not working: last trial before giving up Ubuntu. HELP!"
date: 2007-05-22
forum: Networking &amp; Wireless
---

### Post by chiarchiaru on 2007-05-22
Dear Ubuntu masters,
I am completely new to linux and Ubuntu. I have an old T20 and a Cisco  Aironet AIR-PCM352 wireless card. I have installed ubuntu 7.04 on a partition and it looks very nice but, ](*,) I cannot get my wireless connection working!!
I have now tried for days with solutions given on other threads but no way... I am not 100% sure I have implemented the correct procedures as I have zero knowledge of Linux.
The card works with same machine under Windows. My wired connection works. I have a WEP encryption on my D-LINK router and a MAC filter.
I can see my network but I cannot connect. 
I hope some of you with experience find easily this problem that unfortunately makes not possible for me to enjoy Ubuntu and say goodbye to Windows.
I copy below some info here that I hope will be useful. 
Thanks in advance for those who will try to help.

sadministrator@mylaptop:~$ sudo lsmod | grep airo
Password:
airo_cs                 7168  1 
airo                   74400  1 airo_cs
pcmcia                 39212  1 airo_cs
pcmcia_core            40852  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic


administrator@mylaptop:~$ sudo iwlist eth1 scan
eth1      Scan completed :
          Cell 01 - Address: **:**:**:**:**:** ### modified by me to hide info ###
                    ESSID:"**MY WIRELESS NAME***"  ### modified by me to hide info ###
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=70/100  Signal level=-60 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 22 Mb/s
                    Extra:bcn_int=200

administrator@mylaptop:~$ sudo iwconfig eth1
eth1      IEEE 802.11-DS  ESSID:"**MY WIRELESS NAME***"  ### modified by me to hide info ###  
          Mode:Managed  Frequency:2.442 GHz  Access Point: **:**:**:**:**:** ### modified by me to hide info ###  
          Bit Rate:11 Mb/s   Tx-Power=17 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:****-****-** [4]   Security mode:open
          Power Management:off
          Link Quality=59/100  Signal level=-66 dBm  Noise level=-92 dBm
          Rx invalid nwid:18  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:4180   Missed beacon:0

administrator@mylaptop:~$ sudo lshw -businfo
Bus info        Device      Class          Description
======================================================
                            system         26474MG
                            bus            26474MG
                            memory         BIOS
cpu@0                       processor      Intel(R) Pentium(R) III Mobile CPU   
                            memory         L1 cache
                            memory         L2 cache
                            memory         System Memory
                            memory         SODIMM SDRAM Synchronous
                            memory         SODIMM SDRAM Synchronous
pci@00:00.0                 bridge         82830 830 Chipset Host Bridge
pci@00:01.0                 bridge         82830 830 Chipset AGP Bridge
pci@01:00.0                 display        SuperSavage IX/C SDR
pci@00:1d.0                 bus            82801CA/CAM USB (Hub #1)
usb@1           usb1        bus            UHCI Host Controller
pci@00:1d.1                 bus            82801CA/CAM USB (Hub #2)
usb@2           usb2        bus            UHCI Host Controller
pci@00:1d.2                 bus            82801CA/CAM USB (Hub #3)
usb@3           usb3        bus            UHCI Host Controller
pci@00:1e.0                 bridge         82801 Mobile PCI Bridge
pci@02:00.0                 bridge         PCI1420
                            network        Cisco Systems
pci@02:00.1                 bridge         PCI1420
pci@02:02.0                 communication  WinModem 56k
pci@02:08.0     eth0        network        82801CAM (ICH3) PRO/100 VE (LOM) Ethe
pci@00:1f.0                 bridge         82801CAM ISA Bridge (LPC)
pci@00:1f.1     scsi0       storage        82801CAM IDE U100
scsi@0:0.0.0    /dev/sda    disk           HITACHI_DK23CA-3
scsi@0:0.0.0,1  /dev/sda1   disk           W95 FAT32 (LBA) partition
scsi@0:0.0.0,2  /dev/sda2   disk           Linux filesystem partition
scsi@0:0.0.0,3  /dev/sda3   disk           Extended partition
                /dev/sda5   disk           Linux swap / Solaris partition
scsi@1:0.0.0    /dev/cdrom  disk           DVD-ROM SR-8176
                /dev/cdrom  disk           
pci@00:1f.3                 bus            82801CA/CAM SMBus Controller
pci@00:1f.5                 multimedia     82801CA/CAM AC'97 Audio Controller
                eth1        network        Wireless interface

administrator@mylaptop:~$ sudo iwlist eth1 key
Password:
eth1      2 key sizes : 40, 104bits
          4 keys available :
                [1]: ****-****-** (40 bits)
                [2]: ****-****-** (40 bits)
                [3]: ****-****-** (40 bits)
                [4]: ****-****-** (40 bits)
          Current Transmit Key: [4]
          Security mode:open

---

### Post by blazercist on 2007-05-22
is there any particular reason why you're attempting to do this from the command line when there is a GUI for it?

Administration > Network

Pick your ESSID from the drop down and enter your WEP key.

---

### Post by chiarchiaru on 2007-05-22
I have tried but it doesn't work from there or from the small Network Manager icon on the top of the screen. In this last one I can see my wireless network only if I set "Roaming mode enabled".
Any idea?

---

### Post by blazercist on 2007-05-22
try "sudo ifconfig eth1" and give me the output, also try to ping your router and let me know what happens.

---

### Post by chiarchiaru on 2007-05-22
Thanks for trying with my problem.
Ping the router gives no answer. I have tried both the WAN and the LAN address IP. With wired network OK

Here the result of the command:

administrator@mylaptop:~$ sudo ifconfig eth1
Password:
eth1      Link encap:Ethernet  HWaddr 00:07:85:92:6C:09  
          inet6 addr: fe80::207:85ff:fe92:6c09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:1823 errors:70980 dropped:0 overruns:0 frame:70980
          TX packets:850 errors:0 dropped:0 overruns:0 carrier:0
          collisions:71 txqueuelen:1000 
          RX bytes:144321 (140.9 KiB)  TX bytes:117607 (114.8 KiB)
          Interrupt:3 Base address:0x2100

---

### Post by blazercist on 2007-05-23
try turning off WEP see what happens

---

### Post by chiarchiaru on 2007-05-23
It is working without WEP. I had to connect with Manual Configuration in Network Manager, which otherwise was not conecting automatically just clicking on the available network.  Ping router is ok. Any idea to make it working with WEP?

Here the new situation:
administrator@mylaptop:~$ sudo ifconfig eth1
eth1      Link encap:Ethernet  HWaddr 00:07:85:92:6C:09  
          inet addr:192.168.1.5  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::207:85ff:fe92:6c09/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:697 errors:1526 dropped:0 overruns:0 frame:1526
          TX packets:527 errors:19 dropped:0 overruns:4 carrier:15
          collisions:6 txqueuelen:1000 
          RX bytes:699767 (683.3 KiB)  TX bytes:54732 (53.4 KiB)
          Interrupt:3 Base address:0x2100

---

### Post by chiarchiaru on 2007-05-24
One additiona hopefully important information: when I reactivate WEP on my wireless router, a message says that SSID support will be disabled when activating the encription. Can this be the reason of the problem???

---

### Post by arm-c on 2007-09-28
Well,  First I would like to thank the person who started this thread, as the information provided by him, while not the solution, was the piece of information that lead to me solving my own problems with the Cisco Aironet 352 card.

I saw the output they indicated from iwlist.  the output threw a flag up for me, as it indicated that two of the encryption key fields were populated and that field 4 was being used.  Running the 'iwlist' command from my computer also yielded the same problems.

For me, the solution was to run:

iwconfig eth1 key [1]

This command sets the key field in use to field ONE.  Once I did that, I dropped over to Wifi-radar (I am using Xubuntu with that card - so NW-Manager isn't installed).  Clicked configure the connection, entered my key and off I went.

I decided to come back here to post this in hopes that it will help others as they work to resolve their problems with this card.

:)

---

### Post by G2_vincent on 2008-02-24
hi
it is likely that your AP is using WPA, and the MP350 can't.
try to configure it to use WEP

---

