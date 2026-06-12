---
title: "Sometimes have to reboot the computer several times before wired network works"
date: 2008-09-13
forum: Networking &amp; Wireless
---

### Post by delfick on 2008-09-13
hello,

I updated my computer a while ago so that I now have a [Giga-Byte GA-EP45-DS4P motherboard](http://www.gigabyte.com.tw/Products/Motherboard/Products_Spec.aspx?ClassValue=Motherboard&ProductID=2839&ProductName=GA-EP45-DS4P) (among other things like ram and intel Core 2 Duo E8200) which is really great and all, except now I have weird network problems.

incase it makes a difference, this motherboard has two network interfaces (one which I've ended up disabling in bios but it seemed to make little difference)

my problem is that when I boot up the computer it sometimes just won't connect, and I unfortunately don't know enough to try and work out how to make it work.

So I reboot the computer, sometimes all it takes is one reboot and it starts working again.

Sometimes, like this morning, it takes many boots (about 5 this morning)

This is starting to get irritating, so I'm wondering if anyone knows what I could do to try and figure out why it does this?

I'm using Ubuntu hardy 32bit.

Thankyou :)

---

### Post by Iowan on 2008-09-14
Start with basics and see if something is amiss. Post results of **lspci**, **ifconfig**, and contents of **/etc/network/interfaces**.

---

### Post by delfick on 2008-09-15
well, I've done those three commands both when it works and when it doesn't.

In both cases, /etc/network/interfaces and lspci give the same output

[quote="/etc/network/interfaces"]auto lo
iface lo inet loopback[/quote]

[quote="lspci"]00:00.0 Host bridge: Intel Corporation Eaglelake DRAM Controller (rev 02)
00:01.0 PCI bridge: Intel Corporation Eaglelake PCI Express Root Port (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #4
00:1a.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #5
00:1a.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #6
00:1a.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #2
00:1b.0 Audio device: Intel Corporation 82801JI (ICH10 Family) HD Audio Controller
00:1c.0 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 1
00:1c.5 PCI bridge: Intel Corporation 82801JI (ICH10 Family) PCI Express Port 6
00:1d.0 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #1
00:1d.1 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #2
00:1d.2 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB UHCI Controller #3
00:1d.7 USB Controller: Intel Corporation 82801JI (ICH10 Family) USB2 EHCI Controller #1
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 90)
00:1f.0 ISA bridge: Intel Corporation 82801JIR (ICH10R) LPC Interface Controller
00:1f.2 IDE interface: Intel Corporation 82801JI (ICH10 Family) 4 port SATA IDE Controller
00:1f.3 SMBus: Intel Corporation 82801JI (ICH10 Family) SMBus Controller
00:1f.5 IDE interface: Intel Corporation 82801JI (ICH10 Family) 2 port SATA IDE Controller
01:00.0 VGA compatible controller: nVidia Corporation NV43 [GeForce 6600 GT] (rev a2)
03:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)
04:06.0 FireWire (IEEE 1394): Texas Instruments TSB43AB23 IEEE-1394a-2000 Controller (PHY/Link)
04:07.0 IDE interface: Integrated Technology Express, Inc. Unknown device 8213[/quote]

and ifconfig gives different outputs

when working :
```
eth1      Link encap:Ethernet  HWaddr [..]
          inet addr:10.1.1.7  Bcast:10.1.1.255  Mask:255.255.255.0
          inet6 addr: fe80::21f:d0ff:fe20:f23a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:3417 errors:0 dropped:2849565219 overruns:0 frame:0
          TX packets:3605 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:1787056 (1.7 MB)  TX bytes:647709 (632.5 KB)
          Interrupt:220 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3326 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3326 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:166760 (162.8 KB)  TX bytes:166760 (162.8 KB)

```

when not working :
```
eth1      Link encap:Ethernet  HWaddr [..] 
          inet6 addr: fe80::21f:d0ff:fe20:f23a/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:4294967223 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:220 Base address:0x8000 

eth1:avahi Link encap:Ethernet  HWaddr [..]  
          inet addr:169.254.7.10  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:220 Base address:0x8000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:3013 errors:0 dropped:0 overruns:0 frame:0
          TX packets:3013 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:150980 (147.4 KB)  TX bytes:150980 (147.4 KB)

```

...

(I'm not certain on safety of posting HWaddr on a public forum, so I replaced them with [..]
forgive me if I'm wrong in thinking that be a bad thing to do :))

:)

---

### Post by Iowan on 2008-09-15
I'm not too confident today, but... try adding a section to **/etc/network/interfaces** file:
```
sudo nano /etc/network.interfaces
```
Add these lines:```
auto eth1
iface eth1 inet dhcp

```I assume (dangerous as it is to assume) that you get address via DHCP (when the system works).  The avahi address means something didn't work (right).
What provides address - router, modem, you...?

---

### Post by delfick on 2008-09-15
> **Iowan said:**
> I'm not too confident today, but... try adding a section to **/etc/network/interfaces** file:
```
sudo nano /etc/network.interfaces
```
Add these lines:```
auto eth1
iface eth1 inet dhcp

```I assume (dangerous as it is to assume) that you get address via DHCP (when the system works).  The avahi address means something didn't work (right).
What provides address - router, modem, you...?
 
I assume router is providing the address...

at the moment I have it set to "roaming mode"

I'll try again later when I get home, but when I try and set it to a static ip it never works.......

---

### Post by Iowan on 2008-09-15
> **delfick said:**
> I assume router is providing the address...

at the moment I have it set to "roaming mode"

I'll try again later when I get home, but when I try and set it to a static ip it never works....... If the previous suggestions don't work, try 
disabling "roaming mode".

---

### Post by delfick on 2008-09-16
when it isn't working dhcp and static ip doesn't work.

So I tried when it was working and dhcp did work
though setting to roaming mode after that didn't work

I also tried static ip when it was working in the first place which gave
SIOCADDRT: No such process
when I did "sudo /etc/init.d/networking restart"

....

---

