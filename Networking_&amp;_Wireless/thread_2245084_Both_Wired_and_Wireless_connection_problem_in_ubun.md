---
title: "Both Wired and Wireless connection problem in ubuntu 13.10 64-bit"
date: 2014-09-21
forum: Networking &amp; Wireless
---

### Post by Ila_Rana on 2014-09-21
Hello,

I fed up with ubuntu 13.10.

I have dual os in Lenovo Z580 ideapad laptop. One is Window 7 64-bit. other one is 13.10 64-bit.

In window 7, both wired and wireless connection working fine.

But in ubuntu 13.10 no networking at all.

Following are the outputs after run several commands.

1> uname -mr
   3.11.0-26-generic x86_64


2> ifconfig -a
erp@erp-Lenovo-Z580:~$ ifconfig -a
lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:202 errors:0 dropped:0 overruns:0 frame:0
          TX packets:202 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:66465 (66.4 KB)  TX bytes:66465 (66.4 KB)

3> nm-tool
erp@erp-Lenovo-Z580:~$ nm-tool
NetworkManager Tool
State: disconnected


4> route -n
erp@erp-Lenovo-Z580:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface


5> cat /var/lib/NetworkManager/NetworkManager.state
erp@erp-Lenovo-Z580:~$ cat /var/lib/NetworkManager/NetworkManager.state
[main]
NetworkingEnabled=true
WirelessEnabled=true
WWANEnabled=true
WimaxEnabled=true
erp@erp-Lenovo-Z580:~$ 






6> cat /etc/NetworkManager/NetworkManager.conf
cat /etc/NetworkManager/NetworkManager.conf
[main]
plugins=ifupdown,keyfile,ofono
dns=dnsmasq


no-auto-default=08:9E:01:DB:8C:CC,


[ifupdown]
managed=true


7> cat /etc/network/interfaces
erp@erp-Lenovo-Z580:~$ cat /etc/network/interfaces
# interfaces(5) file used by ifup(8) and ifdown(8)
auto lo
auto eth0
iface lo inet loopback




8> dmesg | grep -i dhclient
erp@erp-Lenovo-Z580:~$ dmesg | grep -i dhclient
[   18.577508] type=1400 audit(1411281817.601:2): apparmor="STATUS" operation="profile_load" parent=544 profile="unconfined" name="/sbin/dhclient" pid=580 comm="apparmor_parser"
[   18.577519] type=1400 audit(1411281817.601:4): apparmor="STATUS" operation="profile_load" parent=544 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=580 comm="apparmor_parser"
[   18.578026] type=1400 audit(1411281817.601:6): apparmor="STATUS" operation="profile_replace" parent=544 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=580 comm="apparmor_parser"
[   18.578299] type=1400 audit(1411281817.601:7): apparmor="STATUS" operation="profile_replace" parent=544 profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=580 comm="apparmor_parser"
[   21.825788] type=1400 audit(1411281820.845:11): apparmor="STATUS" operation="profile_replace" parent=785 profile="unconfined" name="/sbin/dhclient" pid=793 comm="apparmor_parser"




9> sudo ethtool eth0
erp@erp-Lenovo-Z580:~$ sudo ethtool eth0
Settings for eth0:
Cannot get device settings: No such device
Cannot get wake-on-lan settings: No such device
Cannot get message level: No such device
Cannot get link status: No such device
No data available




10> lspci 
erp@erp-Lenovo-Z580:~$ lspci 
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8101E/RTL8102E PCI Express Fast Ethernet controller (rev 05)
03:00.0 Network controller: Broadcom Corporation BCM4313 802.11bgn Wireless Network Adapter (rev 01)




11> erp@erp-Lenovo-Z580:~$ sudo lshw -C network
  *-network UNCLAIMED     
       description: Ethernet controller
       product: RTL8101E/RTL8102E PCI Express Fast Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 05
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list
       configuration: latency=0
       resources: ioport:2000(size=256) memory:f0404000-f0404fff memory:f0400000-f0403fff
  *-network UNCLAIMED
       description: Network controller
       product: BCM4313 802.11bgn Wireless Network Adapter
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress bus_master cap_list
       configuration: latency=0
       resources: memory:f0500000-f0503fff


12> sudo nano /etc/resov.confg


# Generated by resolvconf
nameserver 8.8.8.8
nameserver 8.8.4.4


13> erp@erp-Lenovo-Z580:~$ iwconfig
lo        no wireless extensions.


14> erp@erp-Lenovo-Z580:~$ rfkill list
0: ideapad_wlan: Wireless LAN
    Soft blocked: no
    Hard blocked: no
1: ideapad_bluetooth: Bluetooth
    Soft blocked: no
    Hard blocked: no
2: hci0: Bluetooth
    Soft blocked: no
    Hard blocked: no


Please give me exact solution that what to do with this problem.

Thanks,
Ila Rana

---

### Post by varunendra on 2014-09-21
Hello Ila Rana, Welcome to the forums!

The request for "exact solution" scared me a bit, but I'll try nonetheless :p

First things first - 13.10 has reached its [End of Life]("https://wiki.ubuntu.com/Releases"), means it is no more supported. You should download a fresh ISO of either 12.04.4 or 14.04.1 > test it in live mode > do a clean install if satisfied.

For downloading the ISOs, it is highly recommended to use torrents to ensure not only faster download, but also the integrity of the downloaded data. Official torrent links can be found here : [http://www.ubuntu.com/download/alternative-downloads](http://www.ubuntu.com/download/alternative-downloads)

By the way, both your ethernet and wireless cards should have been supported natively. So unless you manually blacklisted the drivers or prevented them from loading some other way, it looks like a broken installation anyway.

You may try to manually download the kernel from [here]("http://archive.ubuntu.com/ubuntu/pool/main/l/linux/") (the package you want is "linux-image-3.11.0-26-generic_3.11.0-26.45_amd64.deb") , and installing it again with a double-click or "*dpkg -i linux-image-3.11.0-26-generic_3.11.0-26.45_amd64.deb*" command, but again, it is highly recommended to do a clean install of a supported version instead.

**PS:**
Terminal commands & outputs should always be posted within '**Code**' tags to preserve their formatting and make the post compact and more readable. To see a quick 'HowTo' with screenshots, please follow the "Use Code Tags" link in my signature.

---

### Post by lisati on 2014-09-21
Hi, and welcome to the forums.

We highly recommend upgrading to a newer release, as our ability to support EOL releases is limited. Please read the information here: [http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

---

### Post by Ila_Rana on 2014-09-21
Hello Varun,

Thank you for reply. But rightnow, I cant upgrade to 14.04. There many libraries which are not compatible with 14.04. 
and I tried with your solution. I installed same version for kernel. and Also  try with reinstalling that thing. But there 
is no change in system. And in 12.04 still few libraries is not supported. So I need to stick with current system. Everything
working properly before 4-5 days. But when I try to get increase speed of wifi in this system. Everything is gone.

Help to get out for this problem. 

Thanks,
Ila

---

### Post by mörgæs on 2014-09-21
What exactly is not compatible with 14.04?

---

### Post by varunendra on 2014-09-23
Please answer the question, if you can, that mörgæs asked.

For the speed issue, maybe a report of the [wireless_script]("http://ubuntuforums.org/showpost.php?p=13024222") could help.

---

