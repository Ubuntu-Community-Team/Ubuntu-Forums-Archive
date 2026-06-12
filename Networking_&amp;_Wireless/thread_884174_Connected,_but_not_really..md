---
title: "Connected, but not really."
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by DaltonAdair on 2008-08-08
Hay guise, Dalton here again.

Okay, so I got Ubuntu 8.04.1 64 bit running on my shiny new D945GCLF board. Hardware stats:

Intel Atom @ 1.6GHZ w/HT
1GB ptiTurbo @ 533MHz (3-4-4-15) ((I think? Might be 3-4-4-12)
Intel 945 Chipset (Desktop)
80GB WesternDigital SATA2 
Creative 24x CD-RW 

Here is my problem:

Network shows up as connected, but really isn't. Can't access my network resources (read as test share on my laptop) or the internet. Huh?

But it says I am connected.

This is via a Belkin router (model number will be edited in when I get home.)

Any ideas? Am I missing something?

---

### Post by pytheas22 on 2008-08-08
Sounds like either you don't really have an IP address, or there's an issue with DNS.  Please post the output of the following:
```

cat /etc/resolv.conf
ifconfig
lshw -C Network
host google.com
ping -c 3 google.com
ping -c 3 72.14.207.99

```

That will help get to the bottom of it.

---

### Post by DaltonAdair on 2008-08-08
cat /etc/resolv.conf puts out:
```
 cat: /etc/resolv.conf: No such file or directory
```

ifconfig puts out:
```
lo     Link encap: Local loopback
             inet addr:127.0.0.1 Mask: 255.0.0.0
             inet6 addr: ::1/128 Scope:Host
             UP LOOPBACK RUNNING  MTU:16436  Metric:1
             RX packets:1541 errors:0 dropped:0 overruns:0 frame:0
             TX packets:1541 errors:0 dropped:0 overruns:0 carrier:0
             collisions:0 txqueueln:0
             RX bytes:86680 (84.6 KB) TX bytes:86680 (84.6 KB)

```

host google.com puts out:
```
 ;; connection timed out; no servers could be reached
```

ping -c 3 google.com puts out:
```
Ping: unknown host google.com
```

ping -c 3 72.14.207.99 puts out:
```
connect: Network is unreachable
```

Looks like I am dead in the water. 127.0.0.1 means I haven't been assigned an IP address by my router, I know that much. That missing conf file is worrying me to. What next?

---

### Post by pytheas22 on 2008-08-08
You have no networking interfaces ('lo' is not a real interface; it's just for localhost stuff), so that's clearly the problem--I'm not sure why the network shows up as connected (what exactly was telling you that?), but it's apparently wrong, as "ifconfig" mentions no interfaces present.

Were you trying to connect via ethernet or wireless?  Either way, please post the output of:
```

ifconfig -a
lspci -nn
lsusb
lshw -C Network
```

so that we can figure out which drivers you need to install in order for the networking to work.

---

### Post by DaltonAdair on 2008-08-08
Trying to connect via Ethernet.

ifconfig -a puts out:
```

eth0   Link encap:Ethernet  HWaddr ff:ff:ff:ff:ff:ff
       BROADCAST MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 B) TX bytes: 0 (0.0 B)
       Interrupt: 252 Base address: 0xa000

lo     Link encap: Local Loopback
         (all the local loopback crap we ahve seen before)

```

lspci -nn puts out (bear with me, this is long):
```
00:00.0 Host bridge [0600]: Intel Corporation 82945G/GZ/P/PL Memory Controller Hub [8086:2770] (rev 02)
00:02.0 VGA compatible controller [0300]: Intel Corporation 82945G/GZ Integrated Graphics Controller [8086:2772] (rev 02)
00:1b.0 Audio device [0403]: Intel Corporation 82801G (ICH7 Family) High Definition Audio Controller [8086:27d8] (rev 01)
00:1c.0 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 1 [8086:27d0] (rev 01)
00:1c.2 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 3 [8086:27d4] (rev 01)
00:1c.3 PCI bridge [0604]: Intel Corporation 82801G (ICH7 Family) PCI Express Port 4 [8086:27d6] (rev 01)
00:1d.0 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #1 [8086:27c8] (rev 01)
00:1d.1 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #2 [8086:27c9] (rev 01)
00:1d.3 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB UHCI Controller #4 [8086:27cb] (rev 01)
00:1d.7 USB Controller [0c03]: Intel Corporation 82801G (ICH7 Family) USB2 EHCI Controller [8086:27cc] (rev 01)
00:1e.0 PCI bridge [0604]: Intel Corporation 82801 PCI Bridge [8086:244e] (rev e1)
00:1f.0 ISA bridge [0601]: Intel Corporation 82801GB/GR (ICH7 Family) LPC Interface Bridge [8086:27b8] (rev 01)
00:1f.1 IDE interface [0101]: Intel Corporation 82801G (ICH7 Family) IDE Controller [8086:27df] (rev 01)
00:1f.2 IDE interface [0101]: Intel Corporation 82801GB/GR/GH (ICH7 Family) SATA IDE Controller [8086:27c0] (rev 01)
00:1f.3 SMBus [0c05]: Intel Corporation 82801G (ICH7 Family) SMBus Controller [8086:27da] (rev 01)
01:00.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL8101E PCI Express Fast Ethernet controller [10ec:8136] (rev 02)

```
lsusb puts out: 
```
Bus 004 Device 001: ID 0000:0000
Bus 003 Device 001: ID 0000:0000
Bus 002 Device 001: ID 0000:0000
Bus 001 Device 001: ID 0000:0000

```

lshw -C Network warns, "You should run as super-user" then puts out:
```

*-network DISABLED
   Description: Ethernet interface
   product: RTL8101E PCI Express Fast Ethernet controller
   vendor: Realtek Semiconductor Co., Ltd.
   physcial id: 0
   logical name: eth0
   bus info: pci@0000:01:00.0
   version: 02
   serial: ff:ff:ff:ff:ff:ff
   width: 64 bits
   clock: 33MHz
   capabilities: bus_master cap_list ethernet physical
   configuration: broadcast=yes driver=r8169 driverversion=2.2LK latency=0
module=r8169 multicast=yes
   resources: iomemory:ffffffff0-fffffffef iomemory:ffffffff0-fffffffef

```

---

### Post by DaltonAdair on 2008-08-09
*bamp*

---

### Post by pytheas22 on 2008-08-09
hmmm, for some reason the system thinks that your ethernet card is disabled.  Make sure it's not turned off via BIOS or a switch on your computer (not likely, but I just want to check).

If you're sure the ethernet should be on, try these commands and please post their output:
```

sudo ifconfig eth0 up
ifconfig eth0
sudo dhclient eth0
```

If that works, you should get an IP address and be able to get online.  If not, try this next:
```

sudo rmmod r8169
sudo modprobe r8169
sudo ifconfig eth0 up
sudo dhclient eth0
```

If none of the above is useful, are you on a dual-boot system running Windows?  If so, you may be affected by the issue outlined [here]("http://ubuntuforums.org/showthread.php?t=538448")--basically Windows powers down the ethernet card in a way that makes it not work on Ubuntu, but you can workaround that problem.  Please take a look at that thread and try applying the fixes.

Let me know how it goes.

---

### Post by DaltonAdair on 2008-08-09
Again, thanks for your help.

sudo ifconfig eth0 up puts out:
```
 SIOCSIFFLAGS: Invalid argument
```

ifconfig eth0 puts out:
```

eth0   Link encap:Ethernet HWaddr ff:ff:ff:ff:ff:ff
       BROADCAST MULTICAST MTU:1500 Metric:1
       RX packets:0 errors:0 dropped:0 overruns:0 frame:0
       TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
       collisions:0 txqueuelen:1000
       RX bytes:0 (0.0 B) TX bytes:0 (0.0 B)
       Interrupt:252 Base address:0xa000

```

sudo dhclient eth0 puts out:
```

SCIOCSIFFLAGS: Invalid argument
SCIOCSIFFLAGS: Invalid argument
Listening on LPF/eth0/ff:ff:ff:ff:ff:ff
Sending on  LPF/eth0/ff:ff:ff:ff:ff:ff
Sending on   Socket/fallback
receive_packet failed on eth0: Network is down
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Network is down

```

sudo rmmod r8169 executes.

sudo modprobe r8169 executes.

sudo ifconfig eth0 up puts out:
```
 SIOCSIFFLAGS: Invalid argument 
```

At this point I think we both know that dhclient is going to give the same results. 

This is a clean system, freshly installed Ubuntu 8.0.4.1 amd64.

I also tried the little trick outlined in the post you link too, no effect it seems.

---

### Post by pytheas22 on 2008-08-09
Yeah, it sounds like a major problem with detection of the ethernet card.  Are you running Windows on the same machine and if so did you look at that thread that I linked to above?

Finally, do you have any luck with:
```

sudo ifconfig eth0 hw ether 01:23:45:67:89:01
```

That would reset your MAC address to something more valid (right now it's given as ff:ff:ff:ff:ff:ff, which is weird); maybe it will help.

---

### Post by DaltonAdair on 2008-08-09
I dont have Windows on this machine. I did have windows at one point though... 

I tried to cut the power for about 60 seconds, no effect. 

sudo ifconfig eth0 hw ether 01:23:45:67:89:01 puts out:
```
SIOCSIFHWADDR: cannot assign requested address
```

Balls. :(

---

### Post by pytheas22 on 2008-08-09
Yeah, it doesn't look really good.  Could you try restarting your computer several times and seeing if the card works after any of the restarts?  [This thread]("http://ubuntuforums.org/showthread.php?t=413984") (dealing with the same card and seemingly the same problem) suggests that the card arbitrarily works after certain restarts.

---

### Post by DaltonAdair on 2008-08-09
Sure, I will let you know.

---

### Post by DaltonAdair on 2008-08-09
I figured it out!

Resetting the computer repeatedly didn't work, but it got me thinking, since the LAN device has been put into some sort of zombiefied state why not reset the LAN device instead of the whole computer?

So here is what I did.

I went into BIOS and disabled it, then cycled the power, re-enabled it, cycled the power again, and now it works!

Thanks for your help though, I really appreciate it. 
Spread the word on this find though!

---

### Post by DaltonAdair on 2008-08-09
Nevermind, that solution was only a one-off and it doesn't work every time.

I am just going to buy a different NIC so I don't have to keep wrestling with his stupid piece. 

Anyone have a suggestions as to a solid NIC that is PCI and is compatible with 8.04.1 amd64?

---

### Post by rtrdom on 2008-08-09
I don't know if it will help but: if you have a router/access point you're
using between your computer and the internet modem, ensure there are no
**other** devices (routers, access points, boosters, telephones, etc.,) that
are using the same frequency as your router. The problem manifested itself
for me recently and the solution was to turnoff the second (booster it was)
device. Try setting the operating frequency of your router/access device to
the channel farthest from whatever is interfering. I chased this problem
for over three weeks and since turning off the Linksys booster, ALL computers with wireless can connect to the internet. All previously showed
connection to the network but could not get to the internet.
Hope this helps.

---

### Post by pytheas22 on 2008-08-10
> Nevermind, that solution was only a one-off and it doesn't work every time.

I am just going to buy a different NIC so I don't have to keep wrestling with his stupid piece.

Anyone have a suggestions as to a solid NIC that is PCI and is compatible with 8.04.1 amd64?

With a handful of exceptions, pretty much every kind of ethernet card should "just work" on Ubuntu--you are very unlikely with yours.  The best way to make sure it will work is to find the name of the chipset and google it + ubuntu; if there are problems, they should be obvious.  It may be difficult to figure out which chipset a card uses, though, without putting it in a computer (it usually doesn't say on the box).  Maybe your best bet is to buy something that you can return easily on the off chance that it doesn't work.

---

### Post by Xeon3D on 2008-08-31
Just update to a newer kernel, the driver is bugged on the default ones. Try using the latest available and report back to us :)

---

### Post by fortran01 on 2008-10-24
Appears to be a bug in Linux kernel:
[http://www.gossamer-threads.com/lists/linux/kernel/982159](http://www.gossamer-threads.com/lists/linux/kernel/982159)

---

### Post by fortran01 on 2008-10-26
This is the fix:
[http://linuxtrek1.blogspot.com/2008/10/ubuntu-on-intel-d945gclf-with-intel.html](http://linuxtrek1.blogspot.com/2008/10/ubuntu-on-intel-d945gclf-with-intel.html)

Patched the most recent kernel.

---

