---
title: "bcm4318 sees &quot;iwlist scan&quot; results but does not connect"
date: 2009-07-23
forum: New to Ubuntu
---

### Post by A7Bo on 2009-07-23
I need some help! I have been at a wireless network card problem for 6 days! This ends either in a solution or with this #^%$&^%$ HP laptop in pieces flying back from the wall!!!

I have an HP2000 latop (which is BTW meaningless to an extent since in the past I have found that HP seems to recycle laptop numbers!) with a bc43xx wireless card built in.

I have loaded the b43 firmware and wireless-tools. LSPCI gives me all of the proper answers. The light is on AND when I run "iwslist scan" I am able to see my wireless router. I have the thing hidden (not broadcasting SSID) BUT, BUT! I have tried with the SSID on and off. It makes no never mind! The wireless builtin "sees" the router and returns all of the info when I run "iwlist scan."

BUT the card will NOT connect when I run 
< sudo iwconfig wlan0 essid "My wireless point" >.

My other laptop runs fine with a US Robotics 5411 PCI card. going to the same point!

I can send info but, at this point I don't know what to send! To save time, effort, and page space please know that the card:

1. Is a proper card (bcm4318) and returns the proper info from both "lspci" and the "lspc -n" commands.
2. I have loaded the b43-iwcutter package AND the attendent firmware as well as 'wireless-tools'
3. The card sees the access point and encryption is OFF for testing. The card returns the proper channel, name, etc from an < iwlist scan > command.

4. I have tried:
<iwconfig wlan0 essid "my router name">  as both user and sudo. The command runs but I get 0 packets trx or rec'd.

5. When I run < iwconfig > without parameters the "iwconfig" command returns the information for my router and shows zero packet traffic.
6. The router works since I am usng the router to send this post from another machine.

Is there anyone who can help get me further troubleshooting this? Is there a tool I can use to further troubleshoot the problem? Has anyone experienced similar problems. I would prefer to work from the command line in attempting to fix this problem.

Thanx

---

### Post by keplerspeed on 2009-07-23
Firstly:

1) Go to system>administration>hardware drivers. The Broadcom driver should be avaliable. Enable this driver and reboot.

2) Left click on the network applet>connect to hidden network, and enter the details.

3) If no connect, please describle what is happening (ie do you get a box popping up asking for the password again?)

4) If no connect please post the output of these commands:
```

lspci

```

Also since you are using kubuntu details will be different. For example I have no idea when "hardware drivers" is in kubuntu.

```

ifconfig

```

```

iwconfig

```

```

iwlist scan

```

```

cat /etc/network/interfaces

```

---

### Post by A7Bo on 2009-07-24
1) Go to system>administration>hardware drivers. The Broadcom driver should be avaliable. Enable this driver and reboot.
2) Left click on the network applet>connect to hidden network, and enter the details.
3) If no connect, please describe what is happening (ie do you get a box popping up asking for the password again?)

     [I]  I run Kubuntu. KDE doesn't have this app in the same place. However, It is interesting that there IS
       a "hardware drivers" selection under "System" on my other laptop. This is the laptop that runs my 
       US Robotics card under ndiswrapper. However, the B43 driver is a native Linux driver so I don't have 
       a hardware driver selection on the laptop that has the problem. That is why I am trying to attack this 
       problem from the console.  Oh well :) Also I can run the Knetwork app and it takes the logon command, 
       but nothing happens. No packet traffic. A 'ping' returns 'network does not exist' [/I]


Ok. Here is the output. There are no suprises. One thing, my other laptop, using a US Robotics PCI card under NDISWRAPPER does have a "wireless driver" menu icon in System. But the laptop with the problem does not. Leads me to wonder about some needed software? Since I have installed fw-cutter, wireless-tools, and a check indicates that wpasupplicant is installed (well, I have a wpasupplicant entry in /etc/network) I wonder if I need some other software that was not installed by the inital install of Kubuntu 9.04. FYI I installed the Kubuntu 9.04 "hack" with KDE 3.5 [http://apt.pearsoncomputing.net/cdimages/]("http://apt.pearsoncomputing.net/cdimages/")
(I really can't stand the 4.0 KDE and it doesn't work correctly anyhoo!)


< Obviously not linking after the card comes up and the radio is turned on 
output from DMESG: (tailed) >
[with my NIC addr "xx"'d out]

```
[   20.795036] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.795044] Bluetooth: BNEP filters: protocol multicast
[   20.821009] Bridge firewalling registered
[   21.665753] ppdev: user-space parallel port driver
[   23.531461] pci 0000:01:05.0: power state changed by ACPI to D0
[   23.531482] pci 0000:01:05.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   23.686527] [drm] Initialized drm 1.1.0 20060810
[   23.739616] [drm] Initialized radeon 1.29.0 20080528 on minor 0
[   24.377261] [drm] Setting GART location based on new memory map
[   24.378429] [drm] Loading R300 Microcode
[   24.378457] [drm] Num pipes: 1
[   24.378466] [drm] writeback test succeeded in 1 usecs
[   25.628866] eth0: link down
[   25.629458] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.690746] input: b43-phy0 as /devices/virtual/input/input9
[   25.752114] b43 ssb0:0: firmware: requesting b43/ucode5.fw
[   25.855142] b43 ssb0:0: firmware: requesting b43/pcm5.fw
[   25.904582] b43 ssb0:0: firmware: requesting b43/b0g0initvals5.fw
[   25.971018] b43 ssb0:0: firmware: requesting b43/b0g0bsinitvals5.fw
[   26.121507] b43-phy0: Loading firmware version 410.2160 (2007-05-26 15:32:10)
[   26.174980] Registered led device: b43-phy0::radio
[   26.201185] b43-phy0: Radio turned on by software
[   26.201890] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   27.752304] wlan0: direct probe to AP xx:xx:xx:xx:xx try 1
[   27.952066] wlan0: direct probe to AP xx:xx:xx:xx:xx try 2
[   28.152079] wlan0: direct probe to AP xx:xx:xx:xx:xx try 3
[   28.352061] wlan0: direct probe to AP xx:xx:xx:xx:xx timed out
[   35.911248] [drm] Num pipes: 1

```


Obviously not linking after the card comes up and the radio is turned on.

Output from LSPCI:

```
00:00.0 Host bridge: ATI Technologies Inc RS480 Host Bridge (rev 10)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 81)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
00:14.5 Multimedia audio controller: ATI Technologies Inc IXP SB400 AC'97 Audio Controller (rev 80)
00:14.6 Modem: ATI Technologies Inc SB400 AC'97 Modem Controller (rev 80)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:05.0 VGA compatible controller: ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)
05:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
05:02.0 Network controller: Broadcom Corporation BCM4318 [AirForce One 54g] 802.11g Wireless LAN Controller (rev 02)
05:09.0 CardBus bridge: Texas Instruments PCIxx21/x515 Cardbus Controller

```

Output from IFCONFIG (with my NIC addr "xx"'d out)

```
eth0      Link encap:Ethernet  HWaddr 
 xx:xx:xx:xx:xx:xx
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:18 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wlan0     Link encap:Ethernet  HWaddr 00:xx:xx:xx:xx:xx  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

wmaster0  Link encap:UNSPEC  HWaddr xx:xx:xx:xx:xx:xx-00-00-00-00-00-00-00-00-00-00  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

```

output from < /etc/network/interfaces > :

```
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

```

---

### Post by superprash2003 on 2009-07-26
could you also post output of
1)iwconfig
2)lshw -C network
3)sudo iwlist scanning ( you didnt post it earlier , when asked )

---

### Post by A7Bo on 2009-07-26
Thank you for extending your help. I greatly appreciate the time and trouble you took to help me with this problem. I am certainly not the only person to experience this problem. 

I "solved" the problem by installing UBUNTU 9.04. The Jaunty (9.04) version has the B43 driver code included. After reading untold numbers of posts, info files, how-to's, and tutorials I installed the b43-fwcutter and firmware (via wired connection) by adding:

   [B] deb  [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) jaunty-cafuego all
    deb-src [http://ubuntu.cafuego.net/](http://ubuntu.cafuego.net/) jaunty-cafuego all
[/B]
to my /etc/apt/sources.list

Then added the GnuPG key for the Cafuego.net repositories(from console):

**wget -q -O - [http://ubuntu.cafuego.net/cafuego.gpg](http://ubuntu.cafuego.net/cafuego.gpg) | sudo apt-key add - **

and ran (from console):

**"sudo aptitude update"**

**"sudo apt-get install b43-fwcutter" **(which asked me to install the firmware patches).

I then rebooted and ... it works!

---

