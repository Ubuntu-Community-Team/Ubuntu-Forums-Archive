---
title: "Wired Connection"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by egkeat on 2010-10-30
I don't know. I'm starting to think this is just a bit too time consuming to keep using. I've upgraded to 9.10 and now have no internet connection...again.  This has happened several times.  I don't understand--one day it's there, the next it's not.  My router shows the internet on, but the Ubuntu software seems to be blocking it or something.

I have a netgear router on my desktop HP with a wireless modem broadband service. This works fine in Windows but if I go into Windows and use the internet here, when going back into Ubuntu, the network connection is gone.  Don't know what the problem is, but it's far too unreliable. Of course with no internet, I can't upgrade or do much of anything in Ubuntu.

---

### Post by egkeat on 2010-10-30
Can anyone help me? Still can't get the internet working in Ubuntu.
I have run the codes and get this in return:


br@ubuntu:~$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1e:8c:2b:06:8d  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)
          Interrupt:28 Base address:0xe000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:84 errors:0 dropped:0 overruns:0 frame:0
          TX packets:84 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9553 (9.5 KB)  TX bytes:9553 (9.5 KB)

vboxnet0  Link encap:Ethernet  HWaddr 0a:00:27:00:00:00  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 B)  TX bytes:0 (0.0 B)

br@ubuntu:~$ route -n
Kernel IP routing table
Destination     Gateway         Genmask         Flags Metric Ref    Use Iface
br@ubuntu:~$ ping -c3 4.2.2.1
connect: Network is unreachable
br@ubuntu:~$

---

### Post by cariboo on 2010-10-30
We need a lot more information,before we can help you with your connection problem. Could you post the output of the following commands in you next post.

```
sudo lshw -C network > network.txt
```

and 

```
ifconfig > ifconfig.txt
```

The above two commands when run will create text files that you can copy to your windows partition, one called network.txt and the other ifconfig.txt. They will go a long way in helping you solve your problem.

---

### Post by egkeat on 2010-10-30
Ok will do.  Have to go out for a while but will get to it when I get back.

---

### Post by egkeat on 2010-10-30
results for ifconfig:

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:82 errors:0 dropped:0 overruns:0 frame:0
          TX packets:82 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:9409 (9.4 KB)  TX bytes:9409 (9.4 KB)


network:

  *-network DISABLED
       description: Ethernet interface
       product: RTL8111/8168B PCI Express Gigabit Ethernet controller
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 02
       serial: 00:1e:8c:2b:06:8d
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress msix vpd bus_master cap_list rom ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=r8169 driverversion=2.3LK-NAPI duplex=full latency=0 link=yes multicast=yes port=MII speed=100MB/s
       resources: irq:28 ioport:e800(size=256) memory:febff000-febfffff memory:fdff0000-fdffffff(prefetchable) memory:febc0000-febdffff(prefetchable)
  *-network DISABLED
       description: Ethernet interface
       physical id: 1
       logical name: vboxnet0
       serial: 0a:00:27:00:00:00
       capabilities: ethernet physical
       configuration: broadcast=yes multicast=yes

---

### Post by Hippytaff on 2010-10-30
Looks like they're disabled, might be driver conflicts, but what happens when you type

```

sudo ifup eth0

```

and try it again replacing eth0 with eth1

---

### Post by egkeat on 2010-10-30
> **Hippytaff said:**
> Looks like they're disabled, might be driver conflicts, but what happens when you type

```

sudo ifup eth0

```

and try it again replacing eth0 with eth1


output eth0:
br@ubuntu:~$ sudo ifup eth0 
Ignoring unknown interface eth0=eth0.
br@ubuntu:~$ 

same thing eth1:
br@ubuntu:~$ sudo ifup eth1
Ignoring unknown interface eth1=eth1.
br@ubuntu:~$

---

### Post by Hippytaff on 2010-10-30
whats the driver called (or what chipset is it?)

```

lspci

```

lookup the driver. To be honest it should be pretty much plug and play with ethernet, but there might be an issue with your ethernet controller. Worth looking into.

Does it work ok with any other os?

---

### Post by sydbat on 2010-10-30
Might be a hardware issue. Perhaps your motherboard is starting to go? Happened to a client of mine.

---

### Post by egkeat on 2010-10-30
> **Hippytaff said:**
> whats the driver called (or what chipset is it?)

```

lspci

```

lookup the driver. To be honest it should be pretty much plug and play with ethernet, but there might be an issue with your ethernet controller. Worth looking into.

Does it work ok with any other os?

Works perfectly in Vista.

This is what I get with lspci

lspci
00:00.0 Host bridge: Intel Corporation 82G33/G31/P35/P31 Express DRAM Controller (rev 02)
00:02.0 VGA compatible controller: Intel Corporation 82G33/G31 Express Integrated Graphics Controller (rev 02)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 02)
00:1c.2 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 3 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 02)

---

### Post by egkeat on 2010-10-30
> **sydbat said:**
> Might be a hardware issue. Perhaps your motherboard is starting to go? Happened to a client of mine.

Don't think so.... Ethernet connection lost in Ubuntu. Works fine in Windows.

---

### Post by egkeat on 2010-10-30
I forgot to say I'm sharing a connection w/daughter's laptop. This didn't happen when she wasn't using it.

---

### Post by Hippytaff on 2010-10-30
I can't see your ethernet controller, if your using a router with two pc's then it can cause problems when one pc is turned off and on again. I have this problem (though we use wifi) ip addresses and mac addresses get all confused, I thought it was just my router being a bit rubbish though...usually have to reset the router

---

### Post by egkeat on 2010-10-30
> **Hippytaff said:**
> I can't see your ethernet controller, if your using a router with two pc's then it can cause problems when one pc is turned off and on again. I have this problem (though we use wifi) ip addresses and mac addresses get all confused, I thought it was just my router being a bit rubbish though...usually have to reset the router

Yes, using a router. So maybe this means I'll probably have to go first or won't have internet? Aw shucks. :(

---

### Post by egkeat on 2010-10-30
Well, looks like no matter what I do now, internet will not work with Ubuntu.  I'm back on in Windows now and working fine even though I've removed the router. Doing the same in Ubuntu does not work. It seems to be locked out somehow.

---

### Post by egkeat on 2010-10-31
For some strange reason my internet has started working again? I have been up all night trying to figure this thing out and finally got frustrated, clicked the network manager and suddenly...it worked. That makes no sense whatsoever. Is the connection timing out or something?

---

### Post by Hippytaff on 2010-10-31
No idea what was going on there. As long as it works though :-)

---

