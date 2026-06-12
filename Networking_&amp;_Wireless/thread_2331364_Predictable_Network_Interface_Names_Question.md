---
title: "Predictable Network Interface Names Question"
date: 2016-07-21
forum: Networking &amp; Wireless
---

### Post by dfuerpo on 2016-07-21
This is more of an observation about Predictable Network Interface Names (PNIN). It is my understanding that this first appeared in Ubuntu 15.10 because of a change in systemd ([https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)). This means the traditional network interface names like eth0, eth1, wlan0 etc. are replaced by something, well…less obvious.

I recently made these observations on three Ubuntu 16.04 installs. 

The first is a standard Ubuntu 16.04 desktop running in a VMware Fusion VM on a Mac:

```
gary@ubuntu:~$ dmesg | grep eth
[    1.900145] e1000 0000:02:01.0 eth0: (PCI:66MHz:32-bit) 00:0c:29:de:16:44
[    1.900154] e1000 0000:02:01.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.903562] e1000 0000:02:01.0 ens33: renamed from eth0

```

Pretty straightforward; ens33 is not much harder to remember than eth0.

The second install is a standalone (non-virtual) Ubuntu 16.04 Server on standard Intel hardware with two ethernet interfaces; one on the motherboard and another in a PCIe slot.

```
doug@snort:~$ dmesg | grep -i eth
[    3.575997] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.589910] r8169 0000:01:00.0 eth0: RTL8168e/8111e at 0xf8442000, ec:08:6b:05:c4:ae, XID 0c200000 IRQ 33
[    3.617698] r8169 0000:01:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    3.767697] r8169 0000:01:00.0 enp1s0: renamed from eth0
[    4.210014] e1000e 0000:00:19.0 eth0: registered PHC clock
[    4.222654] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:30:18:ad:3d:a4
[    4.430910] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    4.444583] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    4.459631] e1000e 0000:00:19.0 eno1: renamed from eth0

doug@snort:~$ ifconfig
eno1      Link encap:Ethernet  HWaddr 00:30:18:ad:3d:a4  
          inet addr:192.168.0.61  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::230:18ff:fead:3da4/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:43961 errors:0 dropped:0 overruns:0 frame:0
          TX packets:19629 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:52455832 (52.4 MB)  TX bytes:1551704 (1.5 MB)
          Interrupt:20 Memory:f7e00000-f7e20000 

enp1s0    Link encap:Ethernet  HWaddr ec:08:6b:05:c4:ae  
          inet addr:192.168.0.68  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::ee08:6bff:fe05:c4ae/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:6358 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1109154 (1.1 MB)  TX bytes:1332 (1.3 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:160 errors:0 dropped:0 overruns:0 frame:0
          TX packets:160 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1 
          RX bytes:11840 (11.8 KB)  TX bytes:11840 (11.8 KB)
```

Still not too difficult to understand. It is interesting though that the kernel recognizes both initially as eth0, presumable because the first interface (the RTL8168e) has already been renamed to enp1s0 before the Intel PRO/1000 is enumerated and then renamed from eth0 to eno1.

But now things get more interesting. The next install is Ubuntu 16.04 armv7l running on a Raspberry Pi model 2. This device has the built-in ethernet and a USB D-Link DWA-121 wifi adapter based on the Realtek RTL8188CUS chip. The built-in ethernet in also on the USB bus (which I didn’t know until I looked) and is based on the SMSC9512/9514 chip. See below:

```
doug@Raspi-Ubuntu:~$ uname -a && lsb_release -a
Linux Raspi-Ubuntu 4.1.19-v7+ #858 SMP Tue Mar 15 15:56:00 GMT 2016 armv7l armv7l armv7l GNU/Linux
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 16.04.1 LTS
Release:    16.04
Codename:    xenial

doug@Raspi-Ubuntu:~$ dmesg | grep -e 'rtl\|smsc'
[    0.000000] Kernel command line: dma.dmachans=0x7f35 bcm2708_fb.fbwidth=656 bcm2708_fb.fbheight=416 bcm2709.boardrev=0xa21041 bcm2709.serial=0xaed8e6df smsc95xx.macaddr=B8:27:EB:D8:E6:DF bcm2708_fb.fbdepth=32 bcm2708_fb.fbswap=1 bcm2709.uart_clock=3000000 bcm2709.disk_led_gpio=47 bcm2709.disk_led_active_low=0 vc_mem.mem_base=0x3dc00000 vc_mem.mem_size=0x3f000000  dwc_otg.lpm_enable=0 console=tty1 root=/dev/mmcblk0p2 rootfstype=ext4 elevator=deadline rootwait quiet splash
[    0.342484] usbcore: registered new interface driver smsc95xx
[    1.706438] smsc95xx v1.0.4
[    1.767308] smsc95xx 1-1.1:1.0 eth0: register 'smsc95xx' at usb-3f980000.usb-1.1, smsc95xx USB 2.0 Ethernet, b8:27:eb:d8:e6:df
[    7.197057] smsc95xx 1-1.1:1.0 enxb827ebd8e6df: renamed from eth0
[    7.421672] usbcore: registered new interface driver rtl8192cu
[    7.454092] rtl8192cu 1-1.3:1.0 enxb8a3868ee9df: renamed from wlan0
[    9.567704] smsc95xx 1-1.1:1.0 enxb827ebd8e6df: hardware isn't capable of remote wakeup

doug@Raspi-Ubuntu:~$ ifconfig
enxb827ebd8e6df Link encap:Ethernet  HWaddr b8:27:eb:d8:e6:df  
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

enxb8a3868ee9df Link encap:Ethernet  HWaddr b8:a3:86:8e:e9:df  
          inet addr:192.168.0.97  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::f81f:edde:16b6:a393/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:2022 errors:0 dropped:41 overruns:0 frame:0
          TX packets:1386 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1504042 (1.5 MB)  TX bytes:164531 (164.5 KB)

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:65536  Metric:1
          RX packets:77 errors:0 dropped:0 overruns:0 frame:0
          TX packets:77 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:6401 (6.4 KB)  TX bytes:6401 (6.4 KB)
```

It looks like the ethernet interface is initially named eth0 and then renamed to enxb827ebd8e6df (I presume based on its MAC address). The wifi chip is initially named wlan0 and then renamed to enxb8a3868ee9df. In the output from ifconfig above, how would one know that enxb8a3868ee9df is a wifi interface? Note at the time I did this I did not have the ethernet port connected so it hadn’t picked up an IP address.

So, I guess there are reasons for implementing PNIN but at least in the last example it could get pretty confusing. Is this really progress?

Doug

---

### Post by TheFu on 2016-07-21
[https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/](https://www.freedesktop.org/wiki/Software/systemd/PredictableNetworkInterfaceNames/)

> I don't like this, how do I disable this?

You basically have four options:
[LIST=1]
[*]    You disable the assignment of fixed names, so that the unpredictable kernel names are used again. For this, simply mask udev's rule file for the default policy: ln -s /dev/null /etc/udev/rules.d/80-net-setup-link.rules
[*]    You create your own manual naming scheme, for example by naming your interfaces "internet0", "dmz0" or "lan0". For that create your own .link files in /etc/systemd/network/, that choose an explicit name or a better naming scheme for one, some, or all of your interfaces. See systemd.link(5) for more information.
[*]    You pass the net.ifnames=0 on the kernel command line
[/LIST]



For some people, I can see where this would be better. It isn't *better* for me either.

---

