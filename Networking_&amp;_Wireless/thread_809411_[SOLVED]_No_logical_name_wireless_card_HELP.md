---
title: "[SOLVED] No logical name wireless card? HELP"
date: 2008-05-27
forum: Networking &amp; Wireless
---

### Post by yogo on 2008-05-27
I can not find a logical name for my wireless card.

When the connecting computer was using Ubuntu, it was ra0. However I get no device found if I try sudo dhclient ra0.

The wireless is using XP, I am using Gutsy.
steve@steve-desktop:~$ sudo lshw -C network
  *-network               
       description: Ethernet interface
       product: BCM4401 100Base-T
       vendor: Broadcom Corporation
       physical id: 9
       bus info: pci@0000:01:09.0
       logical name: eth0
       version: 01
       serial: 00:0d:56:55:3a:9b
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
      capabilities: pm bus_master cap_list ethernet physical mii 10bt 10bt-fd 100bt       100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=b44 driverversion=1.01 duplex=full ip=192.168.11.2 latency=64 link=yes module=b44 multicast=yes port=twisted pair speed=100MB/s


It connects fine but I want to be able to bring the wireless down with sudo ifdown <interface>

But I can not for the life of me find the name of the <interface>

and I am pulling my hair out!

TIA

---

### Post by pytheas22 on 2008-05-27
It doesn't look like lshw is seeing a wireless card--the listing above appears to only be for ethernet.  Are you sure your wireless card is being detected (and are you using it now)?

If the card is detected, iwconfig should tell you the name assigned to it even if the interface is down.

If it's not being detected, use lspci (or lsusb if it's a USB device) to figure out what kind of card you have and try to learn what you need to do to get it working.  If you can't figure it out, post the output of lspci here and maybe someone can point you in the right direction.

---

### Post by yogo on 2008-05-27
pytheas22,

The wireless card is connected and works just fine. It is an Edimax 712 and has worked flawlessly in both Feisty and Windows.

My router sees the wireless LOL Obviously otherwise it would not connect. But absolutely nothing in my Gutsy install sees it?

I even added WICD today and it does not see a wireless connection but it is connected.


I have gone through all the CLI commands I can find and I am not sure what I need to do to get rid of the (no wireless extensions)  

I guess this is a reverse problem, as the card connects, I just want the ability to bring it up and down from my pc. (router)

Thanks

---

### Post by pytheas22 on 2008-05-27
That seems strange.  Please post the output of:

```
iwconfig
ifconfig -a
```

This should tell you the name.

---

### Post by yogo on 2008-05-27
Theoretically it should, as well as a ton of other commands but here is my output.

steve@steve-desktop:~$ iwconfig -a
-a        No such device

steve@steve-desktop:~$ iwconfig 
lo        no wireless extensions.

eth0      no wireless extensions.

steve@steve-desktop:~$ 

I could go through posting screen captures, but not really worth the trouble.

My router firmware sees in the bedroom wireless connection, but down here in my office, WICD does not see any wireless connections?

Hurry please, before all my hair is gone!:)

---

### Post by pytheas22 on 2008-05-27
Wow, that's really crazy.  Short of magic, how can you have a working wireless connection that the system doesn't see?  Are you absolutely sure you're not connected to the Internet in some other way?

I can't think of many other places to look...do you know which module drives your wireless card?  From that you could figure out what the name of the interface should be.  If you don't know the module, you should be able to figure it out with some Google searches.

---

### Post by yogo on 2008-05-27
When Feisty was on the wireless, it was seen as ra0, my drivers are rt61, yeah it is crazy but I am connected by my Buffalo router and am using aes with a wpa-psk so there is no doubt that I am  connected to my router, when I reset my router the wireless drops it's connection. Also by the tray icon, I can switch modes between router and AP. when switched on the wireless card, the connection drops, when switching back, the connection is back.

So there is no doubt whatsoever that the bedroom is picking up my router, it identifies essid etc.

So what we have is a case of Windows seeing my router, Feisty saw my router, however my system (Gutsy) does not see that I have a wireless device connected.


This has got me stumped, I have followed a many good tutorial about wireless network commands, including one written by a member here (kevdog) so all in all, nothing is wrong with the commands but the system is seeing nothing.

Confused.

---

### Post by pytheas22 on 2008-05-27
Wait, so on your current Ubuntu system, wireless does not work?  That makes more sense...I thought you meant that the wireless connection was working somehow but the system was not showing it.

The ralink drivers (which include rt61) have been changing a lot recently; I'd bet that that's the reason it stopped working in a more recent distribution.  You'd probably have better luck if you blacklisted the rt61pci module (the one that ships with Ubuntu now) and used the legacy rt61 driver from [http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads](http://rt2x00.serialmonkey.com/wiki/index.php?title=Downloads) instead.  My ralink card (rt73) doesn't work with the new drivers either, only legacy.

It's pretty easy to install the legacy driver if you have some experience with Linux, but if you need help, feel free to ask.

By the way, what is the output of lspci?

---

### Post by yogo on 2008-05-27
pytheas22, Thanks for your help/interest.

steve@steve-desktop:~$ lspci
00:00.0 Host bridge: Intel Corporation 82845G/GL[Brookdale-G]/GE/PE DRAM Controller/Host-Hub Interface (rev 01)
00:02.0 VGA compatible controller: Intel Corporation 82845G/GL[Brookdale-G]/GE Chipset Integrated Graphics Device (rev 01)
00:1d.0 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #1 (rev 01)
00:1d.1 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #2 (rev 01)
00:1d.2 USB Controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) USB UHCI Controller #3 (rev 01)
00:1d.7 USB Controller: Intel Corporation 82801DB/DBM (ICH4/ICH4-M) USB2 EHCI Controller (rev 01)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev 81)
00:1f.0 ISA bridge: Intel Corporation 82801DB/DBL (ICH4/ICH4-L) LPC Interface Bridge (rev 01)
00:1f.1 IDE interface: Intel Corporation 82801DB (ICH4) IDE Controller (rev 01)
00:1f.3 SMBus: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) SMBus Controller (rev 01)
00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 01)
01:05.0 Communication controller: Conexant Unknown device 2702 (rev 01)
01:06.0 FireWire (IEEE 1394): Agere Systems FW323 (rev 61)
01:09.0 Ethernet controller: Broadcom Corporation BCM4401 100Base-T (rev 01)
steve@steve-desktop:~$ 


Actually, this is correct IE ( I  thought you meant that the wireless connection was working somehow but the system was not showing it.)


At one time we had Feisty on both the bedroom and my office pc. I have upgraded to Gutsy and have HH on a stick, I do however want to play around with HH before I decide to install it.

To make a long story short, my wife had troubles with her Feisty and something was haywire and I was always having to get it going, anyways I just decided it was easier to put her back on Windows than listen to her complaining.

So when she had Feisty, I would sudo dhclient ra0 up to bring up her Interface/Internet.
I did use the serial monkey to get hers going originally in Feisty. So I do have legacy and possibly new stuff if Gutsy installed it with upgrading. 

Since she is back on Windows, all I had to do is slap in the cd with drivers and install. Took about two seconds and it works well, HOWEVER my system does not see her wireless, BUT in a browser window, my router sees her wireless connection.

Hope all this makes sense.

---

### Post by yogo on 2008-05-27
Interesting enough, output from dmesg renders this

  69.532860] eth0: no IPv6 routers present
as well as this 
[ 8231.850041] ADDRCONF(NETDEV_UP): eth0: link is not ready
[ 8234.841484] b44: eth0: Link is up at 100 Mbps, full duplex.
[ 8234.841489] b44: eth0: Flow control is off for TX and off for RX.
[ 8234.844199] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready


Now it has been over a year but I swear I had blacklisted b44 and I have a Buffalo WHR-HP-54G and I am thinking of adding Tomato but the router works well and never drops unless I want it to.

---

### Post by pytheas22 on 2008-05-27
It's making a more sense but I'm still a little confused.  Is this right:

Your wife's computer, in the bedroom, runs Windows and has a working wireless connection.  You have a working wireless connection on Ubuntu.  Your wireless router detects your wife's machine, but your computer is not able to see hers via network sharing.  Every computer running Ubuntu detects its own wireless devices without a problem; it's seeing other computers on the network that is the issue.

If this is the case, then the problem would be samba I guess (if that's what you're using for network sharing).  But if I'm still misunderstanding the situation, please let me know.

---

### Post by yogo on 2008-05-27
> **pytheas22 said:**
> It's making a more sense but I'm still a little confused.  Is this right:

Your wife's computer, in the bedroom, runs Windows and has a working wireless connection.  You have a working wireless connection on Ubuntu.  Your wireless router detects your wife's machine, but your computer is not able to see hers via network sharing.  Every computer running Ubuntu detects its own wireless devices without a problem; it's seeing other computers on the network that is the issue.

If this is the case, then the problem would be samba I guess (if that's what you're using for network sharing).  But if I'm still misunderstanding the situation, please let me know.


You got it pretty much right, I have never used samba and am not familiar with it.
What can I add to make it possible to see her wireless card from my PC? IE  it's seeing other computers on the network that is the issue.

---

### Post by pytheas22 on 2008-05-28
Alright, I'm glad I understand now and sorry for all the confusion.  Do you mean that you are trying to open a folder in Nautilus and browse to your wife's PC over the local network?  You won't be able to see other Windows PCs on your local network unless you have samba installed.  You can have it automatically installed and configured by selecting System>Preferences>Shared Folders (I think; I'm not on an Ubuntu machine now so the name may be slightly different).

You could also try pinging your wife's computer.  As long as ping requests are not being dropped by Windows or a firewall, you should be able to do something like:

```
ping 192.168.0.5
```

and get a response.  This would tell you that your machine is at least capable of "seeing" your wife's PC; from there it's just a matter of setting up samba properly.

Another thing to try would be to install an ssh server on your Ubuntu machine and see if you can access it over the local network from Windows via putty.  This would also  confirm that the machines see each other.

There are other things to check for as well, like making sure that your router is not dropping traffic between your machine and your wife's for some reason.

---

### Post by yogo on 2008-05-28
> **pytheas22 said:**
> 

```
ping 192.168.0.5
```and get a response.  This would tell you that your machine is at least capable of "seeing" your wife's PC; from there it's just a matter of setting up samba properly.




I can ping her pc and get responses and I know they are seeing each other. However I can not see her interface name? I guess it would be the same as ra0 when she was on Feisty but when I try that from terminal, I get no device found, also have the same reply for wlan/wlan0/eth1 etc. All I really want to do is be able to bring it up if it is down and visa versa, instead of have to run from one end of the house to the other, sure I can use VNC, but it would be simpler with a sudo ifdown ra0 or sudo dhclient ra0 down etc.

I will look into setting up Samba, but for what I want do not see why that is needed, IE not trying to share files back and forth.

---

### Post by pytheas22 on 2008-05-28
Alright, then yes I agree, you probably don't need samba.  I don't understand what you mean, however, by "seeing" your *wife's* interface.  Isn't her computer running Windows right now?  If it is, the only way to control it or its network interfaces remotely I think is to use remote desktop or vnc.  Running ifconfig or iwconfig on your Ubuntu machine will only show the interfaces for *your* machine, not neighboring ones, regardless of which operating systems they're running.  If your wife were running Linux, you could bring her interfaces up and down using an ssh session, but I don't know of any way to get functionality similar to ssh on Windows; moreover I don't even know if you can control network interfaces on Windows from the command line.  The only way I know is to enable/disable them in the network connections utility.

I'm sorry to keep asking for clarifications but I guess I'm still not entirely certain what your objective is.

---

### Post by yogo on 2008-05-28
> **pytheas22 said:**
>   Running ifconfig or iwconfig on your Ubuntu machine will only show the interfaces for *your* machine, not neighboring ones, regardless of which operating systems they're running.  If your wife were running Linux, you could bring her interfaces up and down using an ssh session,.


Ok well I may as well mark this solved, I guess I was trying to do something that is not possible.  I thought I should be able to see what interfaces are connecting to my router like I can with my router but thru terminal.

Yes I can use VNC to shut it down, just thought that I could thru terminal.

Thanks.

---

### Post by pytheas22 on 2008-05-28
Yes, I think vnc is the only solution.  Sorry it took so long to clarify your question, but I'm glad you've finally arrived at a solution of sorts.

---

