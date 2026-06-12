---
title: "Wifi Password"
date: 2008-07-14
forum: Networking &amp; Wireless
---

### Post by neon100 on 2008-07-14
i am using ubuntu 8.04

problem is that i use a secured Wifi network. Whenever i save the password on my PC it works fine. But whenever i reboot, The password changes automatically to some very long combination of letters and numbers. And thus i have to enter password again and again in network settings and wireless network settings. Only then it starts working again.

Is this some bug?

---

### Post by neon100 on 2008-07-14
should i assume that no one knows the answer?

---

### Post by nickdbliss on 2008-07-14
Not really. Which encryption method u are using? SOmetimes there is a problem with network manager itself. Which driver? Ndiswrapper ? which wireless adapter?

---

### Post by neon100 on 2008-07-14
do you mean the security method? its 'WPA Personal'
what do you mean by encription?

---

### Post by nickdbliss on 2008-07-14
> **neon100 said:**
> do you mean the security method? its 'WPA Personal'
what do you mean by encription?

yeah i meant that. 
Go to terminal and type this
wpa_passphrase <Your SSID> <Yourpassword>
Example:
wpa_passphrase Home Mypassword
network={
	ssid="Home"
	#psk="Mypassword"
	psk=c123a4d958658e4fc252bbd95261fca24329f36791d0ccf9a0b3bc6025e0e692
}
Copy what is next to psk. Example: c123a4d958658e4fc252bbd95261fca24329f36791d0ccf9a0b3bc6025e0e692

Put that when it asks for ur password. Retry if fails. hope that helps. If not give the output of this command
cat /etc/network/interfaces
and
cat /etc/wpa_supplicant.conf

Also give output of these commands:
lspci
iwlist scan
ifconfig

Thanks

---

### Post by bacalao21 on 2008-07-15
hi nickdbliss, 
Sorry to cut in, I'm new to ubuntu, and I'm having the same problem. I can show you what my outputs were; note that iwlist scan shows that I can't scan.

**lspci**
00:00.0 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.0 ISA bridge: nVidia Corporation MCP67 ISA Bridge (rev a2)
00:01.1 SMBus: nVidia Corporation MCP67 SMBus (rev a2)
00:01.2 RAM memory: nVidia Corporation MCP67 Memory Controller (rev a2)
00:01.3 Co-processor: nVidia Corporation MCP67 Co-processor (rev a2)
00:02.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:02.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:04.0 USB Controller: nVidia Corporation MCP67 OHCI USB 1.1 Controller (rev a2)
00:04.1 USB Controller: nVidia Corporation MCP67 EHCI USB 2.0 Controller (rev a2)
00:06.0 IDE interface: nVidia Corporation MCP67 IDE Controller (rev a1)
00:07.0 Audio device: nVidia Corporation MCP67 High Definition Audio (rev a1)
00:08.0 PCI bridge: nVidia Corporation MCP67 PCI Bridge (rev a2)
00:09.0 IDE interface: nVidia Corporation MCP67 AHCI Controller (rev a2)
00:0a.0 Ethernet controller: nVidia Corporation MCP67 Ethernet (rev a2)
00:0c.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:0d.0 PCI bridge: nVidia Corporation MCP67 PCI Express Bridge (rev a2)
00:12.0 VGA compatible controller: nVidia Corporation GeForce 7150M (rev a2)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:09.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
01:09.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
01:09.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
01:09.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
01:09.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
04:00.0 Network controller: Broadcom Corporation BCM4310 USB Controller (rev 01)

 **iwlist scan**
lo        Interface doesn't support scanning.

eth1      Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

**ifconfig**
eth0      Link encap:Ethernet  HWaddr 00:1d:72:42:56:f2  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:252 Base address:0x6000 

eth1      Link encap:Ethernet  HWaddr 00:1a:73:d6:94:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:21472 errors:0 dropped:0 overruns:0 frame:749759
          TX packets:5690 errors:12 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6278316 (5.9 MB)  TX bytes:961004 (938.4 KB)
          Interrupt:19 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:179 errors:0 dropped:0 overruns:0 frame:0
          TX packets:179 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9256 (9.0 KB)  TX bytes:9256 (9.0 KB)

**cat /etc/wpa_supplicant.conf**
ap_scan=1
ctrl_interface=/var/run/wpa_supplicant 

network={
        ssid="router"
        scan_ssid=0
        proto=WPA
        key_mgmt=WPA-PSK
        psk="globalobserver"
        pairwise=TKIP
        group=TKIP
}
[B]
cat /etc/network/interfaces[/B]
auto lo
iface lo inet loopback

This is my first post, the only major issue I've had is not being able to connect to the WPA-PSK network and relying on the hardwire. If this post takes up way too much space I'll delete it. Thanks in advance if you can help out.

---

### Post by nickdbliss on 2008-07-15
> **bacalao21 said:**
> 
This is my first post, the only major issue I've had is not being able to connect to the WPA-PSK network and relying on the hardwire.

Are you using USB wireless adapter? your iwlist scan shows it is unable to see any network.

---

### Post by neon100 on 2008-07-15
jj@The-Laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 10.2.3.54
netmask 255.255.255.0
gateway 10.2.3.1





































iface eth1 inet dhcp
wpa-psk 5743d4f6356ce0bc4e6a9d437540bf588fff21ba5be22ddf1ad538c606b6bf1a
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid ZyXEL





auto eth1
jj@The-Laptop:~$ cat /etc/wpa_supplicant.conf
cat: /etc/wpa_supplicant.conf: No such file or directory
jj@The-Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV41.9 [GeForce Go 6800 Ultra] (rev a2)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
jj@The-Laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:02:CF:7C:F4:C7
                    ESSID:"ZyXEL"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=79/100  Signal level=-50 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1516ms ago

jj@The-Laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:78:44:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:83:45:15  
          inet addr:192.168.1.36  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe83:4515/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:558 errors:16 dropped:16 overruns:0 frame:0
          TX packets:487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:578135 (564.5 KB)  TX bytes:119406 (116.6 KB)
          Interrupt:18 Memory:dcfef000-dcfeffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74879 (73.1 KB)  TX bytes:74879 (73.1 KB)

jj@The-Laptop:~$

---

### Post by neon100 on 2008-07-15
jj@The-Laptop:~$ cat /etc/network/interfaces
auto lo
iface lo inet loopback


iface eth0 inet static
address 10.2.3.54
netmask 255.255.255.0
gateway 10.2.3.1





































iface eth1 inet dhcp
wpa-psk 5743d4f6356ce0bc4e6a9d437540bf588fff21ba5be22ddf1ad538c606b6bf1a
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid ZyXEL





auto eth1
jj@The-Laptop:~$ cat /etc/wpa_supplicant.conf
cat: /etc/wpa_supplicant.conf: No such file or directory
jj@The-Laptop:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 915GM/PM/GMS/910GML Express Processor to DRAM Controller (rev 03)
00:01.0 PCI bridge: Intel Corporation Mobile 915GM/PM Express PCI Express Root Port (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #3 (rev 03)
00:1d.3 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB UHCI #4 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) USB2 EHCI Controller (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev d3)
00:1e.2 Multimedia audio controller: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Audio Controller (rev 03)
00:1e.3 Modem: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) AC'97 Modem Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation 82801FBM (ICH6M) LPC Interface Bridge (rev 03)
00:1f.2 IDE interface: Intel Corporation 82801FBM (ICH6M) SATA Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) SMBus Controller (rev 03)
01:00.0 VGA compatible controller: nVidia Corporation NV41.9 [GeForce Go 6800 Ultra] (rev a2)
03:00.0 Ethernet controller: Broadcom Corporation NetXtreme BCM5705M_2 Gigabit Ethernet (rev 03)
03:01.0 CardBus bridge: Ricoh Co Ltd RL5c476 II (rev b3)
03:01.1 FireWire (IEEE 1394): Ricoh Co Ltd R5C552 IEEE 1394 Controller (rev 08)
03:01.2 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 17)
03:03.0 Network controller: Intel Corporation PRO/Wireless 2915ABG Network Connection (rev 05)
jj@The-Laptop:~$ iwlist scan
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

eth1      Scan completed :
          Cell 01 - Address: 00:02:CF:7C:F4:C7
                    ESSID:"ZyXEL"
                    Protocol:IEEE 802.11bg
                    Mode:Master
                    Frequency:2.437 GHz (Channel 6)
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 6 Mb/s; 9 Mb/s
                              11 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Quality=79/100  Signal level=-50 dBm  
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Extra: Last beacon: 1516ms ago

jj@The-Laptop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:11:43:78:44:28  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:19 

eth1      Link encap:Ethernet  HWaddr 00:12:f0:83:45:15  
          inet addr:192.168.1.36  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::212:f0ff:fe83:4515/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:558 errors:16 dropped:16 overruns:0 frame:0
          TX packets:487 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:578135 (564.5 KB)  TX bytes:119406 (116.6 KB)
          Interrupt:18 Memory:dcfef000-dcfeffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1422 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1422 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:74879 (73.1 KB)  TX bytes:74879 (73.1 KB)

jj@The-Laptop:~$

---

### Post by neon100 on 2008-07-15
first post is when i changed the password as per your instructions and WiFi stopped working.

and second post is when i changed the password to original password and WiFi started working.

can't i write it permanenetly somewhere in configuration?

---

### Post by bacalao21 on 2008-07-15
> **nickdbliss said:**
> Are you using USB wireless adapter? your iwlist scan shows it is unable to see any network.

No, I have a broadcom 4310 (rev 01) wireless on laptop. I can only connect to unsecured networks.

---

### Post by neon100 on 2008-07-17
This forum used to be so active. Where are those techies?

---

### Post by bacalao21 on 2008-07-17
> **neon100 said:**
> This forum used to be so active. Where are those techies?

Maybe we have to trade-in our computers?...  haha  
I was using an unsecured network for awhile and just last night, the dude put a password on the network.. I'm SOL.

---

### Post by nickdbliss on 2008-07-17
Sorry guys as far as i am concerned i am having a bit of problem with my ISP. not much minutes but i ll get back to you. good luck.

---

### Post by bacalao21 on 2008-07-17
> **nickdbliss said:**
> Sorry guys as far as i am concerned i am having a bit of problem with my ISP. not much minutes but i ll get back to you. good luck.

Thanks Nickdbliss! Good luck on your too.

---

### Post by neon100 on 2008-07-18
come one MAAAANNNN ! there must be someone here who can understand and solve my problem

---

### Post by mrfreakybig on 2008-07-20
Hi, I just figured I'd chime in. I'm having the same problem, too. I'm using an HP 530 notebook and its onboard wireless network adapter, and I'm running Ubuntu 8.04.

The interesting thing is this was working completely fine until maybe a week and a half ago. I've been installing every updated recommended by the Update Manager, and it was after one of those recent updates that this stopped working correctly. I wonder if one of these updates might have something to do with it.

Below are the outputs of some commands that were suggested.

Thanks for your help.

--Scott.

<>

**root@oblivion:~# wpa_passphrase <my ssid> <my password>**
network={
	ssid="<my ssid>"
	#psk="<m password>"
	psk=2ff45d259dd52738b995a185e4845fbd1986c6c5924e641ba3f9b5a5cc5617e0
}

-=-

**root@oblivion:~# cat /etc/network/interfaces**
auto lo
iface lo inet loopback



iface wlan0 inet dhcp
wpa-psk 2ff45d259dd52738b995a185e4845fbd1986c6c5924e641ba3f9b5a5cc5617e0
wpa-driver wext
wpa-key-mgmt WPA-PSK
wpa-proto WPA
wpa-ssid watusi

auto wlan0

-=-

**root@oblivion:~# cat /etc/wpa_supplicant.conf**
cat: /etc/wpa_supplicant.conf: No such file or directory

-=-
<b>root@oblivion:~# lspci</b>

00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS, 943/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS, 943/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/GME, 943/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801G (ICH7 Family) IDE Controller (rev 01)
00:1f.2 SATA controller: Intel Corporation 82801GBM/GHM (ICH7 Family) SATA AHCI Controller (rev 01)
02:06.0 CardBus bridge: ENE Technology Inc CB1410 Cardbus Controller (rev 01)
02:08.0 Ethernet controller: Intel Corporation 82562ET/EZ/GT/GZ - PRO/100 VE (LOM) Ethernet Controller Mobile (rev 01)
10:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)

-=-

**root@oblivion:~# iwlist scan**
lo        Interface doesn't support scanning.

eth0      Interface doesn't support scanning.

wmaster0  Interface doesn't support scanning.

wlan0     Scan completed :
          Cell 01 - Address: 00:1D:7E:6C:91:FB
                    ESSID:"watusi"
                    Mode:Master
                    Channel:6
                    Frequency:2.437 GHz (Channel 6)
                    Quality=80/100  Signal level=-54 dBm  Noise level=-127 dBm
                    Encryption key:on
                    IE: WPA Version 1
                        Group Cipher : TKIP
                        Pairwise Ciphers (1) : TKIP
                        Authentication Suites (1) : PSK
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:tsf=0000024648e81b82
          Cell 02 - Address: 00:0F:66:BE:FA:74
                    ESSID:"amber"
                    Mode:Master
                    Channel:11
                    Frequency:2.462 GHz (Channel 11)
                    Quality=54/100  Signal level=-76 dBm  Noise level=-127 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 6 Mb/s
                              9 Mb/s; 12 Mb/s; 18 Mb/s; 24 Mb/s; 36 Mb/s
                              48 Mb/s; 54 Mb/s
                    Extra:tsf=000000294f217202

-=-

**root@oblivion:~# ifconfig**

eth0      Link encap:Ethernet  HWaddr 00:1b:38:3b:90:07  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1524 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1524 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:80020 (78.1 KB)  TX bytes:80020 (78.1 KB)

wlan0     Link encap:Ethernet  HWaddr 00:1b:77:af:dc:8b  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0:avahi Link encap:Ethernet  HWaddr 00:1b:77:af:dc:8b  
          inet addr:169.254.9.62  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1

wmaster0  Link encap:UNSPEC  HWaddr 00-1B-77-AF-DC-8B-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

---

### Post by rlondre on 2008-07-20
I'm sorry to say but I've got the exact same problem. I have to change the password type back to WPA2 Personal and reenter my password. A real pain.  

For the past 8 years just about every year I give a different linux distro a try and for the past 3 or so I keep trying each new ubuntu version but eventually find a bug I can't resolve and cant tolerate and end up back with windows. I sure hope someone can help because I'm really trying to kick windows.

---

### Post by sputnikkk on 2008-07-20
I swear to god this is the biggest farce ive ever come across ... !!!  Literally hundreds of others having the same issues with all sorts of different NIC's.

Im 15+ hrs in to the exact same issue on a desktop system using this NetworkManager GUI ... my saga is in process here - [http://ubuntuforums.org/showthread.php?t=571188&page=64](http://ubuntuforums.org/showthread.php?t=571188&page=64)

maybe some of the posts by ubuntu guru's might help your plight.  Im still struggling.  This NIC is about to experience an UGLY death!

Apparently - none of these issues existed in prior ubuntu releases starting at Gutsy??? But  Im finding threads discussing this issue over a year old, and LOTs of them.

Hardy Heron
Linksys WMP54G
RaLink Chipset
rt2500pci driver
WAP1 / WAP2 / WEP - tried
Static IP setup

---

### Post by nickdbliss on 2008-07-21
Hi neon, cat /etc/wpa_supplicant.conf says no file or directory. You cant use wpa encryption since that means wpa_supplicant is not install to handle it right. go to terminal and enter this to install it:

sudo apt-get install wpasupplicant

Also in interfaces file comment out everything but leave
auto lo
iface lo inet loopback

as such. Then try posting result of cat /etc/wpa_supplicant.conf and also try to connect via network manager. Thx

Also see if network manager is added to ur startup programs.
system > preferences > sessions >startup programs
Look for network manager, if it is not there add it n put this in command box:
 nm-applet --sm-disable
Save n restart.

---

### Post by nickdbliss on 2008-07-21
Hi bacalao, Scan doesnt show anything, so i suspect the driver is not installed properly. 
Anyways also check if network manager is added to startup programs as explained in above post.I ll suggest you to uninstall Network-manager and try WICD as network manager application.

---

### Post by nickdbliss on 2008-07-21
These issues generally occur because of incompatible drivers or network manager or both.

---

### Post by bacalao21 on 2008-07-23
Thanks nickdbliss, sorry I've been out for a little bit. I'll try the recommendations as soon as I get off of work. I have a feeling that the multiple troubleshooting techniques and terminal commands may have my computer confused or incorrectly configured. I'll post again the results.

---

### Post by charonred on 2008-10-12
I was having similar problems and this solution/work-around seems to have fixed my 'Hardy' wireless connection & password/key problems so that my network is detected and connected, and keeps working even after re-booting.

NOTE: I wouldn't remove 'Network Manager' as that may kill your ethernet connection (it may not, but it has on one PC).

My laptop which runs Hardy, but with the KDE instead of Gnome, gave me a hint on how to get wireless working - it connects fine as it uses 'kwifi' and not 'Network Manager'.

As I use Gnome on my other PCs I went looking for something similar.

I used Synaptic to install 'wifi-radar' - I then put in the relevant settings into it and presto, I have wireless networking; and then I rebooted, and yep I still had wireless - after several reboots I still had wireless, so I recommend using 'wifi-radar' instead of Gnome's sometimes buggy 'Network Manager' 

(note: I'm using WEP, but I think it'll still work with WPA)

---

### Post by neon100 on 2009-03-08
How much do i need to donate to Ubuntu community to hire enough manpower to work on Ubuntu so hard until no problem is known to exist?

---

