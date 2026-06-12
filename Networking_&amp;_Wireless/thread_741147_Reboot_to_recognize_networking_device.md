---
title: "Reboot to recognize networking device?"
date: 2008-03-31
forum: Networking &amp; Wireless
---

### Post by gfunkdave on 2008-03-31
I'm running Gutsy on a Thinkpad T60.

When I boot the machine without an ethernet cord plugged in, it recognizes the wireless card just fine and I connect via wireless. If I then plug in an ethernet cord, it does not recognize the ethernet card (even though the little twinkly lights on the ethernet NIC are on), In order to get ethernet connectivity, I have to reboot the machine. And then I can't connect wirelessly until I unplug the ethernet cord and reboot.

I've tried sudo /etc/init.d/networking restart and it doesn't help.

Here's my /etc/networking/interfaces file, which seems to show that Ubuntu doesn't recognize the network card unless it's connected:
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


/etc/network/interfaces (END) 

Here's what networking restart gives:

> david@better-mousetrap:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                   [ OK ] 


ifconfig output:

> david@better-mousetrap:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:13:02:70:B0:48  
          inet addr:172.16.254.104  Bcast:172.16.254.255  Mask:255.255.255.0
          inet6 addr: fe80::213:2ff:fe70:b048/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2995 errors:0 dropped:5375 overruns:0 frame:0
          TX packets:3063 errors:0 dropped:1 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:36365118 (34.6 MB)  TX bytes:11254952 (10.7 MB)
          Interrupt:21 Base address:0x4000 Memory:edf00000-edf00fff 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:63 errors:0 dropped:0 overruns:0 frame:0
          TX packets:63 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:145325 (141.9 KB)  TX bytes:145325 (141.9 KB)

david@better-mousetrap:~$ 


...and, iwconfig output:
> 
david@better-mousetrap:~$ iwconfig
lo        no wireless extensions.

eth0      IEEE 802.11g  ESSID:"Process Energy Solutions"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: 00:18:02:29:38:B2   
          Bit Rate:36 Mb/s   Tx-Power:15 dBm   
          Retry limit:15   RTS thr:off   Fragment thr:off
          Power Management:off
          Link Quality=85/100  Signal level=-49 dBm  Noise level=-49 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:5385   Missed beacon:0

david@better-mousetrap:~$ 


Thanks for any advice...I'm sure it's something stupid.

---

### Post by gfunkdave on 2008-03-31
Here's something else I found...it definitely knows that there's an ethernet NIC there, but hasn't activated it.

> 
david@better-mousetrap:~$ lshw -C network
WARNING: you should run this program as super-user.
  *-network UNCLAIMED     
       description: Ethernet controller
       product: 82573L Gigabit Ethernet Controller
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: cap_list
       configuration: latency=0
  *-network
       description: Wireless interface
       product: PRO/Wireless 3945ABG Network Connection
       vendor: Intel Corporation
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: 02
       serial: 00:13:02:70:b0:48
       width: 32 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw3945 driverversion=1.2.2mp.ubuntu1 firmware=14.2 1:0 () ip=172.16.254.104 latency=0 module=ipw3945 multicast=yes wireless=IEEE 802.11g


---

### Post by process91 on 2008-03-31
It seems to me that the wired ethernet card and the wireless are both being accessed as eth0. The wireless should be set up as wl0 or eth1. I'm not an expert, but I would backup your /etc/network/interfaces file and then make it look like this.
> 
auto lo
iface lo inet loopback

iface eth0 inet dhcp
auto eth0

iface eth1 inet dhcp
auto eth1

I'll check my laptop and see if that is how it's setup.

---

### Post by gfunkdave on 2008-03-31
Thanks for the idea...making that change and restarting networking did this:

> 
david@better-mousetrap:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          There is already a pid file /var/run/dhclient.eth0.pid with pid 9133
killed old client process, removed PID file
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

Listening on LPF/eth0/00:13:02:70:b0:48
Sending on   LPF/eth0/00:13:02:70:b0:48
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
DHCPACK from 172.16.254.254
bound to 172.16.254.104 -- renewal in 406193 seconds.
eth1: ERROR while getting interface flags: No such device
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519120
Internet Systems Consortium DHCP Client V3.0.5
Copyright 2004-2006 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/sw/dhcp/](http://www.isc.org/sw/dhcp/)

SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
eth1: ERROR while getting interface flags: No such device
Bind socket to interface: No such device
Failed to bring up eth1.
                                                                         [ OK ]


---

### Post by process91 on 2008-03-31
OK I think I have a clearer understanding of the problem and a possible solution. Can you post the output of this command:

```
ip link show
```

I think both cards are mapped to eth0. If you get the mac address of both cards you can manually map them to whatever you want. For instance, the result of **ip link show **returns this on my machine:

> 1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <NO-CARRIER,BROADCAST,MULTICAST,UP> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:11:d8:ac:6e:b2 brd ff:ff:ff:ff:ff:ff
3: eth1: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:0f:66:1c:e3:b1 brd ff:ff:ff:ff:ff:ff


And my /etc/network/interfaces file looks like this

> auto lo
iface lo inet loopback

auto eth0
mapping eth0 eth1
script /etc/network/scripts/get-mac-address.sh
map 00:11:d8:ac:6e:b2 wifi
map 00:0f:66:1c:e3:b1 wired

iface wifi inet dhcp

iface wired inet dhcp

From your last post, I believe your wifi mac address is **00:13:02:70:b0:48**. Conceivably you could make your /etc/network/interfaces file look like this:

> auto lo
 iface lo inet loopback
 
 auto eth0
 mapping eth0
 script /etc/network/scripts/get-mac-address.sh
 map **00:13:02:70:b0:48** wifi
 
 iface wifi inet dhcp
 
 iface eth0 inet dhcp

But I think it would be better to also map the wired network card, if nothing else than for consistency.

---

### Post by gfunkdave on 2008-03-31
Hmm, all right. This is what ip link show gives:

> 
david@better-mousetrap:~$ ip link show
1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:13:02:70:b0:48 brd ff:ff:ff:ff:ff:ff


You're correct, that MAC is my wireless card. But why doesn't it even map my wired card to eth1? And in fact, if I try to bring the wifi card down, it tells me there's no such thing as eth0!

> 
david@better-mousetrap:~$ sudo ifdown eth0
[sudo] password for david:
ifdown: interface eth0 not configured


And remember, my /etc/network/interfaces file only has the loopback interface - shouldn't it have eth0 at least? I did add the ones you suggested before but it didn't help.

> 
david@better-mousetrap:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


And there is no /etc/network/scripts directory on my machine...

---

### Post by process91 on 2008-03-31
This makes sense, I didn't notice it before but if you look in your first post the result of **lshw -C network** shows that your wired connection doesn't have a logical name (eth0, eth1, etc.)

Can you give me the output of the following commands?

```
lshal | grep -B 10 -A 15 Network

ls /sys/class/net/

```

**lshal** will list the Hardware Abstraction Layer information. When I ran the first command I got back the following information:

>   pci.subsys_product_id = 33089  (0x8141)  (int)
  pci.subsys_vendor = 'ASUSTeK Computer Inc.'  (string)
  pci.subsys_vendor_id = 4163  (0x1043)  (int)
  pci.vendor = 'nVidia Corporation'  (string)
  pci.vendor_id = 4318  (0x10de)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_11_d8_ac_6e_b2'
  info.capabilities = {'net', 'net.80203'} (string list)
  info.category = 'net.80203'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_10de_57'  (string)
  info.product = 'Networking Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_11_d8_ac_6e_b2'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)
  linux.sysfs_path = '/sys/class/net/eth0'  (string)
  net.80203.mac_address = 76649623218  (0x11d8ac6eb2)  (uint64)
  net.address = '00:11:d8:ac:6e:b2'  (string)
  net.arp_proto_hw_id = 1  (0x1)  (int)
  net.interface = 'eth0'  (string)
  net.linux.ifindex = 2  (0x2)  (int)
  net.originating_device = '/org/freedesktop/Hal/devices/pci_10de_57'  (string)
  net.physical_device = '/org/freedesktop/Hal/devices/pci_10de_57'  (string)

udi = '/org/freedesktop/Hal/devices/pci_10de_5c'
  info.bus = 'pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)


Basically it's describing what it knows about my onboard NIC. My MAC Address is all over this thing, a few examples below:

udi = '/org/freedesktop/Hal/devices/net_00_11_d8_ac_6e_b2'
  info.udi = '/org/freedesktop/Hal/devices/net_00_11_d8_ac_6e_b2'  (string)
  net.80203.mac_address = 76649623218  (0x11d8ac6eb2)  (uint64)
**  net.address = '00:11:d8:ac:6e:b2'  (string)**

Use the MAC address from **net.address** to map your /etc/network/interfaces file as I described in the last post.

The second command is just there in case you don't get anything returned from the first command or it just returns garbage. Either way please post the output of both commands.

---

### Post by gfunkdave on 2008-03-31
All righty...

> 
david@better-mousetrap:~$ lshal | grep -B 10 -A 15 Network
  pci.product_id = 10194  (0x27d2)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_4227'
  info.bus = 'pci'  (string)
  info.linux.driver = 'ipw3945'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d2'  (string)
  info.product = 'PRO/Wireless 3945ABG Network Connection'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_4227'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 128  (0x80)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.1/0000:03:00.0'  (string)
  pci.product = 'PRO/Wireless 3945ABG Network Connection'  (string)
  pci.product_id = 16935  (0x4227)  (int)
  pci.subsys_product_id = 4112  (0x1010)  (int)
  pci.subsys_vendor = 'Intel Corporation'  (string)
  pci.subsys_vendor_id = 32902  (0x8086)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/net_00_13_02_70_b0_48'
  info.capabilities = {'net', 'net.80211'} (string list)
  info.category = 'net.80211'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_4227'  (string)
  info.product = 'WLAN Interface'  (string)
  info.udi = '/org/freedesktop/Hal/devices/net_00_13_02_70_b0_48'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'net'  (string)


and...

> 
david@better-mousetrap:~$ ls /sys/class/net
eth0  lo


---

### Post by process91 on 2008-03-31
OK, that gives us the same info about the wireless. Try this:

```
lshal | grep -B 10 -A 15 Ethernet
```

---

### Post by gfunkdave on 2008-03-31
Et voila...


> 
david@better-mousetrap:~$ lshal | grep -B 10 -A 15 Ethernet
  pci.product = '82801G (ICH7 Family) PCI Express Port 1'  (string)
  pci.product_id = 10192  (0x27d0)  (int)
  pci.subsys_product_id = 0  (0x0)  (int)
  pci.subsys_vendor_id = 0  (0x0)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_109a'
  info.bus = 'pci'  (string)
  info.parent = '/org/freedesktop/Hal/devices/pci_8086_27d0'  (string)
  info.product = '82573L Gigabit Ethernet Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_109a'  (string)
  info.vendor = 'Intel Corporation'  (string)
  linux.hotplug_type = 2  (0x2)  (int)
  linux.subsystem = 'pci'  (string)
  linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0'  (string)
  pci.device_class = 2  (0x2)  (int)
  pci.device_protocol = 0  (0x0)  (int)
  pci.device_subclass = 0  (0x0)  (int)
  pci.linux.sysfs_path = '/sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0'  (string)
  pci.product = '82573L Gigabit Ethernet Controller'  (string)
  pci.product_id = 4250  (0x109a)  (int)
  pci.subsys_product = 'ThinkPad T60'  (string)
  pci.subsys_product_id = 8193  (0x2001)  (int)
  pci.subsys_vendor = 'Lenovo'  (string)
  pci.subsys_vendor_id = 6058  (0x17aa)  (int)
  pci.vendor = 'Intel Corporation'  (string)
  pci.vendor_id = 32902  (0x8086)  (int)

udi = '/org/freedesktop/Hal/devices/pci_8086_27d8'
  info.bus = 'pci'  (string)
  info.linux.driver = 'HDA Intel'  (string)
  info.parent = '/org/freedesktop/Hal/devices/computer'  (string)
  info.product = '82801G (ICH7 Family) High Definition Audio Controller'  (string)
  info.subsystem = 'pci'  (string)
  info.udi = '/org/freedesktop/Hal/devices/pci_8086_27d8'  (string)


---

### Post by process91 on 2008-03-31
OK It seems like the card is being detected but for whatever reason it doesn't get linked to correctly. Post the output of

```
sudo ls /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/
```

If you see something like "eth0" then we won't have to recompile the driver, just change it to "eth1" and then set up the interfaces file again.

If you get an error indicating that it is not a directory or if there aren't any subdirectories like eth0 or eth1 then we'll have to recompile the e1000 driver. Download the latest driver from [Intel]("http://sourceforge.net/project/showfiles.php?group_id=42302&package_id=54835"). Let me know if you need instructions on compiling.

---

### Post by gfunkdave on 2008-03-31
OK, but only two seconds. :)

---

### Post by process91 on 2008-03-31
You could still run the **sudo modprobe e1000** command to see if it will load. Post any output.

---

### Post by gfunkdave on 2008-03-31
No output...it just ran...

> 
david@better-mousetrap:~$ sudo modprobe e1000
[sudo] password for david:
david@better-mousetrap:~$ 


---

### Post by process91 on 2008-03-31
Does
**ip link show**

now show an additional ethernet controller or not? Also did you take a look at post #11? I know it's different because I edited it...

---

### Post by gfunkdave on 2008-03-31
Nope...guess we need to recompile.

And yeah, I'll need a hand compiling. I can usually do it if there's a makefile but there isn't. :)

> **process91 said:**
> Does
**ip link show**

now show an additional ethernet controller or not? Also did you take a look at post #11? I know it's different because I edited it...

---

### Post by process91 on 2008-03-31
Before we do the recompile, one more thing - can you post the contents of /etc/udev/rules.d/70-persistent-net.rules

---

### Post by gfunkdave on 2008-03-31
> 
david@better-mousetrap:~/Desktop/e1000-7.6.15.5/src$ cat /etc/udev/rules.d/70-persistent-net.rules
# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x4227 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:13:02:70:b0:48", NAME="eth0"

# PCI device 0x8086:0x109a (e1000)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:15:58:2c:83:d6", NAME="eth1"


I did figure out the recompile. Oddly enough, the readme file had instructions. Who knew? 

I missed an instruction in the readme file - and NOW IT'S WORKING! Thanks!

The initial compile didn't seem to work (it gave me an error that seemed to imply there was something wrong with creating the man page for something?). Anyway, I did 
```

sudo modprobe e1000

```

and it didn't work - then I saw I was supposed to do 

```

sudo rmmod e1000
sudo modprobe e1000

```

And now ifconfig gives:

> 
david@better-mousetrap:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:02:70:B0:48  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:32 dropped:189457 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1782064333 (1.6 GB)  TX bytes:338351344 (322.6 MB)
          Interrupt:22 Base address:0x4000 Memory:edf00000-edf00fff 

eth1      Link encap:Ethernet  HWaddr 00:15:58:2C:83:D6  
          inet addr:192.168.1.114  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::215:58ff:fe2c:83d6/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:648 errors:0 dropped:0 overruns:0 frame:0
          TX packets:984 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:100 
          RX bytes:141498 (138.1 KB)  TX bytes:106634 (104.1 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1424 (1.3 KB)  TX bytes:1424 (1.3 KB)


and /etc/network/interfaces gives:
> 
david@better-mousetrap:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback



Not sure why it still doesn't show eth0 and eth1...

Thanks for your help!

---

### Post by process91 on 2008-03-31
Glad to help. Just so you know, the /etc/network/interfaces file doesn't have to contain those two entries. That file will be manipulated by the Network-Manager applet. So you're all set.

---

### Post by tclayton on 2008-06-01
I have been having the exact same problem, I have followed every instruction but still no joy.  I have done the recompile but if I then run "sudo ls /sys/devices/pci0000:00/0000:00:1c.0/0000:02:00.0/net/" I get the error message stating there is no such directory.

Below is the contents of /etc/udev/rules.d/70-persistent-net.rules

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x8086:0x4227 (ipw3945)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1b:77:2f:78:cc", NAME="eth0"

# PCI device 0x8086:0x1049 (e1000)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:1c:25:18:64:03", NAME="eth1"

As you can see it does detect eth0 and eth1 here but if I run "ip link show" I get the following:

1: lo: <LOOPBACK,UP,10000> mtu 16436 qdisc noqueue 
    link/loopback 00:00:00:00:00:00 brd 00:00:00:00:00:00
2: irda0: <NOARP> mtu 2048 qdisc noop qlen 8
    link/irda 00:00:00:00 brd ff:ff:ff:ff
3: eth0: <BROADCAST,MULTICAST,UP,10000> mtu 1500 qdisc pfifo_fast qlen 1000
    link/ether 00:1b:77:2f:78:cc brd ff:ff:ff:ff:ff:ff

No eth1 is shown here.

I have run "sudo rmmod e1000" and "sudo modprobe e1000" both return no output.

My only thoughts as to where it has gone wrong is when I ran "make install" to recompile I got the following output:

tclayton@LINUXLAP:~/Desktop/e1000-8.0.1/src$ sudo make install
[sudo] password for tclayton:
make -C /lib/modules/2.6.22-14-generic/build SUBDIRS=/home/tclayton/Desktop/e1000-8.0.1/src modules
make[1]: Entering directory `/usr/src/linux-headers-2.6.22-14-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.22-14-generic'
# remove all old versions of the driver
find /lib/modules/2.6.22-14-generic -name e1000.ko -exec rm -f {} \; || true
find /lib/modules/2.6.22-14-generic -name e1000.ko.gz -exec rm -f {} \; || true
install -D -m 644 e1000.ko /lib/modules/2.6.22-14-generic/kernel/drivers/net/e1000/e1000.ko
/sbin/depmod -a || true
install -D -m 644 e1000.7.gz /usr/share/man/man7/e1000.7.gz
man -c -P'cat > /dev/null' e1000 || true
man: 
cannot write to /var/cache/man/cat7/e1000.7.gz in catman mode
e1000.


As you can see there is the error at the bottom referring to catman mode, I'm not sure what this means but I read in another forum that it is not important???

If anyone can provide any help I would be very grateful.

---

