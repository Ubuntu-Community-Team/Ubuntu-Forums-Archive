---
title: "[SOLVED] Wired Connection, internet not working."
date: 2008-01-03
forum: Networking &amp; Wireless
---

### Post by Aaronought on 2008-01-03
Hi all,

I'm new to Linux and ubuntu. I only really installed it for a challenge and just to see how it was. I've installed it on a storage HDD in my desktop (made a separate partition) install went well. i get to the desktop i click on firefox and it says Server error or whatever (pretty much the page can not be displayed firefox version). I've had a play in network tools and the manual configuration in the white bar at the top and no luck.

now because im such noob i don't know what im going to need to tell you so you can help me so you ask and i will deliver.

my computer is connected to a wireless Linksys router (WRT54G) but im using a wire not wireless. (wireless is for the ps3 and psp)

hope you guys can help and sorry for my inexperience  

Aaron

---

### Post by Aaronought on 2008-01-03
ipconfig'ed on XP and is said this



Windows IP Configuration



        Host Name . . . . . . . . . . . . : inc-wak829x0qqx

        Primary Dns Suffix  . . . . . . . : 

        Node Type . . . . . . . . . . . . : Unknown

        IP Routing Enabled. . . . . . . . : No

        WINS Proxy Enabled. . . . . . . . : No



Ethernet adapter Local Area Connection:



        Connection-specific DNS Suffix  . : 

        Description . . . . . . . . . . . : Realtek RTL8139/810x Family Fast Ethernet NIC

        Physical Address. . . . . . . . . : 00-13-D4-61-5C-FB

        Dhcp Enabled. . . . . . . . . . . : Yes

        Autoconfiguration Enabled . . . . : Yes

        IP Address. . . . . . . . . . . . : 192.168.1.102

        Subnet Mask . . . . . . . . . . . : 255.255.255.0

        Default Gateway . . . . . . . . . : 192.168.1.1

        DHCP Server . . . . . . . . . . . : 192.168.1.1

        DNS Servers . . . . . . . . . . . : 62.31.64.39

                                            62.31.112.39

                                            62.31.144.39

        Lease Obtained. . . . . . . . . . : 04 January 2008 03:02:46

        Lease Expires . . . . . . . . . . : 05 January 2008 03:02:46


if that helps

---

### Post by Nrbelex on 2008-01-03
What's shown in the network manager icon in the top right when you unplug then re-plug the wire in?

~ Brett

---

### Post by Lostincyberspace on 2008-01-04
Run 
```
Ifconfig
```
and post the results.

---

### Post by Aaronought on 2008-01-04
here you go pal


caelestis@caelestis-desktop:~$ sudo ifconfig
[sudo] password for caelestis:
eth0      Link encap:Ethernet  HWaddr 00:13:D4:61:5C:FB  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:16 Base address:0xac00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:899 errors:0 dropped:0 overruns:0 frame:0
          TX packets:899 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:68860 (67.2 KB)  TX bytes:68860 (67.2 KB)

---

### Post by Lostincyberspace on 2008-01-04
try running sudo ifup and then rerunning ifconfig

---

### Post by Aaronought on 2008-01-05
right oh, i did that and this happened.

caelestis@caelestis-desktop:~$ sudo ifup
ifup: Use --help for help
caelestis@caelestis-desktop:~$ sudo ifconfig
eth0      Link encap:Ethernet  HWaddr 00:13:D4:61:5C:FB  
          inet6 addr: fe80::213:d4ff:fe61:5cfb/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:20 Base address:0xcc00 

eth0:avah Link encap:Ethernet  HWaddr 00:13:D4:61:5C:FB  
          inet addr:169.254.9.54  Bcast:169.254.255.255  Mask:255.255.0.0
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          Interrupt:20 Base address:0xcc00 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:64 errors:0 dropped:0 overruns:0 frame:0
          TX packets:64 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:5008 (4.8 KB)  TX bytes:5008 (4.8 KB)

caelestis@caelestis-desktop:~$ 

and still no internet =/

i had a look in connection information and it looks like this which is just totally wrong lol

[IMG]http://img441.imageshack.us/img441/7941/screenshotconnectioninfod2.png[/IMG]

---

### Post by ugm6hr on 2008-01-05
Seems like a problem with DHCP assigning an IP.  Certainly looks like DHCP is on (based on the Windows ipfonfig).  Best to check that is the case on the router's setup page.

In Network (System- menu), is "roaming mode" enabled for the wired ethernet?

Maybe just unplugging the ethernet cable and plugging back in after checking those will do the trick?

---

### Post by Aaronought on 2008-01-05
just had a look and DHCP is turned on in my router and theres other stuff that might help you guys help me so i took a screenie

[img]http://img170.imageshack.us/img170/6841/dhcpgg3.jpg[/img]

ill now try as u suggested

be back in a couple of mins mabe lol

nope =/ i unplugged and plugged it in again and still no internet.

something i did notice though on windows i look at the back of my computer there are 2 lights inside the network port a green and an orange when in ubuntu they dont light up

any more suggestions?

---

### Post by Aaronought on 2008-01-05
OPPS sorry =/ double

oh and yea, roaming mode is enabled ive also tried DHCP but that didnt work either

---

### Post by ugm6hr on 2008-01-05
One other possiblitity that I have thought of - but if this is the case you may be out of luck.

There are some cheap Chinese copied Realtek chipset ethernet cards (i.e. not true Realtek RTL8139), which unfortunately don't work in Linux.  In Ubuntu, post the output of these:
```
lspci
lshw -C network
```

If they mention something like: 
RTL8139D [Realtek] PCI 10/100BaseTX ethernet adaptor
Hangzhou Silan Microelectronics Co., Ltd.

Then I suspect that you have one of these cards, and you will be better off just getting a new ethernet card (people will often give them away, or otherwise they are under £5).

---

### Post by Aaronought on 2008-01-05
its an onboard ethernet port =/ lol so i may need to buy one haha.

ill post back with results

---

### Post by Aaronought on 2008-01-05
here we go

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 661FX/M661FX/M661MX Host (rev 11)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SiS AGP Port (virtual PCI-to-PCI bridge)
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:05.0 RAID bus controller: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]
01:00.1 Display controller: ATI Technologies Inc RV350 AP [Radeon 9600] (Secondary)

caelestis@caelestis-desktop:~$ sudo lshw -C network
[sudo] password for caelestis:
  *-network               
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: b
       bus info: pci@0000:00:0b.0
       logical name: eth0
       version: 10
       serial: 00:13:d4:61:5c:fb
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=64 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s

---

### Post by ugm6hr on 2008-01-05
OK - looks like the ethernet card is working, and has the right driver.

And with DHCP on, and working correctly on Windows, it's not that.  Although it might be worth restarting the router, just to check.

If not, one other thing  comes to mind...  Can you turn your ethernet card on and off from BIOS?  Does it have a software switch in Windows?

From: [http://support.microsoft.com/kb/910389](http://support.microsoft.com/kb/910389)
> If the network adapter supports a power management option, the following check box may be selected:
Allow the computer to turn off this device to save power
If the network adapter supports this option, it is available on the Power Management tab of the network adapter properties dialog box. To resolve this issue, disable this option on the Power Management tab. For more information about how to disable this power management option, click the following article number to view the article in the Microsoft Knowledge Base:

If you have this power-save function on in Windows, it will turn the network card off before shutting down, leaving it unavailable to Ubuntu.  So check that in Windows, and make sure you don't have power-save on.

Only other thing I can think of is a problem with Network Manager.  Maybe it's worth trying WIcd?  See the link in my signature.  Basically - download this and put on your desktop (or home folder): [http://downloads.sourceforge.net/wicd/wicd_1.3.8-all.deb?modtime=1196593368&big_mirror=0](http://downloads.sourceforge.net/wicd/wicd_1.3.8-all.deb?modtime=1196593368&big_mirror=0)

And then double-click to run it with GDebi.

It will probably insist on uninstalling Network Manager and ubuntu-desktop, but that should be OK.

---

### Post by Aaronought on 2008-01-05
power management was on, i didnt even know windows did that!

ill check back in a second.

---

### Post by Aaronought on 2008-01-05
AWSOME!! 

Thank you VERY much pal.

there was a setting in BIOS called "LAN boot ROM" or something that i enabled and not it works this post is from ubuntu xD

thanks to all the other people aswell.

---

### Post by ugm6hr on 2008-01-05
No worries.  That Windows power-saving function is really bizarre, since it would be unusual for you to *not* want the network connection to stay on if the computer is on.

Glad your online in Ubuntu :guitar:

---

### Post by mrraster on 2008-05-31
Thanks y'all.
This thread helped me solve my problem.
I have a Shuttle K43 barebones system that has a Realtek rtl-8139/8139C/8139C+ in it.
Ubuntu wasn't able to enable it for use.
I had to enable the "Boot from LAN chip" for it to work.
I never would have thought of that.
Thanks again.

MrRaster

---

