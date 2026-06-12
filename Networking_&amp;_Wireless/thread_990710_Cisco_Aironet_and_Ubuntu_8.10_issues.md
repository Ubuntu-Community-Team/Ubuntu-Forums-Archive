---
title: "Cisco Aironet and Ubuntu 8.10 issues"
date: 2008-11-23
forum: Networking &amp; Wireless
---

### Post by somu76 on 2008-11-23
Hi,
  I seem to have two problems. I just installed Ubuntu 8.10 today, and saw that I couldn't get my wireless to work, and realized:

1) I am not sure if my wireless card is being recognized.
2) I can't get the Network Manager Applet to show up...

for the first problem, I tried a number of things, documented below..so, if anyone can look at it and let me know if my card is even being accepted or not, I would appreciate it.

```
Machine : IBM Thinkpad T21

somu@somu-ubuntu:~$ lsb_release -d
Description:	Ubuntu 8.10
somu@somu-ubuntu:~$ uname -mr
2.6.27-7-generic i686



somu@somu-ubuntu:~$ sudo lspci
[sudo] password for somu: 
00:00.0 Host bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX Host bridge (rev 03)
00:01.0 PCI bridge: Intel Corporation 440BX/ZX/DX - 82443BX/ZX/DX AGP bridge (rev 03)
00:02.0 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:02.1 CardBus bridge: Texas Instruments PCI1450 (rev 03)
00:03.0 Ethernet controller: Intel Corporation 82557/8/9/0/1 Ethernet Pro 100 (rev 09)
00:03.1 Serial controller: Xircom Mini-PCI V.90 56k Modem
00:05.0 Multimedia audio controller: Cirrus Logic CS 4614/22/24/30 [CrystalClear SoundFusion Audio Accelerator] (rev 01)
00:07.0 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ISA (rev 02)
00:07.1 IDE interface: Intel Corporation 82371AB/EB/MB PIIX4 IDE (rev 01)
00:07.2 USB Controller: Intel Corporation 82371AB/EB/MB PIIX4 USB (rev 01)
00:07.3 Bridge: Intel Corporation 82371AB/EB/MB PIIX4 ACPI (rev 03)
01:00.0 VGA compatible controller: S3 Inc. 86C270-294 Savage/IX-MV (rev 13)

somu@somu-ubuntu:~$ sudo lsusb
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub

somu@somu-ubuntu:~$ sudo lspcmcia -v
Socket 0 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:02.0)
	Configuration:	state: on	ready: yes
Socket 1 Bridge:   	[yenta_cardbus] 	(bus ID: 0000:00:02.1)
	Configuration:	state: on	ready: yes
			Voltage: 5.0V Vcc: 5.0V Vpp: 5.0V
Socket 1 Device 0:	[airo_cs]		(bus ID: 1.0)
	Configuration:	state: on
	Product Name:   Aironet PC4800 
	Identification:	manf_id: 0x015f	card_id: 0x0007
			function: 6 (network)
			prod_id(1): "Aironet" (0x207bb848)
			prod_id(2): "PC4800" (0xbf73f7ef)
			prod_id(3): --- (---)
			prod_id(4): --- (---)


Wireless is not showing up in the output of lspci, but it is in pcmcia, so dumped out the verbose version of that.


somu@somu-ubuntu:~$ sudo ifconfig
[sudo] password for somu: 
eth0      Link encap:Ethernet  HWaddr 00:10:a4:78:1f:ff  
          inet addr:10.10.10.115  Bcast:10.10.10.255  Mask:255.255.255.0
          inet6 addr: fe80::210:a4ff:fe78:1fff/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11403 errors:0 dropped:0 overruns:0 frame:0
          TX packets:7097 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:10725998 (10.7 MB)  TX bytes:939435 (939.4 KB)

eth1      Link encap:Ethernet  HWaddr 00:40:96:28:e6:7a  
          inet6 addr: fe80::240:96ff:fe28:e67a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:8949 dropped:0 overruns:0 frame:8949
          TX packets:3 errors:3 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:990 (990.0 B)
          Interrupt:3 Base address:0x100 

eth1:avahi Link encap:Ethernet  HWaddr 00:40:96:28:e6:7a  
          inet addr:169.254.7.223  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:3 Base address:0x100 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:4240 (4.2 KB)  TX bytes:4240 (4.2 KB)


somu@somu-ubuntu:~$ sudo lshw -C network
  *-network               
       description: Aironet
       physical id: 0
       version: PC4800
       slot: Socket 1
       resources: irq:3
  *-network
       description: Ethernet interface
       product: 82557/8/9/0/1 Ethernet Pro 100
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:00:03.0
       logical name: eth0
       version: 09
       serial: 00:10:a4:78:1f:ff
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.23-k4-NAPI duplex=full firmware=N/A ip=10.10.10.115 latency=66 link=yes maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=100MB/s
  *-network:0
       description: Wireless interface
       physical id: 1
       logical name: eth1
       serial: 00:40:96:28:e6:7a
       capabilities: ethernet physical wireless
       configuration: broadcast=yes multicast=yes wireless=IEEE 802.11-DS
  *-network:1 DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 3e:89:e7:b2:e1:e0
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes



somu@somu-ubuntu:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

irda0     Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:13:10:33:69:E4
                    ESSID:"ssomunet"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-40 dBm  Noise level:-103 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:11:50:29:4E:F9
                    ESSID:"KitKat&Rocks"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/100  Signal level=-82 dBm  Noise level:-103 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:16:B6:AF:4E:82
                    ESSID:"Dalpaa"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality=15/100  Signal level=-88 dBm  Noise level:-103 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

wifi0     Scan completed :
          Cell 01 - Address: 00:13:10:33:69:E4
                    ESSID:"ssomunet"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=100/100  Signal level=-40 dBm  Noise level:-103 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100
          Cell 02 - Address: 00:11:50:29:4E:F9
                    ESSID:"KitKat&Rocks"
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Quality=28/100  Signal level=-82 dBm  Noise level:-103 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s
                    Extra:bcn_int=100
          Cell 03 - Address: 00:16:B6:AF:4E:82
                    ESSID:"Dalpaa"
                    Mode:Master
                    Frequency:2.457 GHz (Channel 10)
                    Quality=15/100  Signal level=-88 dBm  Noise level:-103 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s
                    Extra:bcn_int=100

pan0      Interface doesn't support scanning.


somu@somu-ubuntu:~$ sudo iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

eth1      IEEE 802.11-DS  ESSID:"tsunami"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=-103 dBm  Noise level=-103 dBm
          Rx invalid nwid:32483  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24191   Missed beacon:0

wifi0     IEEE 802.11-DS  ESSID:"tsunami"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Invalid   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:off
          Power Management:off
          Link Quality=0/100  Signal level=-103 dBm  Noise level=-103 dBm
          Rx invalid nwid:32483  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:24191   Missed beacon:0

pan0      no wireless extensions.



somu@somu-ubuntu:~$ lsmod | grep airo
airo_cs                12416  1 
airo                   77088  1 airo_cs
pcmcia                 43052  1 airo_cs
pcmcia_core            43412  4 airo_cs,pcmcia,yenta_socket,rsrc_nonstatic


somu@somu-ubuntu:~$ dmesg | grep airo
[   35.866164] airo(): Probing for PCI adapters
[   35.869585] airo(): Finished probing for PCI adapters
[   37.186921] airo(): cmd:111 status:7f11 rsp0:2 rsp1:0 rsp2:0
[   37.186938] airo(): Doing fast bap_reads
[   37.455313] airo(): WPA unsupported (only firmware versions 5.30.17 and greater support WPA.  Detected 4.25.23)
[   37.459360] airo(eth1): MAC enabled 00:40:96:28:e6:7a


The following lines are added to the /etc/modprobe.d/blacklist file

#these aes modules break the airo driver
blacklist padlock_aes
blacklist geode_aes


somu@somu-ubuntu:~$ sudo ifconfig eth1 down
somu@somu-ubuntu:~$ sudo dhclient -r eth1
There is already a pid file /var/run/dhclient.pid with pid 6295
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:40:96:28:e6:7a
Sending on   LPF/eth1/00:40:96:28:e6:7a
Sending on   Socket/fallback
somu@somu-ubuntu:~$ sudo ifconfig eth1 up
somu@somu-ubuntu:~$ sudo iwconfig eth1 essid "ssomunet"
somu@somu-ubuntu:~$ sudo iwconfig eth1 key 666C7DF8A230A6E54D003DE975
somu@somu-ubuntu:~$ sudo iwconfig eth1 channel 6
somu@somu-ubuntu:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801

wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:40:96:28:e6:7a
Sending on   LPF/eth1/00:40:96:28:e6:7a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 15
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 19
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 4
No DHCPOFFERS received.
No working leases in persistent database - sleeping.

somu@somu-ubuntu:~$ sudo iwconfig eth1
eth1      IEEE 802.11-DS  ESSID:"ssomunet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:33:69:E4   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-** [4]   Security mode:open
          Power Management:off
          Link Quality=43/100  Signal level=-74 dBm  Noise level=-98 dBm
          Rx invalid nwid:32580  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:4  Invalid misc:24474   Missed beacon:0

somu@somu-ubuntu:~$ sudo iwconfig eth1 key [1]

somu@somu-ubuntu:~$ sudo iwconfig eth1
eth1      IEEE 802.11-DS  ESSID:"ssomunet"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:13:10:33:69:E4   
          Bit Rate:11 Mb/s   Tx-Power=15 dBm   Sensitivity=0/65535  
          Retry limit:16   RTS thr:off   Fragment thr:off
          Encryption key:****-****-****-****-****-****-**   Security mode:open
          Power Management:off
          Link Quality=54/100  Signal level=-68 dBm  Noise level=-98 dBm
          Rx invalid nwid:32580  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:11  Invalid misc:24514   Missed beacon:0


somu@somu-ubuntu:~$ sudo dhclient eth1
Internet Systems Consortium DHCP Client V3.1.1
Copyright 2004-2008 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

wifi0: unknown hardware address type 801
wifi0: unknown hardware address type 801
Listening on LPF/eth1/00:40:96:28:e6:7a
Sending on   LPF/eth1/00:40:96:28:e6:7a
Sending on   Socket/fallback
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 6
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 21
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 17
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 10
DHCPDISCOVER on eth1 to 255.255.255.255 port 67 interval 1
No DHCPOFFERS received.
No working leases in persistent database - sleeping.



```



For the second problem, I tried reinstalling the applet with no luck... I also tried to start it manually and got the following error::

```
somu@somu-ubuntu:~$ sudo nm-applet --sm-disable

** (nm-applet:7133): WARNING **: <WARN>  applet_dbus_manager_start_service(): Could not acquire the NetworkManagerUserSettings service as it is already taken.  Return: 3


(nm-applet:7133): GLib-GObject-CRITICAL **: g_object_unref: assertion `G_IS_OBJECT (object)' failed

```



any insight into this is much appreciated. Also, if anyone knows or has the latest firmware for my card (PC4800), that would be much appreciated.. Cisco's site seems to have just the windows drivers.. 

Thanks,
somu.

---

### Post by Olivier2371 on 2008-11-23
If your are looking for a driver look at this website.

[http://linuxwireless.org/en/users/Devices]("http://linuxwireless.org/en/users/Devices")

---

### Post by somu76 on 2008-11-23
Nope, that site didn't seem to have this device listed...

---

### Post by Olivier2371 on 2008-11-23
What device are you talking about?

the device name maybe pc4800 but what is the chipset?

---

### Post by somu76 on 2008-11-23
It is the Cisco Aironet card. Class PC 4800, Model PC4820B (the one that enables WEP functionality)

More info from my machine:
```
somu@somu-ubuntu:~$ cat /proc/driver/aironet/eth1/Status
Status: CFG ACT SYN LNK PRIV KEY WEP 
Mode: 3bf
Signal Strength: 48
Signal Quality: 7
SSID: ssomunet
AP: 
Freq: 0
BitRate: 11mbs
Driver Version: airo.c 0.6 (Ben Reed & Javier Achirica)
Device: PC4800B
Manufacturer: Aironet Wireless Communications
Firmware Version: 4.25.23
Radio type: 2
Country: 0
Hardware Version: 10
Software Version: 425
Software Subversion: 17
Boot block version: 132

```

Thanks,

---

### Post by Olivier2371 on 2008-11-23
I will try to explain myself.

If you don't have Device Manager installed, install it.

Applications->Add/Remove->search for Device Manager and install it.

Applications->System Tools-> Device Manager

Then look in the device manager(see picture)

[ATTACH]93850[/ATTACH]

Under View in the menu click Display Properties
You should know be able to see the chipset of your wireless adapter.

Hope this helps

---

### Post by somu76 on 2008-11-23
here is what I have in there:

---

### Post by Olivier2371 on 2008-11-23
Instead of using 8.10 have you tried first on 8.04?

---

### Post by somu76 on 2008-11-23
yeah, this whole saga began with Hardy (8.04)... I thought 8.10 would fix it, and for a minute, I thought it did... If I remove everything from the interfaces file except the defaults, I seem to get back the network manager, but it can't connect to my wireless router using WEP... it keeps prompting me for the key even though I entered it... I then tried connecting manually using iwconfig, but no dice.. so, i modified the interfaces file and entered the essid manually in there, but upon a restart, the network manager vanished again (the process is running, but I can't get the UI to come up)... and the connection status is not changing... 

I think I need to go back to WinXP instead of dealing with this... have spent about 2 days on this, with no progress and have been looking all over the forums too....

---

### Post by Olivier2371 on 2008-11-23
Aironet ARLAN 4500, 4800, Cisco 340 and Cisco 350 series.

Did you know that cisco has produced driver for your wireless.

I cannot access it because you need to be registered to access the data.

I am still looking through the net to see if i can dig up something for you.

Check also this link:

[http://www.goonda.org/archive/wireless/aironet/]("http://www.goonda.org/archive/wireless/aironet/")

---

### Post by somu76 on 2008-11-23
yeah.. already saw that site, and visited Cisco, registered with them, and tried to find the drivers... unfortunately, Cisco had changed their site from the description available at a number of sites, and the only drivers I could find were for Windows... no Linux drivers on their site for the Aironet stuff... sent them and email about it, and got a reply that to open a request, I need to have a contract with them :(... 

not sure if I am having problems because I don't have the driver, or if something is incompatible here.. but from what I have been reading, these cards should work out of the box for this version of Ubuntu...

---

### Post by Olivier2371 on 2008-11-23
Do you see the network icon, in the bar?

If you do try to click left and tell me what you see.

---

### Post by somu76 on 2008-11-23
As I said earlier, I see it when I remove everything from my interfaces file and keep just the settings for iface lo. I don't see it otherwise.. When I see it, it shows up connected to my wired connection, and gave me the list of wireless networks to connect to.. I chose mine and it kept prompting me for the security key inspite of me entering my WEP key multiple times...

---

### Post by Olivier2371 on 2008-11-23
Have you tried another type of security like WPA/personal TKIP?

Or without security at all.

If you change security make your router setup reflect the security type that you trying to use

---

### Post by somu76 on 2008-11-29
was out of the country, so couldn't reply sooner on this... yeah, tried to use wireless without any security, but the same result... also tried with my neighbors wireless (it is unencrypted all the time), with no luck... as far as WPA, it says that WPA is not supported unless I use the latest firmware for this card... so, didn't try it.. I don't think it will work, if it doesn't work without encryption anyways... 

any more ideas? :(

---

### Post by somu76 on 2008-11-30
can anyone help here? seems like I have everything lined up properly here... the pccardctl command is showing the proper airo_cs driver loaded for the card, and the fact that it can see my wireless network, and others tell me that it is functioning (atleast at a basic level). However, I am not able to connect to my network that is using WEP.. I even tried to remove the security requirement, or use a neighbors wireless network that didn't have security, and it still failed... is there a way to debug this? I event removed Network Manager, and installed WICD, since some threads on the net were mentioning that to be more efficient at connecting to wireless networks, and this didn't help either.... 

any help is much appreciated here..

---

