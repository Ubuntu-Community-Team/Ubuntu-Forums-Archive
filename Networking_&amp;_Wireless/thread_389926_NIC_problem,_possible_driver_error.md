---
title: "NIC problem, possible driver error?"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by PureW on 2007-03-21
Hello, I used to have my computer wired to a router, where I recieved my ip-adress from a dhcp.
Now I've moved and connect to the internet through a lan. I have recieved my network settings from my landlord, they look like this:
Computer Name: ****
IP-adress: 193.11.220.***
netmask: 255.255.254.0
Default Gateway: 193.11.220.1
Domain: olf.sgsnet.se
nameserver 1: 193.11.230.41
nameserver 2: 83.140.87.2

The connection works fine in windows on the same computer as well as on a laptop with the same ubuntu version. That is Ubuntu 6.10.

I've tried reinstalling, installing OpenSuse, Sabayon but nothing works, so now Im back to Ubuntu.

ifconfig:
```
eth0      Link encap:Ethernet  HWaddr 00:13:8F:81:80:30  
          inet addr:193.11.220.***  Bcast:193.11.221.255  Mask:255.255.254.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:82 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:20 errors:0 dropped:0 overruns:0 frame:0
          TX packets:20 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:1608 (1.5 KiB)  TX bytes:1608 (1.5 KiB)

```

/etc/network/interfaces
```

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
address 193.11.220.***
netmask 255.255.254.0
gateway 193.11.220.1

```

But it seems as the network driver is causing the error:
part of lspci -v:
```
00:11.0 Ethernet controller: ALi Corporation M5263 Ethernet Controller (rev 40)
        Subsystem: ASRock Incorporation Unknown device 5263
        Flags: bus master, medium devsel, latency 32, IRQ 82
        I/O ports at e400 [size=256]
        Memory at febfec00 (32-bit, non-prefetchable) [size=256]
        Capabilities: <access denied>

```
[lscpi](ssoeu.apakossa.org/lspci)
[dmesg](sso.apakossa.org/dmesg.out)

Basically the problem is that when I had dynamic ip, it worked and now that I have static, it doesn't work.

---

### Post by chili555 on 2007-03-21
What did you do with this information:> nameserver 1: 193.11.230.41
nameserver 2: 83.140.87.2

Can you ping -c3 216.239.51.104?

I don't think it's driver problem, because it shows up in ifconfig. I believe this uses the module uli526x. To check, please do lsmod | grep uli. If it pops back to the prompt with no output, it means the module is not loaded. If it outputs a bit of text including uli526x, it tells us the correct module is loaded.

Let us know.

---

### Post by PureW on 2007-03-21
I entered the dns information through the graphical configuration thingy: System->Administration->Networking 

Ping does not work.

lsmod | grep uli does indeed return "uli526x 22036 0"

---

### Post by PureW on 2007-03-21
I dont know if this is supposed to happen, but if I do a:
ifconfig
ping <somewhere>
ifconfig

I see that the loopback interface has transfered a few bytes, while there is no change in the eth0. Could this be related to the problem?

---

### Post by Mr. C. on 2007-03-21
Let's do things in order.  DNS is irrelevant for pinging an IP address.

TCP/IP doesn't care where the network information came from, just that its correct.

Let's start with some basics at the physical layer.  If your NIC has a link light, its it illuminated when the cable is plug in, and off when you take out the cable?  If its off all the time, you need a different cable, or a switch inbetween.

Let's check the physical connection:

```
sudo mii-tool -vv eth0
```

Let's run your ifconfig again. I want to see all the interfaces the system thinks you have:

```
sudo ifconfig -a
```

Your command lines shows your interfaces are up, but no packets have come or gone.  Ignore the loopback interface - the system is not getting confused and sending packets to the wrong interface.

MrC

---

### Post by PureW on 2007-03-21
The network card is integrated, I don't see a link light. But the same setup works in Windows.

sudo mii-tool -vv eth0
```

Using SIOCGMIIPHY=0x8947
SIOCGMIIPHY on 'eth0' failed: Operation not supported
```

Another inteface showed up:
sudo ifconfig -a
```
eth0      Link encap:Ethernet  HWaddr 00:13:8F:81:80:30  
          inet addr:193.11.220.209  Bcast:193.11.220.255  Mask:255.255.254.0
          UP BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:82 Base address:0xe400 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:32 errors:0 dropped:0 overruns:0 frame:0
          TX packets:32 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:2799 (2.7 KiB)  TX bytes:2799 (2.7 KiB)

sit0      Link encap:IPv6-in-IPv4  
          NOARP  MTU:1480  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

---

### Post by Mr. C. on 2007-03-21
Sorry, I see the problem.  The card is not known.

Please provide the output of 

lspci -n

and I will lookup the driver you require.

MrC

---

### Post by PureW on 2007-03-21
lspci -n
```
00:00.0 0600: 10b9:1695
00:01.0 0604: 10b9:524b
00:02.0 0604: 10b9:524c
00:03.0 0604: 10b9:524d
00:04.0 0600: 10b9:1689
00:05.0 0604: 10b9:5246
00:06.0 0604: 10b9:5249
00:07.0 0601: 10b9:1563 (rev 70)
00:07.1 0680: 10b9:7101
00:08.0 0401: 10b9:5455 (rev 20)
00:11.0 0200: 10b9:5263 (rev 40)
00:12.0 0101: 10b9:5229 (rev c7)
00:13.0 0c03: 10b9:5237 (rev 03)
00:13.1 0c03: 10b9:5237 (rev 03)
00:13.2 0c03: 10b9:5237 (rev 03)
00:13.3 0c03: 10b9:5239 (rev 01)
00:18.0 0600: 1022:1100
00:18.1 0600: 1022:1101
00:18.2 0600: 1022:1102
00:18.3 0600: 1022:1103
03:00.0 0106: 197b:2360
04:00.0 0300: 10de:0042 (rev a1)

```

---

### Post by Mr. C. on 2007-03-21
Ok, bad news.

Your device is not currently known in the PCI device registry, and I can find no drivers in any of the linux kernels at [www.kernel.org](www.kernel.org)

The Ali Corporation site has no useful information or product support of any kind that I can find.

Until a driver is available to work with this card (PCI Vendor ID 10b9, Device ID: 5263), you will have to find another card to use with native Ethernet in Linux.

Otherwise, you can try the ndiswrapper to use the windows ndis drivers.

Sorry,
MrC

---

### Post by PureW on 2007-03-21
I really appreciate your help. I googled myself and found this:
```
Linux_K2.6.x_Integrated132

    Version: 1.32

    Function: AUDIO, IDE, LAN, SATA

    Chip: M1567, M1573, M1575, M1689

    OS: LINUX Kernel 2.6.x
    Download

    File Size: 2.57MB
http://download.nvidia.com/ULi/ULi_Linux_K2.6.x_Integrated132.zip

```
I found it here: [http://www.nvidia.com/page/uli_drivers.html](http://www.nvidia.com/page/uli_drivers.html)
Do you think it's worth a try?


> **Mr. C. said:**
> ...
Otherwise, you can try the ndiswrapper to use the windows ndis drivers.



I have no idea what that is or how to do it.

---

### Post by PureW on 2007-03-21
> **Mr. C. said:**
> ...
Otherwise, you can try the ndiswrapper to use the windows ndis drivers.



I have no idea what that is or how to do it.

---

### Post by Mr. C. on 2007-03-21
Yes, indeed, this matches your card.  Nice work!  

#define PCI_ULI5263_ID  0x526310B9      /* ULi M5263 ID*/

Vendor 10B9, Chip 5263

Build that driver!

MrC

---

### Post by PureW on 2007-03-22
Trouble is, I tried building but I don't think I have gcc since I can't compile (getting alot of errors).
So I tried downloading gcc and tranfering by an usb-stick but I couldn't compile the gcc source either so I have no clue now.

---

### Post by Mr. C. on 2007-03-22
> **PureW said:**
> Trouble is, I tried building but I don't think I have gcc since I can't compile (getting alot of errors).
So I tried downloading gcc and tranfering by an usb-stick but I couldn't compile the gcc source either so I have no clue now.
You don't want to build gcc yourself - that's a task.  Get the tools you need:

```
apt-get install build-essential 
apt-get install linux-headers-generic
```

This will get you what you need.

MrC

---

### Post by PureW on 2007-03-22
> **Mr. C. said:**
> You don't want to build gcc yourself - that's a task.  Get the tools you need:

```
apt-get install build-essential 
apt-get install linux-headers-generic
```

This will get you what you need.

MrC

I would love to use apt-get if it was possible but I connect to internet through this network card that doesnt work.
I do have a laptop with internet and an usb-stick. Perhaps someone could compile the driver and send it to me?

---

### Post by chili555 on 2007-03-22
It's not that easy, the driver needs to be compiled against your running kernel.

But, it's also not that hard. Here is the site where you can download the packages to the aforementioned USB drive: [http://packages.ubuntu.com/](http://packages.ubuntu.com/) Search within your version, edgy, dapper, etc. and notice the dependencies (red dot). If your install doesn't have the requirements, download them, too.

Some of these may be on your installation CD. Issue a command: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.bak
sudo apt-cdrom add
sudo apt-get update
```Then see if you can get build-essentials and linux-headers.

I believe that's what my esteemed colleague Mr.C. meant.

---

### Post by PureW on 2007-03-22
Oke, now I have gcc but after following the instructions in the drivers readme, I try the 
"make menuconfig". And I get this output:
```

sudo make menuconfig
  HOSTCC  scripts/basic/fixdep
  HOSTCC  scripts/basic/split-include
  HOSTCC  scripts/basic/docproc
  HOSTCC  scripts/kconfig/conf.o
  HOSTCC  scripts/kconfig/kxgettext.o
  HOSTCC  scripts/kconfig/mconf.o
  HOSTCC  scripts/kconfig/zconf.tab.o
  HOSTLD  scripts/kconfig/mconf
  HOSTCC  scripts/kconfig/lxdialog/checklist.o
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:31:20: error: curses.h: No such file or directory
In file included from scripts/kconfig/lxdialog/checklist.c:24:
scripts/kconfig/lxdialog/dialog.h:128: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;use_colors&#8217;
scripts/kconfig/lxdialog/dialog.h:129: error: expected &#8216;=&#8217;, &#8216;,&#8217;, &#8216;;&#8217;, &#8216;asm&#8217; or &#8216;__attribute__&#8217; before &#8216;use_shadow&#8217;

```

And alot of errors follows that. What do I do?

---

### Post by Mr. C. on 2007-03-22
If you are going to use menuconfig, you need libcurses5-dev.

Otherwise, use make config.

MrC

---

### Post by PureW on 2007-03-23
Oke, make config works. But how do I know what to answer all those questions?

---

### Post by Mr. C. on 2007-03-23
Many people that build their own kernel take one of two forms:

- either they use the configurations supplied by the distro, thereby rebuilding the same kernel supplied, and simply replace one component, or 

- they build their own custom kernel and make the journey towards understanding the multitudes of options available.  This takes time and perseverance.

I've been building my own for ages.  I have not re-built a Debian packaged kernel, so cannot guide you further down this part of the path.  If I get some time today, I'll attempt to do so, but hopefully someone who knows this area better than I will answer your question(s) before then.

MrC

---

### Post by PureW on 2007-03-24
If I just press enter, instead of saying yes or no when I get a question, will the config use the distro's configuration?

---

