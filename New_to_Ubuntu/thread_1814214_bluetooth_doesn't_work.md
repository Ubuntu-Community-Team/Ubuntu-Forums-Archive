---
title: "bluetooth doesn't work"
date: 2011-07-29
forum: New to Ubuntu
---

### Post by moonesque19 on 2011-07-29
im using ubuntu 11.04 and can't get my bluetooth to work.wifi works fine but it just shows that "bluetooth is disabled".how can i get  it to work?

---

### Post by skatinjj on 2011-07-29
Need a bit more information on what blue tooth device you are using.

---

### Post by moonesque19 on 2011-07-29
using a dell inspiron with broadcomm sta wireless driver.can use bluetooth with windows 7 but not with ubuntu.as already mentioned i can use wifi in ubuntu.only bluetooth doesn't work.

---

### Post by skatinjj on 2011-07-29
Have you looked in additional drivers?

---

### Post by moonesque19 on 2011-07-29
yup.it says that the driver is activated and currently in use.

---

### Post by skatinjj on 2011-07-29
[http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/]("http://computerandu.wordpress.com/2011/05/04/how-to-solve-no-wireless-networks-in-ubuntu-11-04/")

You can read this and see if it helps.

---

### Post by moonesque19 on 2011-07-30
still not working.

---

### Post by kumsy on 2011-07-30
it says the same for me and if i click receive files in the blue tooth menu it says blue tooth is disabled because i dont have the required packages.i too have a dell inspiron with broadcom.

---

### Post by Odipides on 2011-07-30
If you have an Intel Centrino Advanced N-6230 there seems to be the odd glitch with bluetooth.

Try this:
1) Open a terminal
2) Run:
   sudo service bluetooth restart

You sometimes have to delete and recreate the attached bluetooth device but, if you wait a few secs, it usually sorts the connections out.

---

### Post by skatinjj on 2011-07-30
Curious, could you all post the output of this:

```
lspci
```

In code tags please?

---

### Post by moonesque19 on 2011-07-30
00:00.0 Host bridge: Intel Corporation Core Processor DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation Core Processor Integrated Graphics Controller (rev 02)
00:16.0 Communication controller: Intel Corporation 5 Series/3400 Series Chipset HECI Controller (rev 06)
00:1a.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1b.0 Audio device: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio (rev 05)
00:1c.0 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 (rev 05)
00:1c.1 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 (rev 05)
00:1c.2 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 3 (rev 05)
00:1c.4 PCI bridge: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 5 (rev 05)
00:1d.0 USB Controller: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller (rev 05)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev a5)
00:1f.0 ISA bridge: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller (rev 05)
00:1f.2 SATA controller: Intel Corporation 5 Series/3400 Series Chipset 6 port SATA AHCI Controller (rev 05)
00:1f.3 SMBus: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller (rev 05)
00:1f.6 Signal processing controller: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem (rev 05)
12:00.0 Network controller: Broadcom Corporation BCM4313 802.11b/g/n Wireless LAN Controller (rev 01)
13:00.0 Ethernet controller: Atheros Communications AR8132 Fast Ethernet (rev c0)

---

### Post by skatinjj on 2011-07-30
[http://ubuntuforums.org/showthread.php?t=1783272]("http://ubuntuforums.org/showthread.php?t=1783272")

You can read that to see if anything there helps.

---

### Post by moonesque19 on 2011-07-31
the issues are different in both cases.

---

### Post by westie457 on 2011-07-31
What does ```
rfkill list all
``` tell us

---

### Post by moonesque19 on 2011-07-31
was playing around to realise that the bluetooth manager said "adapter is disabled".so i booted into win 7 and turned it on and booted into ubuntu after that.bluetooth worked fine.then to make sure of it i did another restart and turned off and booted the laptop.bluetooth's working now.the issue was that i had the adapter disabled in the first place.sorry for being a dork and thank you for the replies.

---

### Post by johnfriend on 2011-08-01
I have same issue. i am using MSI CR620.my bluetooth turned on but it doesn't detect any device. it was worked when i had windows7.
when i try 'rfkill list all'

it shows

0: msi-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: msi-wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

---

### Post by westie457 on 2011-08-01
> **johnfriend said:**
> I have same issue. i am using MSI CR620.my bluetooth turned on but it doesn't detect any device. it was worked when i had windows7.
when i try 'rfkill list all'

it shows

0: msi-bluetooth: Bluetooth
	Soft blocked: no
	Hard blocked: no
1: msi-wlan: Wireless LAN
	Soft blocked: yes
	Hard blocked: no
2: hci0: Bluetooth
	Soft blocked: no
	Hard blocked: no
3: phy0: Wireless LAN
	Soft blocked: no
	Hard blocked: yes

Run these commands one at a time in a terminal ```
lspci -nn

ifconfig

iwconfig

lshw -C network
```

Copy the output for each and paste between ```

``` tags by clicking on # at the top of the message pane.

---

### Post by johnfriend on 2011-08-02
[lspci -nn][00:00.0 Host bridge [0600]: Intel Corporation Core Processor DRAM Controller [8086:0044] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation Core Processor Integrated Graphics Controller [8086:0046] (rev 02)
00:16.0 Communication controller [0780]: Intel Corporation 5 Series/3400 Series Chipset HECI Controller [8086:3b64] (rev 06)
00:1a.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b3c] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 5 Series/3400 Series Chipset High Definition Audio [8086:3b56] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 1 [8086:3b42] (rev 05)
00:1c.1 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 2 [8086:3b44] (rev 05)
00:1c.3 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 4 [8086:3b48] (rev 05)
00:1c.5 PCI bridge [0604]: Intel Corporation 5 Series/3400 Series Chipset PCI Express Root Port 6 [8086:3b4c] (rev 05)
00:1d.0 USB Controller [0c03]: Intel Corporation 5 Series/3400 Series Chipset USB2 Enhanced Host Controller [8086:3b34] (rev 05)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 Mobile PCI Bridge [8086:2448] (rev a5)
00:1f.0 ISA bridge [0601]: Intel Corporation Mobile 5 Series Chipset LPC Interface Controller [8086:3b09] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 5 Series/3400 Series Chipset 4 port SATA AHCI Controller [8086:3b29] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 5 Series/3400 Series Chipset SMBus Controller [8086:3b30] (rev 05)
00:1f.6 Signal processing controller [1180]: Intel Corporation 5 Series/3400 Series Chipset Thermal Subsystem [8086:3b32] (rev 05)
05:00.0 Network controller [0280]: Ralink corp. RT3090 Wireless 802.11n 1T/1R PCIe [1814:3090]
06:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)
3f:00.0 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture Generic Non-core Registers [8086:2c62] (rev 02)
3f:00.1 Host bridge [0600]: Intel Corporation Core Processor QuickPath Architecture System Address Decoder [8086:2d01] (rev 02)
3f:02.0 Host bridge [0600]: Intel Corporation Core Processor QPI Link 0 [8086:2d10] (rev 02)
3f:02.1 Host bridge [0600]: Intel Corporation Core Processor QPI Physical 0 [8086:2d11] (rev 02)
3f:02.2 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d12] (rev 02)
3f:02.3 Host bridge [0600]: Intel Corporation Core Processor Reserved [8086:2d13] (rev 02)
]
[ifconfig][eth0      Link encap:Ethernet  HWaddr 40:61:86:b5:e4:ad  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:40 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:16 errors:0 dropped:0 overruns:0 frame:0
          TX packets:16 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:960 (960.0 B)  TX bytes:960 (960.0 B)

usb0      Link encap:Ethernet  HWaddr fe:07:0a:02:11:7f  
          inet addr:192.168.42.110  Bcast:192.168.42.255  Mask:255.255.255.0
          inet6 addr: fe80::fc07:aff:fe02:117f/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6302 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6613 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5077556 (5.0 MB)  TX bytes:996229 (996.2 KB)
]
[iwconfig]
[lo        no wireless extensions.

eth0      no wireless extensions.

wlan0     IEEE 802.11bgn  ESSID:off/any  
          Mode:Managed  Access Point: Not-Associated   Tx-Power=0 dBm   
          Retry  long limit:7   RTS thr:off   Fragment thr:off
          Power Management:on
          
usb0      no wireless extensions.
]
[lshw -C network]
[WARNING: you should run this program as super-user.
PCI (sysfs)  
  *-network DISABLED      
       description: Wireless interface
       product: RT3090 Wireless 802.11n 1T/1R PCIe
       vendor: Ralink corp.
       physical id: 0
       bus info: pci@0000:05:00.0
       logical name: wlan0
       version: 00
       serial: 6c:62:6d:11:af:4d
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rt2800pci driverversion=2.6.38-10-generic firmware=N/A latency=0 multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 memory:f4000000-f400ffff
  *-network
       description: Ethernet interface
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:06:00.0
       logical name: eth0
       version: 02
       serial: 40:61:86:b5:e4:ad
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half latency=0 multicast=yes port=MII speed=10Mbit/s
       resources: irq:40 ioport:a000(size=256) memory:f2c30000-f2c30fff memory:f2c20000-f2c2ffff memory:f2c00000-f2c1ffff
  *-network
       description: Ethernet interface
       physical id: 2
       logical name: usb0
       serial: fe:07:0a:02:11:7f
       capabilities: ethernet physical
       configuration: broadcast=yes driver=cdc_ether driverversion=22-Aug-2005 firmware=CDC Ethernet Device ip=192.168.42.110 multicast=yes
]

---

### Post by westie457 on 2011-08-02
Are you using a desktop pc or a laptop? If a pc everything should just start. With a laptop the on board wireless module must be switched on for wireless to work even when you want to use a dongle and not the installed modules.

Can you run this in a terminal and let us know what the output is please ```
rfkill unblock all
```
Even if the command goes straight to the prompt is classed as output because this tells us something.

---

### Post by johnfriend on 2011-08-03
no output


i am using MSI cR620 Laptop. i switch on my bluetooth but it doesn't detect any device.my wireless works fine.

---

### Post by lbirunner on 2011-08-09
Did you find a fix for this?
I'm having the same problem with my Dell D630.
Any help would be appreciated.

---

### Post by gandaran on 2011-08-09
> **lbirunner said:**
> Did you find a fix for this?
I'm having the same problem with my Dell D630.
Any help would be appreciated.
fix for what? bluetooth?
what does it say when you open the bluetooth application?

---

### Post by lbirunner on 2011-08-09
Actually, I posted a new thread [here]("http://ubuntuforums.org/showthread.php?t=1812493") about a week ago and have no responses.
If you have any suggestions I would appreciate it.

Thanks.

---

### Post by gandaran on 2011-08-09
> **lbirunner said:**
> Actually, I posted a new thread [here]("http://ubuntuforums.org/showthread.php?t=1812493") about a week ago and have no responses.
If you have any suggestions I would appreciate it.

Thanks.
okay, I have posted on your thread and recommend blueman for enabling bluetooth, I also have the same problem with gnome bluetooth manager, blueman is the only application that can start the bluetooth adapter on my desktop PC while gnome bluetooth manager works fine on my netbook with built-in bluetooth.

---

