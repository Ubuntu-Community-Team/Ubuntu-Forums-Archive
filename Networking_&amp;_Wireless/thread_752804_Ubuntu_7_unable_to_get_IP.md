---
title: "Ubuntu 7 unable to get IP"
date: 2008-04-12
forum: Networking &amp; Wireless
---

### Post by pintoosingh on 2008-04-12
Hi All,

I am newbie to ubuntu. I am tryin to get internet working on it. I am using wimax(Reliance) connection, which needs automatic configuration(dhcp). I am able to get connected, if i get IP by logging in windows first and then coming back to ubuntu. But unable to connect to net by directly logging into ubuntu after switching on my PoE device.

Any comments?

Rgds,
Pintoo.

---

### Post by Red-Shield on 2008-04-12
i dont know what kind of connection that is but are you using a wired connection or wireless connection ??

---

### Post by Crafty Kisses on 2008-04-12
> **pintoosingh said:**
> Hi All,

I am newbie to ubuntu. I am tryin to get internet working on it. I am using wimax(Reliance) connection, which needs automatic configuration(dhcp). I am able to get connected, if i get IP by logging in windows first and then coming back to ubuntu. But unable to connect to net by directly logging into ubuntu after switching on my PoE device.

Any comments?

Rgds,
Pintoo.

Post these outputs:
```
lspci
```
Also
```
iwconfig
```

---

### Post by pintoosingh on 2008-04-12
Hi red-shield it is wired connection.

Codename will get back to you with the result of it soon.
But do you have any basic kinda solution?

---

### Post by Red-Shield on 2008-04-12
can you print what you get when you give** ifconfig  ** and **iwconfig** is this a wireless connection on a laptop or a desktop????

---

### Post by Red-Shield on 2008-04-12
so then run in a terminal iwconfig, and ifconfig, and sudo iwlist scan and then copy and past here in the fourm and i hope to help you.

---

### Post by pintoosingh on 2008-04-12
@Red-shiled and codename.. here is the stack trace for what u asked TIA..

chandrakiran@Pintoo-Singh:~$ lspci
00:00.0 Host bridge: Intel Corporation Mobile 945GM/PM/GMS/940GML and 945GT Express Memory Controller Hub (rev 03)
00:02.0 VGA compatible controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:02.1 Display controller: Intel Corporation Mobile 945GM/GMS/940GML Express Integrated Graphics Controller (rev 03)
00:1b.0 Audio device: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller (rev 01)
00:1c.0 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 (rev 01)
00:1c.1 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 2 (rev 01)
00:1c.3 PCI bridge: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #3 (rev 01)
00:1d.3 USB Controller: Intel Corporation 82801G (ICH7 Family) USB UHCI #4 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev e1)
00:1f.0 ISA bridge: Intel Corporation 82801GBM (ICH7-M) LPC Interface Bridge (rev 01)
00:1f.2 IDE interface: Intel Corporation 82801GBM/GHM (ICH7 Family) Serial ATA Storage Controller IDE (rev 01)
00:1f.3 SMBus: Intel Corporation 82801G (ICH7 Family) SMBus Controller (rev 01)
02:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
02:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832
02:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 19)
02:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 01)
02:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 0a)
02:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 05)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)
chandrakiran@Pintoo-Singh:~$ 
chandrakiran@Pintoo-Singh:~$ 
chandrakiran@Pintoo-Singh:~$ 
chandrakiran@Pintoo-Singh:~$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:off/any  
          Mode:Managed  Frequency=nan kHz  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power:14 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:1   Missed beacon:0

chandrakiran@Pintoo-Singh:~$ 
chandrakiran@Pintoo-Singh:~$ 
chandrakiran@Pintoo-Singh:~$ sudo iwlist
Usage: iwlist [interface] scanning
              [interface] frequency
              [interface] channel
              [interface] bitrate
              [interface] rate
              [interface] encryption
              [interface] key
              [interface] power
              [interface] txpower
              [interface] retry
              [interface] ap
              [interface] accesspoints
              [interface] peers
              [interface] event
chandrakiran@Pintoo-Singh:~$ 
chandrakiran@Pintoo-Singh:~$ 
chandrakiran@Pintoo-Singh:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:15:C5:78:80:8E  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:979 errors:1 dropped:1 overruns:0 frame:0
          TX packets:19 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:101345 (98.9 KiB)  TX bytes:3754 (3.6 KiB)
          Interrupt:17 

eth1      Link encap:Ethernet  HWaddr 00:19:D2:D6:6A:85  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:1 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 Base address:0xc000 Memory:efdff000-efdfffff 

eth0:avah Link encap:Ethernet  HWaddr 00:15:C5:78:80:8E  
          inet addr:169.254.7.206  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:17 

eth1:avah Link encap:Ethernet  HWaddr 00:19:D2:D6:6A:85  
          inet addr:169.254.8.129  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          Interrupt:17 Base address:0xc000 Memory:efdff000-efdfffff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:102 errors:0 dropped:0 overruns:0 frame:0
          TX packets:102 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9032 (8.8 KiB)  TX bytes:9032 (8.8 KiB)


@Red-shield its wired connection and laptop...

---

### Post by Red-Shield on 2008-04-12
ok then what i want you to do is make sure that your wireless card is powered on in the BIOS and then run in a terminal **sudo iwlist scan** and then you need to run in a terminal** sudo iwconfig eth1 essid "any"** and then run** dhclient** and then post here i think that should do it

---

### Post by pintoosingh on 2008-04-13
Hi,

I am able to connect to net using dhclient. 

I gave following terminals in terminal.
sudo dhclient eth0
sudo ifconfig eth0 down
sudo ifconfig eth0 up

and i got ip address... it started working. Redcode can you explain me problem in this case?
is it that my dhcp is not activated?

Now i am trying to install some components like gparted. I am getting the following problem.

chandrakiran@pintoo-singh:~$ sudo apt-get install dhcpcd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package dhcpcd

Could you help me why I am getting these.

---

### Post by Red-Shield on 2008-04-13
well you need to use **sudo apt-get install gparted** sometimes the servers are not up and running or mabey they are unreachable tyr it a few times i all ready have that program i tried to reinstall to day and the server was there and ready it was your command try it as i listed it for you and it should work.

---

### Post by pintoosingh on 2008-04-15
The problem has resurfaced again.

When i did dhclient it returned with no dhcp offers.

When i used **ifdown -a -force**, it said forcefully closing connection on port 67 with **123.237.136.1** which happens to be **default gateway** for my connection.

But when i do **ifconfig eth0**, i am getting the same result as posted in one of the above posts.

I feel that it may be due to incomplete updates, i had to stop downloading them in middle and install only the downloaded updates. What can be the problem?

Is there any way i can revert them?

---

