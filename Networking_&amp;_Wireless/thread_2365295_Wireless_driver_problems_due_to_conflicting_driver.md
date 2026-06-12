---
title: "Wireless driver problems due to conflicting drivers"
date: 2017-07-04
forum: Networking &amp; Wireless
---

### Post by hxu-yunocreative on 2017-07-04
Hi Ubuntu community! I hope you are well. I was trying to get Ubuntu to recognize my external wireless card, and in the process I managed to somehow disable Ubuntu's ability to read my integrated wireless card... I am working with a Sager computer which had been running (I believe) iwlwifi since I first dual-booted my native Windows 10 machine. I bought a tp-link wn722n USB WIFI adapter, and was hoping to make it work on Ubuntu. I followed the steps here [https://askubuntu.com/questions/512727/how-to-install-driver-for-tp-link-tl-wn722n-on-ubuntu-14-04](https://askubuntu.com/questions/512727/how-to-install-driver-for-tp-link-tl-wn722n-on-ubuntu-14-04) to try to make it work with the 4-step process outlined in the first response. Basically it tells you to download backports (I downloaded the most recent version) and configure ath9k. But afterfollowing those steps I rebooted, after which neither my integrated wifi card nor my tp-link would work. I am running Ubuntu 16.04, but thought the article would help me. 

I had read in the forums that the reason it is not working might be because I have installed possibly conflicting drivers. However, now I am not sure what is messing up my integrated connection since I have blacklisted all these in /etc/modprobe.d/blacklist.conf as shown below and it still does not work.

```

blacklist ath9kblacklist ath9k_htc
blacklist ath9k_common
blacklist ath9k_hw
blacklist ath
blacklist acer-wmi

```

Here are the outputs of commonly requested commands:

lspci -nn

```

00:00.0 Host bridge [0600]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor DRAM Controller [8086:0c04] (rev 06)
00:01.0 PCI bridge [0604]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor PCI Express x16 Controller [8086:0c01] (rev 06)
00:02.0 VGA compatible controller [0300]: Intel Corporation 4th Gen Core Processor Integrated Graphics Controller [8086:0416] (rev 06)
00:03.0 Audio device [0403]: Intel Corporation Xeon E3-1200 v3/4th Gen Core Processor HD Audio Controller [8086:0c0c] (rev 06)
00:14.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB xHCI [8086:8c31] (rev 05)
00:16.0 Communication controller [0780]: Intel Corporation 8 Series/C220 Series Chipset Family MEI Controller #1 [8086:8c3a] (rev 04)
00:1a.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #2 [8086:8c2d] (rev 05)
00:1b.0 Audio device [0403]: Intel Corporation 8 Series/C220 Series Chipset High Definition Audio Controller [8086:8c20] (rev 05)
00:1c.0 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #1 [8086:8c10] (rev d5)
00:1c.1 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #2 [8086:8c12] (rev d5)
00:1c.2 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #3 [8086:8c14] (rev d5)
00:1c.3 PCI bridge [0604]: Intel Corporation 8 Series/C220 Series Chipset Family PCI Express Root Port #4 [8086:8c16] (rev d5)
00:1d.0 USB controller [0c03]: Intel Corporation 8 Series/C220 Series Chipset Family USB EHCI #1 [8086:8c26] (rev 05)
00:1f.0 ISA bridge [0601]: Intel Corporation HM87 Express LPC Controller [8086:8c4b] (rev 05)
00:1f.2 SATA controller [0106]: Intel Corporation 8 Series/C220 Series Chipset Family 6-port SATA Controller 1 [AHCI mode] [8086:8c03] (rev 05)
00:1f.3 SMBus [0c05]: Intel Corporation 8 Series/C220 Series Chipset Family SMBus Controller [8086:8c22] (rev 05)
01:00.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Neptune XT [Radeon HD 8970M] [1002:6801] (rev ff)
03:00.0 PCI bridge [0604]: Texas Instruments XIO2213A/B/XIO2221 PCI Express to PCI Bridge [Cheetah Express] [104c:823e] (rev 01)
04:00.0 FireWire (IEEE 1394) [0c00]: Texas Instruments XIO2213A/B/XIO2221 IEEE-1394b OHCI Controller [Cheetah Express] [104c:823f] (rev 01)
05:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTL8411 PCI Express Card Reader [10ec:5289] (rev 01)
05:00.2 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 0a)
06:00.0 Network controller [0280]: Intel Corporation Wireless 7260 [8086:08b1] (rev 73)



```


sudo lshw -C network

```

*-network               
       description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0.2
       bus info: pci@0000:05:00.2
       logical name: eth0
       version: 0a
       serial: 00:90:f5:ef:4d:49
       size: 1Gbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full firmware=rtl8411-1_0.0.3 06/18/12 ip=192.168.1.72 latency=0 link=yes multicast=yes port=MII speed=1Gbit/s
       resources: irq:27 ioport:d000(size=256) memory:f0004000-f0004fff memory:f0000000-f0003fff
  *-network
       description: Network controller
       product: Wireless 7260
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:06:00.0
       version: 73
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: driver=iwlwifi latency=0
       resources: irq:32 memory:f7800000-f7801fff

```


rfkill list all

```

0: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no

```


ifconfig

```

eth0      Link encap:Ethernet  HWaddr 00:90           inet addr:192.1 Bcast:192.16  Mask:255.255.255.0
          inet6 addr: fe80:d/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:247667 errors:0 dropped:0 overruns:0 frame:0
          TX packets:52039 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:356286376 (356.2 MB)  TX bytes:4904430 (4.9 MB)


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:1584 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1584 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:127816 (127.8 KB)  TX bytes:127816 (127.8 KB)

```

iwconfig

```

lo        no wireless extensions.

eth0      no wireless extensions.



```

Thank you very much! I appreciate any help I can get at this point! I was contemplating trying running the following commands as suggested by an answer on this threat: [https://askubuntu.com/questions/260562/ubuntu-12-10-wireless-problem-only-showing-me-bluetooth-option](https://askubuntu.com/questions/260562/ubuntu-12-10-wireless-problem-only-showing-me-bluetooth-option). Please let me know if you have other questions. Sorry for the long post, but I wanted to be as thorough as possible.

```

sudo apt-get install linux linux-headers-generic kernel-package
sudo apt-get purge b43-fwcutter firmware-b43-installer firmware-b43-lpphy-installer firmware-b43legacy-installer bcmwl* 
sudo apt-get install b43-fwcutter firmware-b43-lpphy-installer bcmwl*
```

---

### Post by praseodym on 2017-07-06
Hi,

blacklisting Atheros driver is done automatically during install because you have an internal Intel card, driver **iwlwifi**

Installing Broadcom Firmware is not making sense, but, it is not harmful, too. Lets check
```
uname -a
lsmod
lsusb
```
Those backported drivers are way too old, lets wait for the outputs of those commands to know the chipset of that stick

---

