---
title: "Ethernet Network Disconnected Issue"
date: 2016-09-16
forum: Networking &amp; Wireless
---

### Post by ganesh3 on 2016-09-16
Hi,

My ethernet network is disconnected post a fresh install of Ubuntu 16.04 and even after further updates remains disconnected in the nm-applet. Please note I had raised a similar issue for my old laptop which is still unsolved [https://ubuntuforums.org/showthread.php?t=2332286](https://ubuntuforums.org/showthread.php?t=2332286). This is for reference only as suggested by Jeremy in the post.

I am sharing the wireless-info output as well as the lspci output for the new laptop.

```
$ inxi -ACDMNSG[INDENT=2]System:    Host: ganesh-Lenovo-ideapad-100-14IBD Kernel: 4.4.0-36-generic x86_64 (64 bit) Desktop: Unity 7.4.0
           Distro: Ubuntu 16.04 xenial
Machine:   System: LENOVO (portable) product: 80RK v: Lenovo ideapad 100-14IBD
           Mobo: LENOVO model: Nano 4B6 v: NO DPK Bios: LENOVO v: E0CN45WW date: 01/13/2016
CPU:       Dual core Intel Core i3-5005U (-HT-MCP-) cache: 3072 KB 
           clock speeds: max: 2000 MHz 1: 1073 MHz 2: 799 MHz 3: 800 MHz 4: 1027 MHz
Graphics:  Card: Intel Broadwell-U Integrated Graphics
           Display Server: X.Org 1.18.3 drivers: intel (unloaded: fbdev,vesa) Resolution: 1366x768@60.00hz
           GLX Renderer: Mesa DRI Intel HD Graphics 5500 (Broadwell GT2) GLX Version: 3.0 Mesa 11.2.2
Audio:     Card-1 Intel Wildcat Point-LP High Definition Audio Controller driver: snd_hda_intel
           Card-2 Intel Broadwell-U Audio Controller driver: snd_hda_intel
           Sound: Advanced Linux Sound Architecture v: k4.4.0-36-generic
Network:   Card-1: Realtek RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller driver: r8169
           Card-2: Realtek RTL8723BE PCIe Wireless Network Adapter driver: rtl8723be
Drives:    HDD Total Size: 500.1GB (2.2% used) ID-1: /dev/sda model: TOSHIBA_MQ01ABF0 size: 500.1GB
[/INDENT]

```
```
$ lspci[INDENT=2]00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)
00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)
00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)
00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)
00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)
00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)
00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)
00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)
00:1d.0 USB controller: Intel Corporation Wildcat Point-LP USB EHCI Controller (rev 03)
00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)
00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller (rev 08)
03:00.0 Network controller: Realtek Semiconductor Co., Ltd. RTL8723BE PCIe Wireless Network Adapter
[/INDENT]

```
[ATTACH]271223[/ATTACH]

---

### Post by TheFu on 2016-09-16
Please put the output inside the code tags too!!!!!!!!!!!!  It will be easier to read when things line up.
I'm used to looking at **sudo lshw -C network** output for this stuff.  The output from **route** and **ifconfig** would be helpful too.

Not working can mean all sorts of things. Can you be more specific? Pick on (wired or wifi) and stick with that in 1 question. 

I can't help with wifi stuff or nm stuff. Don't use nm myself due to prior issues over the years.
[https://askubuntu.com/questions/470609/rtl8101e-rtl8102e-not-working-with-ubuntu-14-04-hp-g61](https://askubuntu.com/questions/470609/rtl8101e-rtl8102e-not-working-with-ubuntu-14-04-hp-g61) might be helpful, though it is for 14.04.

---

### Post by ganesh3 on 2016-09-18
Here is the output requested
```

sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: RTL8101/2/6E PCI Express Fast/Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: enp2s0
       version: 08
       serial: 50:7b:9d:ca:c5:cc
       size: 10Mbit/s
       capacity: 100Mbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=half firmware=rtl8106e-2_0.0.1 04/23/13 latency=0 link=no multicast=yes port=MII speed=10Mbit/s
       resources: irq:47 ioport:4000(size=256) memory:c1104000-c1104fff memory:c1100000-c1103fff
  *-network
       description: Wireless interface
       product: RTL8723BE PCIe Wireless Network Adapter
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: wlp3s0
       version: 00
       serial: 30:f7:72:31:0b:b5
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=rtl8723be driverversion=4.4.0-36-generic firmware=N/A ip=192.168.1.101 latency=0 link=yes multicast=yes wireless=IEEE 802.11bgn
       resources: irq:19 ioport:3000(size=256) memory:c1000000-c1003fff

```

```

enp2s0    Link encap:Ethernet  HWaddr 50:7b:9d:ca:c5:cc  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:4882 errors:0 dropped:0 overruns:0 frame:0
          TX packets:4882 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:411697 (411.6 KB)  TX bytes:411697 (411.6 KB)

wlp3s0    Link encap:Ethernet  HWaddr 30:f7:72:31:0b:b5  
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::32f7:72ff:fe31:bb5/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:13936 errors:0 dropped:0 overruns:0 frame:0
          TX packets:14174 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:12174365 (12.1 MB)  TX bytes:1783428 (1.7 MB)


```

```

sudo route
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
default         tata-photon-max 0.0.0.0         UG    600    0        0 wlp3s0
link-local      *               255.255.0.0     U     1000   0        0 wlp3s0
192.168.1.0     *               255.255.255.0   U     600    0        0 wlp3s0

```

---

### Post by ganesh3 on 2016-09-18
Wired Internet it is. The nm-applet is disabled for ethernet. The error is "Ethernet Network Disconnected"

I also have installed elementary desktop and there too once I login I am unable to enable/disable ethernet.

---

### Post by ganesh3 on 2016-09-18
The URL suggests to download drivers from Realtek but for Linux they only have for kernel 3.x, 2.6.x & 2.4.x and we are now on 4.4 with Ubuntu 16.04. Not much help with the link. I am not sure what is wicd and how does it work.

> **TheFu said:**
> Please put the output inside the code tags too!!!!!!!!!!!!  It will be easier to read when things line up.
I'm used to looking at **sudo lshw -C network** output for this stuff.  The output from **route** and **ifconfig** would be helpful too.

Not working can mean all sorts of things. Can you be more specific? Pick on (wired or wifi) and stick with that in 1 question. 

I can't help with wifi stuff or nm stuff. Don't use nm myself due to prior issues over the years.
[https://askubuntu.com/questions/470609/rtl8101e-rtl8102e-not-working-with-ubuntu-14-04-hp-g61](https://askubuntu.com/questions/470609/rtl8101e-rtl8102e-not-working-with-ubuntu-14-04-hp-g61) might be helpful, though it is for 14.04.

---

### Post by TheFu on 2016-09-18
a) it looks like the wifi stuff should be working. Does it or does it not?  If not, can you
[LIST=1]
[*]ping the router, using the IP address?
[*]ping 8.8.8.8
[*]ping google.com (and other well-known websites?
[/LIST]

b) if wifi **is** connected, then it is best NOT to also connect the wired at the same time.  Before doing any troubleshooting on the wired connection, disable the wifi connection.

Are you trying to have a DHCP or static IP configured on the wired connection? Please post the /etc/network/interfaces file (use code tags).

Is there a good, working, ethernet cable connected between the computer and the router?  Hate to ask, but there isn't any information above about it.

---

### Post by ganesh3 on 2016-09-18
The issue is not with Wifi at all. The issue is with Ethernet. 

The nm-applet on Ubuntu 16.04 says "Ethernet Network disconnected" and this is a new laptop that I just bought. 

I have installed elementary desktop as well and the situation is same. I am unable to enable/disable ethernet as the icon is not editable.

Hope this helps.



Thanks

Ganesh

---

### Post by ganesh3 on 2016-10-02
Sharing the interfaces files

```

# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
iface lo inet loopback

```

The issue is that since the "Ethernet Network Disconnected" is the error on the nm-applet, I am unable to connect to any ethernet network. I generally connect to a dongle for connecting to internet and never use both Wifi & Ethernet at the same time.

---

### Post by TheFu on 2016-10-02
Reviewed everything above again.
a) bad cable?
b) bad port?
c) incorrect driver/bad driver?
d) bad network manager.

You might try setting a static IP in the interfaces file to see if that works.
[https://askubuntu.com/questions/766131/set-static-ip-ubuntu-16-04](https://askubuntu.com/questions/766131/set-static-ip-ubuntu-16-04) has an example.  Edit the file, restart networking (sudo service networking restart), check that the card has an IP and that the routes have been updated. Try to ping google.com. If that works, everything should be fine. If that doesn't, try rebooting (sometimes restarting networking doesn't _take_ since 14.04).  If this doesn't fix it and you've swapped the cable/ports (or proved it is working), then it is likely a driver issue.

For better help, please be VERY CLEAR that you've troubleshot everything listed in this and the prior messages. There are questions from 2+ weeks ago which haven't been answered.

---

### Post by ganesh3 on 2016-10-02
It is strange that you ask me for more details on the interfaces file when infact I have already provided all the info in the wireless-info tar file attached in the initial query itself.

I was surprised that there was no response for more than 2 weeks given that all information has already been provided. Please check if all necessary information you need for the steps mentioned are already there in the wireless info file and let me know if I need to perform the steps mentioned by you.


Regards,

Ganesh

---

