---
title: "WIFI dont work after update to 14.10"
date: 2014-10-25
forum: Networking &amp; Wireless
---

### Post by zlatan2 on 2014-10-25
Hi all:)

I have problem with my wifi on asus X552c. wont work after update from 14.04  to 14.10 :( 

```
*-network UNCLAIMED     
       description: Network controller
       product: MT7630e 802.11bgn Wireless Network Adapter
       vendor: MEDIATEK Corp.
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f7900000-f79fffff
  *-network
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:04:00.2
       logical name: eth0
       version: 0a
       serial: 10:c3:7b:8d:a1:85
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-1_0.0.3 06/18/12 ip=192.168.1.106 latency=0 link=yes multicast=yes port=MII speed=100Mbit/s
       resources: irq:43 ioport:d000(size=256) memory:f2104000-f2104fff memory:f2100000-f2103fff
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.10
Release:    14.10
Codename:    utopic


```

Ifconfig :

```
eth0      Link encap:Ethernet  HWaddr 10:c3:7b:8d:a1:85  
          inet addr:192.168.1.106  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::12c3:7bff:fe8d:a185/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:9176 errors:0 dropped:0 overruns:0 frame:0
          TX packets:8871 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:6807255 (6.8 MB)  TX bytes:1207271 (1.2 MB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2379 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2379 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:328370 (328.3 KB)  TX bytes:328370 (328.3 KB)


```

Iwconfig :

```
eth0      no wireless extensions.

lo        no wireless extensions.


```

lspci :

> 00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 3D controller: NVIDIA Corporation GF117M [GeForce 610M/710M/820M / GT 620M/625M/630M/720M] (rev a1)
03:00.0 Network controller: MEDIATEK Corp. MT7630e 802.11bgn Wireless Network Adapter
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5289 (rev 01)
04:00.2 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 0a)





rfkill list 

> asus-wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: asus-bluetooth: Bluetooth
    Soft blocked: yes
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: yes




Help ?:(

---

### Post by xmbwd on 2014-10-27
I am having the same problem -- but not with my built in wifi card (Intel Corporation Wireless 7260 (rev 6b)) [that card works, but it is terrible and randomly drops signal from good to low].  My problem is with the [Edimax ew-7811un]("http://www.google.com/url?sa=t&rct=j&q=&esrc=s&source=web&cd=2&cad=rja&uact=8&sqi=2&ved=0CCYQFjAB&url=http%3A%2F%2Fwww.edimax.com%2Fen%2Fproduce_detail.php%3Fpd_id%3D347&ei=n49OVMqAIZL3oASF_IKgDg&usg=AFQjCNGqB_PSjXcUeOzbAlTraQA2Y3JNbg&bvm=bv.77880786,d.cGU") usb dongle I used to get better reception on my laptop.  It uses a Realtek driver, but that had issues -- though there was [a discussion of a fix]("http://ubuntuforums.org/showthread.php?t=2148130&page=3") (also, [direct link to fix]("https://github.com/pvaret/rtl8192cu-fixes")).  

After the upgrade, the fix no longer seems to work. At least for me.  The new kernel for my 14.10 install is 3.16.0-23-generic x86_64, whereas the fix listed is for 3.11 (though it worked on 3.13 too!).  

Anyone have an idea how to get this back up and running?

---

### Post by xmbwd on 2014-10-28
I don't know the solution, but at least in my case I know the problem -- "Wireless N."  Before the upgrade to 14.10, wireless N worked with the Edimax dongle.  After the upgrade, it does not. 

I was in an area with solely N coverage, that's why it would not connect.  Any ideas?  I had thought this bug was fixed.

---

