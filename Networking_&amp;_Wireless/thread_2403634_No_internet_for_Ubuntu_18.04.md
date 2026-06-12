---
title: "No internet for Ubuntu 18.04"
date: 2018-10-14
forum: Networking &amp; Wireless
---

### Post by willem-v on 2018-10-14
Hello colleague's,

I've a problem with the modem. I can produce an internet-connect with Windows, Firefox and the same... modem. When I'm using the Ubuntu 18.04 also with Firefox, the modem says : "No internet is possible : DHCP-v4 : "error 2 : no answer on DISCOVER".  I've used other kernels, Ubuntu 14.04 and Ubuntu 10, but it give the same results.

What could be the cause of this?

> ifconfig :

eth0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.178.21  netmask 255.255.255.0  broadcast 192.168.178.255
        inet6 fe80::baae:edff:fe36:f401  prefixlen 64  scopeid 0x20<link>
        inet6 2001:981:7e91:1:baae:edff:fe36:f401  prefixlen 64  scopeid 0x0<global>
        ether b8:ae:ed:36:f4:01  txqueuelen 1000  (Ethernet)
        RX packets 265  bytes 59733 (59.7 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 172  bytes 18643 (18.6 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 6553  bytes 453397 (453.3 KB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 6553  bytes 453397 (453.3 KB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

---

### Post by praseodym on 2018-10-14
Hi,

is it a PPPoE connection with Login and password? If yes, try
```

sudo pppoeconf
```
add your Login/PW and answer all other questions with Yes or Ok

---

### Post by kc1di on 2018-10-14
Hello willem-v  and welcome to Ubuntu,

Please give us a little more info to go on.  What modem or card is being use are we looking at a wireless connection or Ethernet?  
If you can go to a terminal in Ubuntu enter these commands one at a time and post the results back here.

```
inxi -Nn
```
```
lspci -nnk | grep -iA2 net
```

---

### Post by willem-v on 2018-10-14
>> dpkg -s pppoeconf

Package: pppoeconf
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 132
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Version: 1.21ubuntu1
Depends: whiptail-provider | whiptail, ppp (>= 2.4.2+20040428-2) | pppoe (>= 3.0), ppp (>= 2.4.1.uus2-4), gettext-base (>= 0.13), sed (>= 3.95), ifupdown (>= 0.7.44~), iproute2
Recommends: locales
Suggests: xdialog
Description: configures PPPoE/ADSL connections
 User-friendly tool for initial configuration of a DSL (PPPoE) connection.
Original-Maintainer: Gregory Colpart <reg@debian.org>

> apt install pppoeconf

pc says : "pppoeconf is already the newest version (1.21ubuntu1)"

when I type in pppoeconf, the pc says

"Concentrator of your provider did not RESPOND. Please
check your network and modem cables. Another reason for
the scan failure may also be another running pppoe 
process which controls the modem"

---

### Post by willem-v on 2018-10-14
> inxi -Nn

I don't have it on my Ubuntu.  Is this important, then I download it with Windows.

> lspci -nnk | grep -iA2 net :

02:00.0 EtherNET controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit EtherNET Controller [10ec:8168] (rev 0c)
    Subsystem: Elitegroup Computer Systems RTL8111/8168/8411 PCI Express Gigabit EtherNET Controller [1019:8116]
    Kernel driver in use: r8169
    Kernel modules: r8169

---

### Post by praseodym on 2018-10-14
Download these files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.046.00-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.046.00-1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.3-3ubuntu9_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.3-3ubuntu9_all.deb)

Installation:

```
sudo dpkg -i ~/Downloads/*.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. This changes the driver

---

### Post by willem-v on 2018-10-14
> **praseodym said:**
> Download these files and save them in "Downloads":

[http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.046.00-1_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/universe/r/r8168/r8168-dkms_8.046.00-1_all.deb)

[http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.3-3ubuntu9_all.deb](http://de.archive.ubuntu.com/ubuntu/pool/main/d/dkms/dkms_2.3-3ubuntu9_all.deb)

Installation:

```
sudo dpkg -i ~/Downloads/*.deb
echo "blacklist r8169" | sudo tee -a /etc/modprobe.d/blacklist.conf 
```
Reboot. This changes the driver

PC state :

"Concentrator of your provider did not RESPOND(..)

This is because I have no internet with Ubuntu, btw, it was an upgrade from 14.04 LTS. In that case I can better enter a complete Ubuntu on my disk. 

But, I'll keep it in mind when everything failed.

---

### Post by praseodym on 2018-10-14
Try downloading it somehow, by phone, or so

---

### Post by cjremley on 2018-11-21
I hope this is the right place to inject into the thread.  If not, please let me know.  I have spent hours on this and looked a a lot of threads.

I am having a similar issue but a little different symptom.  When I ping the IP address of my router (192.168.0.1), I get a response.  I can log on the the router from my Linux box, which tells me my network card is working.  I also get a response from 127.0.0.53, the loopback.  However, when I try to ping a DNS server, such as 8.8.8.8, or the DNS of my ISP (24.116.0.53), it times out with no response.  Of course, when I try to look something up from Chrome, I get a DNS error for a few seconds, then says the site isn't available.  That's what sent me down the DNS path. I have other computers on the router which have no issues.  I can't point to a specific event when this started happening.  I recently switched ISPs but I am pretty sure I was able to connect after the change.

I rolled back my driver, as described above and rebooted.  Here is the pertinent outputs which show it was successful:

ifconfig
```
enp5s0: flags=4163<UP,BROADCAST,RUNNING,MULTICAST>  mtu 1500
        inet 192.168.0.107  netmask 255.255.255.0  broadcast 192.168.0.255
        inet6 fe80::a4a8:c51c:e760:3f5e  prefixlen 64  scopeid 0x20<link>
        ether 48:5b:39:80:e7:f3  txqueuelen 1000  (Ethernet)
        RX packets 18635  bytes 6316808 (6.3 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 8742  bytes 1782602 (1.7 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0
        device interrupt 30  base 0x8000  

lo: flags=73<UP,LOOPBACK,RUNNING>  mtu 65536
        inet 127.0.0.1  netmask 255.0.0.0
        inet6 ::1  prefixlen 128  scopeid 0x10<host>
        loop  txqueuelen 1000  (Local Loopback)
        RX packets 134727  bytes 10012658 (10.0 MB)
        RX errors 0  dropped 0  overruns 0  frame 0
        TX packets 134727  bytes 10012658 (10.0 MB)
        TX errors 0  dropped 0 overruns 0  carrier 0  collisions 0

```

lspci -nnk
```
05:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller [10ec:8168] (rev 06)
    Subsystem: ASUSTeK Computer Inc. P8P67 and other motherboards [1043:8432]
    Kernel driver in use: r8168
    Kernel modules: r8168

```

nmcli device show

```
GENERAL.DEVICE:                         enp5s0
GENERAL.TYPE:                           ethernet
GENERAL.HWADDR:                         48:5B:39:80:E7:F3
GENERAL.MTU:                            1500
GENERAL.STATE:                          100 (connected)
GENERAL.CONNECTION:                     Wired connection 2
GENERAL.CON-PATH:                       /org/freedesktop/NetworkManager/ActiveCo
WIRED-PROPERTIES.CARRIER:               on
IP4.ADDRESS[1]:                         192.168.0.107/24
IP4.GATEWAY:                            192.168.0.19
IP4.ROUTE[1]:                           dst = 0.0.0.0/0, nh = 192.168.0.19, mt =
IP4.ROUTE[2]:                           dst = 192.168.0.0/24, nh = 0.0.0.0, mt =
IP4.ROUTE[3]:                           dst = 169.254.0.0/16, nh = 0.0.0.0, mt =
IP4.DNS[1]:                             192.168.0.19
IP4.DNS[2]:                             8.8.8.8
IP4.DNS[3]:                             8.8.4.4
IP4.DNS[4]:                             24.116.0.53
IP6.ADDRESS[1]:                         fe80::a4a8:c51c:e760:3f5e/64
IP6.GATEWAY:                            --
IP6.ROUTE[1]:                           dst = ff00::/8, nh = ::, mt = 256, table
IP6.ROUTE[2]:                           dst = fe80::/64, nh = ::, mt = 256
IP6.ROUTE[3]:                           dst = fe80::/64, nh = ::, mt = 100

GENERAL.DEVICE:                         lo
GENERAL.TYPE:                           loopback
GENERAL.HWADDR:                         00:00:00:00:00:00
GENERAL.MTU:                            65536
GENERAL.STATE:                          10 (unmanaged)
GENERAL.CONNECTION:                     --
GENERAL.CON-PATH:                       --
IP4.ADDRESS[1]:                         127.0.0.1/8
IP4.GATEWAY:                            --
IP6.ADDRESS[1]:                         ::1/128
IP6.GATEWAY:                            --

```

I have tried various combinations of the netplan yaml.  I run netplan --debug generate / apply sequence after each experiment.  None of these worked.

I tried to put extra lines in which define the connection and the nameserver addresses.  It would not generate and gave me an error when trying to generate the netplan on line three.  The error is shown below.  I am not sure why this context error is generated.  As shown, I fails on line three.

.yaml
```
network:
  version: 2
  renderer: NetworkManager
  ethernets:
    enp5s0:
       dhcp4: yes
       nameservers:
        addresses: [8.8.8.8,8.8.4.4]

```

I did create a yaml which assigned a static address in the router.  When I pinged 8.8.8.8, it gave a response:

```
From 192.168.0.107 icmp_seq=1 Destination Host Unreachable

```

I saw something about starting and stopping the NetworkManager.  I wasn't sure if something needed to be disabled depending on which renderer I was using.  I brought is down and brought it up.  It appears to be running based on the nmcli output.  I have also rebooted, especially when I rolled the driver back.

With all the threads about this issue, I assume this is a problem with the configuration in Linux Ubuntu 18.04, not a hardware or router issue.  Being able to ping my router reinforces that assumption.

I have tried to be thorough and demonstrate I have researched and tried many things.  I would appreciate some help.  I feel like my Linux box is a door stop without a network connection.

BTW, I used the code format to show my output.  It put an annoying label at the top of the box.  If I am using the wrong formatting for output, let me know which one I should be using.

Thanks

---

