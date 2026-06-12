---
title: "Activating wireless driver."
date: 2010-12-30
forum: New to Ubuntu
---

### Post by sunde887 on 2010-12-30
I have a Toshiba L655.

I am trying to get the wireless internet working, searching around, I found a link explaining how to get an install the driver needed.

[http://www.ge.ubuntuforums.org/showthread.php?t=1608908](http://www.ge.ubuntuforums.org/showthread.php?t=1608908)

Post 5 is what I followed.

after running:
```

sudo add-apt-repository ppa:lexical/hwe-wireless
sudo apt-get update
sudo apt-get install rtl8192ce-dkm

```
I ran 
lspci -v

and under network it removed unclaimed.

```

02:00.0 Network controller: Realtek Semiconductor Co., Ltd. Device 8176 (rev 01)
    Subsystem: Realtek Semiconductor Co., Ltd. Device 8185
    Flags: bus master, fast devsel, latency 0, IRQ 10
    I/O ports at 3000 [size=256]
    Memory at d4400000 (64-bit, non-prefetchable) [size=16K]
    Capabilities: <access denied>
    Kernel modules: r8192ce_pci

```I also had the program for additional drivers, when I open it

for the driver named: Linux driver for Realtek RTL819x Wifi cards
it says : this driver is activated but not currently in use.

I tried deactivating and reactivating it and restarting but that didn't work.

What can I do to get this driver working correctly?

---

### Post by nothingspecial on 2010-12-30
Hi,

Did you try with a wired internet connection?

---

### Post by sunde887 on 2010-12-30
Yes, Im posting from ubuntu on a wired connection right now.

---

### Post by nothingspecial on 2010-12-30
Try downloading the module in post 3 of the link you posted.

Make sure it is the right one for your card.

Choose to open it with archive manager.

Extract it to your Desktop

Then
```

cd ~/Desktop/rtl8192ce_linux_2.6.0005.1116.2010
make
sudo make install 
```

---

### Post by sunde887 on 2010-12-30
```

make[1]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  Building modules, stage 2.
  MODPOST 1 modules
make[1]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make[1]: Entering directory `/home/kenny/Desktop/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192'
make -C /lib/modules/2.6.35-24-generic/build M= CC=gcc modules
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/basic/hash
  HOSTCC  scripts/kconfig/conf.o
scripts/kconfig/conf.c: In function ‘conf_askvalue’:
scripts/kconfig/conf.c:105: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
scripts/kconfig/conf.c: In function ‘conf_choice’:
scripts/kconfig/conf.c:307: warning: ignoring return value of ‘fgets’, declared with attribute warn_unused_result
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/conf
scripts/kconfig/conf -s arch/x86/Kconfig
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make[2]: Entering directory `/usr/src/linux-headers-2.6.35-24-generic'
  CHK     include/linux/version.h
  CHK     include/generated/utsrelease.h
  UPD     include/generated/utsrelease.h
make[3]: *** No rule to make target `kernel/bounds.c', needed by `kernel/bounds.s'.  Stop.
make[2]: *** [prepare0] Error 2
make[2]: Leaving directory `/usr/src/linux-headers-2.6.35-24-generic'
make[1]: *** [modules] Error 2
make[1]: Leaving directory `/home/kenny/Desktop/rtl8192ce_linux_2.6.0005.1116.2010/HAL/rtl8192'
make: *** [install] Error 2

```

is what I got from sudo make install.

---

### Post by nothingspecial on 2010-12-30
Try this

```
sudo apt-get install build-essential
```Then try again.

Bed for me now. Hopefully someone will pitch in.

---

### Post by sunde887 on 2010-12-30
Still producing the same results when running sudo make install.

i ran ```
 lshw -class network
``````

 *-network UNCLAIMED     
       description: Network controller
       product: Realtek Semiconductor Co., Ltd.
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       version: 01
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list
       configuration: latency=0
       resources: ioport:3000(size=256) memory:d4400000-d4403fff
  *-network
       description: Ethernet interface
       product: AR8152 v1.1 Fast Ethernet
       vendor: Atheros Communications
       physical id: 0
       bus info: pci@0000:03:00.0
       logical name: eth0
       version: c1
       serial: 60:eb:69:72:4f:f7
       width: 64 bits
       clock: 33MHz
       capabilities: bus_master cap_list ethernet physical
       configuration: broadcast=yes driver=atl1c driverversion=1.0.0.2-NAPI firmware=N/A ip=192.168.1.123 latency=0 multicast=yes
       resources: irq:46 memory:d3400000-d343ffff ioport:2000(size=128)

``````

ifconfig
iwconfig
route -n
ping -c 3 208.67.219.101
ping -c 3 www.opendns.com
```produces:

```

eth0      Link encap:Ethernet  HWaddr 60:eb:69:72:4f:f7  
          inet addr:192.168.1.123  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::62eb:69ff:fe72:4ff7/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:93785 errors:1 dropped:0 overruns:0 frame:1
          TX packets:62158 errors:0 dropped:0 overruns:0 carrier:5
          collisions:0 txqueuelen:1000 
          RX bytes:129162972 (129.1 MB)  TX bytes:5927273 (5.9 MB)
          Interrupt:46 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:26 errors:0 dropped:0 overruns:0 frame:0
          TX packets:26 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1534 (1.5 KB)  TX bytes:1534 (1.5 KB)

``````

lo        no wireless extensions.

eth0      no wireless extensions.


``````
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
192.168.1.0     0.0.0.0         255.255.255.0   U     1      0        0 eth0
169.254.0.0     0.0.0.0         255.255.0.0     U     1000   0        0 eth0
0.0.0.0         192.168.1.1     0.0.0.0         UG    0      0        0 eth0

``````

PING 208.67.219.101 (208.67.219.101) 56(84) bytes of data.

--- 208.67.219.101 ping statistics ---
3 packets transmitted, 0 received, 100% packet loss, time 2003ms


``````

PING www.opendns.com (208.69.38.150) 56(84) bytes of data.
64 bytes from 208.69.38.150: icmp_req=1 ttl=50 time=89.4 ms
64 bytes from 208.69.38.150: icmp_req=2 ttl=50 time=89.9 ms
64 bytes from 208.69.38.150: icmp_req=3 ttl=50 time=88.1 ms

--- www.opendns.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 10334ms
rtt min/avg/max/mdev = 88.128/89.163/89.937/0.799 ms

```

I had windows shutting off network device when turned off, I removed this option and it still didn't recognize it.

---

