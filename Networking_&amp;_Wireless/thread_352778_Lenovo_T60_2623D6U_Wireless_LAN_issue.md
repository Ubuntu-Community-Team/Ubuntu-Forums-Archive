---
title: "Lenovo T60 2623D6U Wireless LAN issue"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by amohanty on 2007-02-03
Hi all,

I have run into a peculiar problem. I have the following:
A Lenovo Thinkpad T60 2623D6U with the Intel 3945ABG wireless lan chip.

I have gotten everything to work (except the ThinkVantage stuff) but for the life of me I cant get the system to even _see_ wlan0. The BIOS is the default setting except for the boot order, everything in the network category is enabled. 

Some useful outputs:

> 
$ lspci
...
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 7149
02:00.0 Ethernet controller: Intel Corporation 82573L Gigabit Ethernet Controller
**03:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG Network Connection (rev 02)**
15:00.0 CardBus bridge: Texas Instruments PCI1510 PC card Cardbus Controller


> 
$ lshw -C network
WARNING: you should run this program as super-user.
  *-network               
       description: Ethernet interface
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@02:00.0
       logical name: eth0
       version: 00
       serial: 00:16:41:e1:06:ef
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=e1000 ip=192.168.0.6 multicast=yes
       resources: iomemory:ee000000-ee01ffff ioport:3000-301f irq:169
  *-network
       description: Network controller
       product: **PRO/Wireless 3945ABG Network Connection**
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@03:00.0
       version: 02
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: driver=ipw3945
       resources: iomemory:edf00000-edf00fff irq:74


Emphasis mine. So as you can see it does detect the hardware.

However:

> 
$ iwconfig
lo        no wireless extensions.

eth0      no wireless extensions.

irda0     no wireless extensions.

sit0      no wireless extensions.



> 
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:16:41:E1:06:EF  
          inet addr:192.168.0.6  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::216:41ff:fee1:6ef/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1492  Metric:1
          RX packets:4356 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3644 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:4679149 (4.4 MiB)  TX bytes:530226 (517.7 KiB)
          Base address:0x3000 Memory:ee000000-ee020000 

irda0     Link encap:IrLAP  HWaddr 00:00:00:00  
          NOARP  MTU:2048  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:8 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:2 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:100 (100.0 b)  TX bytes:100 (100.0 b)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)


the network system does not seem to pick it up.

What I tried:

1. Per [http://www.linux.org.mt/node/82]("http://www.linux.org.mt/node82") (the original source of the thinkwiki article) I installed network-manager and network-manager-gnome. I get the icon on the bottom right, however it doesn't show the wireless options. Perhaps a different model issue. So no-go on that solution.

2. Downloaded [ XP Pro driver from intel]("http://downloadcenter.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Windows*+XP+Professional&lang=eng&strOSs=44&submit=Go%21#DRI"), and used ndiswrapper to install it per[ wiki instructions]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper"). Everything went smoothly, however no wlan0 created in /etc/network/interfaces. And I cant ifup it. Cant add it to th elist and if after that. Cant do pretty much anything regarding wlan0. So no-go there too.

What I have not tried:

1. Download [linux drivers from intel]("http://downloadcenter.intel.com/scripts-df-external/filter_results.aspx?strTypes=all&ProductID=2259&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21#DRI") and try installing them. Will be trying it out next, unless it requires a kernel rebuild in which case see (2).

2. Use the [open-source drivers]("http://ipw3945.sourceforge.net/"). I don't think I will be trying that because per the instructions that requires a kernel rebuild and I don't want to have to do that every time I upgrade my kernel.

I was wondering if there are any network gurus out there, who can help out with this. 
Any help would be greatly appreciated.

Thanks.
AM

---

### Post by amohanty on 2007-02-04
bump !! some help please

---

### Post by amohanty on 2007-02-08
I actually thought that I had the ipw3945d daemon, but per:

[https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62452](https://launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/62452)

apparently not. I also thought that I had installed the linux-restricted-modules-generic package as part of the process to get fglrx drivers for ati going... but apparently not. 

Any way, just install the linux-restricted-modules-generic and then launch ipw3945...d

and wireless should be up and running.

AM

---

### Post by banditti on 2007-02-08
as a point of reference:

[http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60](http://www.thinkwiki.org/wiki/Installing_Ubuntu_6.10_(Edgy_Eft)_on_a_ThinkPad_T60)

---

### Post by banditti on 2007-02-08
might not apply to your issue, but I followed the wireless section in the link above to get wireless working.

---

