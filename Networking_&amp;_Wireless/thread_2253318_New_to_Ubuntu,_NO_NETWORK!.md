---
title: "New to Ubuntu, NO NETWORK!"
date: 2014-11-18
forum: Networking &amp; Wireless
---

### Post by sina3 on 2014-11-18
Hey ladies and gents,

I just recently installed Ubuntu and I was really enjoying it until I realized that I can't connect to the internet. I've tried many different options in order to establish a wired connection but nothing (except for mobile tethering -.-) seems to work. 

I really want to give Ubuntu a shot (this is my first Linux-platform)  but since my first couple of hours in Ubuntu was spent trying to fix this error I have to say I'm tempted to run back to Windows 7 :neutral:. 


Some info:
```

  description: Ethernet interface
       product: RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:07:00.0
       logical name: eth0
       version: 06
       serial: 50:e5:49:c4:ec:76
       size: 100Mbit/s
       capacity: 1Gbit/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8168 driverversion=8.039.00-NAPI duplex=full latency=0 link=yes multicast=yes port=twisted pair speed=100Mbit/s
       resources: irq:43 ioport:de00(size=256) memory:fbdff000-fbdfffff memory:fbdf8000-fbdfbfff


  *-network
       description: Ethernet interface
       physical id: 1
       logical name: usb0
       serial: 02:05:30:66:32:30
       capabilities: ethernet physical
       configuration: broadcast=yes driver=rndis_host driverversion=22-Aug-2005 firmware=RNDIS device ip=192.168.42.28 link=yes multicast=yes

```

More info:

```
$ ifconfig
eth0      Link encap:Ethernet  HWaddr 50:e5:49:c4:ec:76  
          inet addr:195.67.213.169  Bcast:195.67.213.255  Mask:255.255.255.128
          inet6 addr: fe80::52e5:49ff:fec4:ec76/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:8 errors:0 dropped:0 overruns:0 frame:0
          TX packets:902 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1304 (1.3 KB)  TX bytes:84626 (84.6 KB)
          Interrupt:43 Base address:0x6000 


lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:2405 errors:0 dropped:0 overruns:0 frame:0
          TX packets:2405 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:186990 (186.9 KB)  TX bytes:186990 (186.9 KB)


usb0      Link encap:Ethernet  HWaddr 02:05:30:66:32:30  
          inet6 addr: fe80::5:30ff:fe66:3230/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:17766 errors:3 dropped:0 overruns:0 frame:3
          TX packets:13658 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:18664849 (18.6 MB)  TX bytes:2288815 (2.2 MB)

```

I tried downloading drivers from here [http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2](http://www.realtek.com.tw/Downloads/downloadsView.aspx?Langid=1&PNid=13&PFid=5&Level=5&Conn=4&DownTypeID=3&GetDown=false#2) and when I install them I get these messages:
```
$ sudo ./autorun.sh

Check old driver and unload it.
rmmod r8168
Build the module and install
Can't read private key
DEPMOD 3.13.0-32-generic
load module r8168
Updating initramfs. Please wait.
update-initramfs: Generating /boot/initrd.img-3.13.0-32-generic
Completed.

```


So basically I can see the wired connection, but I'm not connected to the internet. 

Please help!

PS. I didn't have network connection when installing Ubuntu so I didn't get some updates that would probably be useful.

---

### Post by chili555 on 2014-11-19
May we see:```
nm-tool
dmesg | grep -e eth -e r816
lsmod | grep r816
```Thanks.

---

### Post by SeijiSensei on 2014-11-20
Also the results of the command "route -n" would help.

---

