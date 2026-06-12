---
title: "replaced bad card, now network broken"
date: 2008-02-19
forum: Networking &amp; Wireless
---

### Post by dphirschler on 2008-02-19
We had some bad weather blow through GA this weekend, and one casualty was the NIC card in my Ubuntu box.  It's actually integrated into the mobo.  Anyways, after verifying the line still worked (by connecting my laptop to that same line), I installed a new NIC.  I also went into BIOS and disabled the bad NIC.  Anyways, now my network is broken.  I've tried unsuccessfully to troubleshoot it and now I appeal to the Ubuntu community.  Please help me get my network back up.

FWIW, I discovered the new card was being named eth1.  I believe I fixed that.  But still no network.  

Help!


Darryl

---

### Post by Whiffle on 2008-02-20
try opening 

/etc/interfaces

make sure eth1 is listed in there like eth0 is/was

---

### Post by dphirschler on 2008-02-20
Here is /etc/interfaces.  I had to modify this to remove the old NIC which was listed as eth0.  Then I renamed the new card from eth1 to eth0.

```
auto lo
iface lo inet loopback

auto eth1
#iface eth1 inet dhcp

auto eth2
#iface eth2 inet dhcp

auto ath0
#iface ath0 inet dhcp

auto wlan0
#iface wlan0 inet dhcp

iface eth0 inet static
address 192.168.1.98
netmask 255.255.255.0
gateway 192.168.1.1

auto eth0

```

---

### Post by dphirschler on 2008-02-20
I had hoped for some helpful suggestions by now.  I am eager to get this working but I do not even know where to look.  I don't mind researching it myself.  If somebody can at least tell me which configuration files hold the settings I need to look at or tweak.  Or possibly give me some commands that will give me some info I can look at.  Anything.  Even point me to a book I can read.  Please Ubuntu community, don't let me down!


Darryl

---

### Post by Iowan on 2008-02-20
Maybe not the most elegant way, but...
From a terminal: **sudo nano /etc/network/interfaces**
Edit **eth0** to **eth1**:
```
iface eth1 inet static
address 192.168.1.98
netmask 255.255.255.0
gateway 192.168.1.1
```
CTRL-O to write file, CTRL-X to exit
**/etc/init.d/networking restart**
check **ifconfig** to see if eth1 has an address

---

### Post by dphirschler on 2008-02-20
OK, not sure what that accomplished.  But I did it anyways.  Here is the output.

```
darryl@darryl-desktop:~$ sudo gedit /etc/network/interfaces
[sudo] password for darryl:
darryl@darryl-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth0=eth0.
eth1: ERROR while getting interface flags: No such device
SIOCSIFADDR: No such device
eth1: ERROR while getting interface flags: No such device
SIOCSIFNETMASK: No such device
eth1: ERROR while getting interface flags: No such device
Failed to bring up eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.
Ignoring unknown interface eth0=eth0.
                                                                         [ OK ]
darryl@darryl-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:DA:22:CF:17  
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:91 errors:0 dropped:0 overruns:0 frame:0
          TX packets:330 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:11483 (11.2 KB)  TX bytes:37131 (36.2 KB)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:97 errors:0 dropped:0 overruns:0 frame:0
          TX packets:97 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10535 (10.2 KB)  TX bytes:10535 (10.2 KB)
```

So what does that tell us?


Darryl

---

### Post by dphirschler on 2008-02-20
All right, I changed it back to eth0 and pinged myself and the router.  Here is the result:

```
darryl@darryl-desktop:~$ sudo gedit /etc/network/interfaces
darryl@darryl-desktop:~$ sudo /etc/init.d/networking restart
 * Reconfiguring network interfaces...                                          Ignoring unknown interface eth1=eth1.
Ignoring unknown interface eth2=eth2.
Ignoring unknown interface ath0=ath0.
Ignoring unknown interface wlan0=wlan0.
                                                                         [ OK ]
darryl@darryl-desktop:~$ ifconfig
eth0      Link encap:Ethernet  HWaddr 00:50:DA:22:CF:17  
          inet addr:192.168.1.98  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::250:daff:fe22:cf17/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:107 errors:0 dropped:0 overruns:0 frame:0
          TX packets:355 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:14221 (13.8 KB)  TX bytes:41724 (40.7 KB)
          Interrupt:19 Base address:0xa000 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:98 errors:0 dropped:0 overruns:0 frame:0
          TX packets:98 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:10623 (10.3 KB)  TX bytes:10623 (10.3 KB)

darryl@darryl-desktop:~$ ping 192.168.1.98
PING 192.168.1.98 (192.168.1.98) 56(84) bytes of data.
64 bytes from 192.168.1.98: icmp_seq=1 ttl=64 time=0.038 ms
64 bytes from 192.168.1.98: icmp_seq=2 ttl=64 time=0.030 ms
64 bytes from 192.168.1.98: icmp_seq=3 ttl=64 time=0.035 ms

--- 192.168.1.98 ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1999ms
rtt min/avg/max/mdev = 0.030/0.034/0.038/0.005 ms
darryl@darryl-desktop:~$ ping 192.168.1.99
PING 192.168.1.99 (192.168.1.99) 56(84) bytes of data.
From 192.168.1.98 icmp_seq=1 Destination Host Unreachable
From 192.168.1.98 icmp_seq=2 Destination Host Unreachable
From 192.168.1.98 icmp_seq=3 Destination Host Unreachable

--- 192.168.1.99 ping statistics ---
5 packets transmitted, 0 received, +3 errors, 100% packet loss, time 4018ms
, pipe 3
darryl@darryl-desktop:~$ ping 192.168.1.1
PING 192.168.1.1 (192.168.1.1) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=5 ttl=64 time=13.5 ms
64 bytes from 192.168.1.1: icmp_seq=8 ttl=64 time=0.838 ms
64 bytes from 192.168.1.1: icmp_seq=9 ttl=64 time=0.770 ms
64 bytes from 192.168.1.1: icmp_seq=10 ttl=64 time=0.779 ms

--- 192.168.1.1 ping statistics ---
22 packets transmitted, 4 received, 81% packet loss, time 21010ms
rtt min/avg/max/mdev = 0.770/3.992/13.584/5.538 ms
```

I think I see it getting through to the router, but it's extremely slow and unreliable (81% packet loss).  Am I right in assuming that something must be wrong with the network card?  Or could this still be a setting/driver issue?


Darryl

---

### Post by Iowan on 2008-02-21
It would seem that the card is now referenced as **eth0**. As far as the errors... obviously something is amiss - although I couldn't say if it's card or configuration.  HAving no intelligent recommendations, I'll ask if the new card is the same speed (or auto negotiating).

---

### Post by dphirschler on 2008-02-22
> **Iowan said:**
> It would seem that the card is now referenced as **eth0**. As far as the errors... obviously something is amiss - although I couldn't say if it's card or configuration.  HAving no intelligent recommendations, I'll ask if the new card is the same speed (or auto negotiating).

That's a question I don't know how to answer.  This much I know, it's a used 3Com PCI card that I have had for quite some time.  Here are the numbers from the card:

silk-screened on the board: 
3C905C-TX
Etherlink10/100PCI
1998 3Com Corporation

on the main chip:
3Com
920-BR03
3com 40-0579-003
1517 CT9921 P14
BROADCOM 5904

sticker on the back of the board:
HP P/N 5064-7429

etched into the back og the board:
94VO
3099

If there is no driver available for this card, then I will just replace it.  But if there is a chance I can get it working, I want to do that.  This is a learning exercise for me at this point and I don't want to give up.  So my question is... IS there a known good driver for this card?  How do I check which driver is installed currently?


Darryl

---

### Post by Iowan on 2008-02-22
The "Etherlink10/100PCI" probably answered my question.
**dmesg |grep eth ** and/or **lspci** *_might_* provide some info.

---

### Post by dphirschler on 2008-02-22
OK, thanks.  I will look at that tonight.


Darryl

---

### Post by dphirschler on 2008-02-25
OK here's what freaks me out.  I didn't have time to troubleshoot it this weekend.  And today I was on one of my Windows machines and I saw the Ubuntu share.  So I checked it out on the Ubuntu machine and it is working fine now.  I went ahead and downloaded updates while I could.  It just spontaneously fixed itself.  Now does anybody have a clue how that happened?


Darryl

---

### Post by dphirschler on 2008-02-26
... And it's down again this morning.  I suspect I have bigger problems than software setup.  I am definitely yanking out this NIC and trying a new one.  I might even have to swap the mobo.


Darryl

---

### Post by rustybronco on 2008-02-26
Please post the output of **lspci -nn**, lspci would have done it also 
[quote=Iowan]dmesg |grep eth  and/or **lspci** might provide some info.[/quote]

---

### Post by dphirschler on 2008-02-27
OK, here is the output from dmesg |grep eth and lspci -nn:

```
darryl@darryl-desktop:~$ dmesg |grep eth
[   26.108973] eth0:  setting full-duplex.
[   37.857895] eth0: no IPv6 routers present

darryl@darryl-desktop:~$ lspci -nn
00:00.0 Host bridge [0600]: nVidia Corporation nForce2 AGP (different version?) [10de:01e0] (rev c1)
00:00.1 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 1 [10de:01eb] (rev c1)
00:00.2 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 4 [10de:01ee] (rev c1)
00:00.3 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 3 [10de:01ed] (rev c1)
00:00.4 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 2 [10de:01ec] (rev c1)
00:00.5 RAM memory [0500]: nVidia Corporation nForce2 Memory Controller 5 [10de:01ef] (rev c1)
00:01.0 ISA bridge [0601]: nVidia Corporation nForce2 ISA Bridge [10de:0060] (rev a4)
00:01.1 SMBus [0c05]: nVidia Corporation nForce2 SMBus (MCP) [10de:0064] (rev a2)
00:02.0 USB Controller [0c03]: nVidia Corporation nForce2 USB Controller [10de:0067] (rev a4)
00:02.1 USB Controller [0c03]: nVidia Corporation nForce2 USB Controller [10de:0067] (rev a4)
00:02.2 USB Controller [0c03]: nVidia Corporation nForce2 USB Controller [10de:0068] (rev a4)
00:05.0 Multimedia audio controller [0401]: nVidia Corporation nForce Audio Processing Unit [10de:006b] (rev a2)
00:06.0 Multimedia audio controller [0401]: nVidia Corporation nForce2 AC97 Audio Controler (MCP) [10de:006a] (rev a1)
00:08.0 PCI bridge [0604]: nVidia Corporation nForce2 External PCI Bridge [10de:006c] (rev a3)
00:09.0 IDE interface [0101]: nVidia Corporation nForce2 IDE [10de:0065] (rev a2)
00:0d.0 FireWire (IEEE 1394) [0c00]: nVidia Corporation nForce2 FireWire (IEEE 1394) Controller [10de:006e] (rev a3)
00:1e.0 PCI bridge [0604]: nVidia Corporation nForce2 AGP [10de:01e8] (rev c1)
01:0a.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 6c)
01:0b.0 RAID bus controller [0104]: Promise Technology, Inc. PDC20376 (FastTrak 376) [105a:3376] (rev 02)
03:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV100 QY [Radeon 7000/VE] [1002:5159]
```

Any clues here?


Darryl

---

### Post by rustybronco on 2008-02-27
> **dphirschler said:**
> 
01:0a.0 Ethernet controller [0200]: 3Com Corporation 3c905C-TX/TX-M [Tornado] [10b7:9200] (rev 6c)

Any clues here?

Darrylfrom one of your posts > Ignoring unknown interface eth2=eth2.

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/118368](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/118368)
> 
 Loye Young wrote on 2007-06-04: (permalink)

I can confirm that this happened to me. Here's my work around:

1. Use the -a flag of ifconfig to get the report on all your ethernet devices.

# ifconfig -a

If you are like me, it will show the second card as eth2. Copy the MAC address of the second card to your clipboard.

2. Then, as root, edit /etc/iftab using your favorite text editor. (Mine is nano.)

# sudo nano /etc/iftab

You will see something like the following:

eth0 mac 00:00:00:00:00:00 arp 1

but the mac address of the card that's already working will be displayed instead of all zeros.

Add a line immediately under it:
eth1 mac [paste here the mac address you copied from step 1] arp 1

3. Save the file and exit. Reboot. (Trying "/etc/init.d/networking restart" won't work. You'll need a full-blown reboot.)

It's what worked for me.


[http://support.3com.com/infodeli/tools/nic/linux.htm](http://support.3com.com/infodeli/tools/nic/linux.htm)
go to...I agree>second page @ the bottom of the 2nd page

> Note: The 3C59x, 3C900 and 3C905 series NICs are supported by Donald Becker's driver. This driver can be obtained at the below URL: [http://www.scyld.com/network/vortex.html](http://www.scyld.com/network/vortex.html)  

But i think it was for 2.2- and 2.4.- kernels

Try the work-a-round first or...
Ethernet cards are cheep find another one...(putting on my flame suit)

---

### Post by dphirschler on 2008-02-27
Well, here is the latest news.  I yanked out the 3com card and placed it in a new Ubuntu system I had been setting up on the side.  It works perfectly.  I am on it currently.  So now I am thinking that either the 3com card was incompatible with my other computer, or more damage than I thought happened in the power outage.  Now I am looking at replacing the mobo.  :-(

Rustybronco, looks like I won't get a chance to try your fix, but I appreciate it all the same.  To the others, thanks for trying to help me with this frustrating problem.


Darryl

---

