---
title: "Can't connect to internet - Realtek RTL8100B"
date: 2008-05-14
forum: Networking &amp; Wireless
---

### Post by Porwah on 2008-05-14
I need some help.  

I installed 8.04 successfully (I think) and have WinXP on the same machine.  

The integrated LAN for my Gigabyte GA-7VRXP mobo -- a Realtek RTL8100B according to the mobo manual -- works in WinXP but not in Ubuntu.  I'm very sad.

I have spent an hour or two for a few nights now searching these forums and Googling for any possible insight.  In the forums, I have only found a few threads on this specific chip and none have seemed to help.

I was really encouraged when I found this thread:
[HOWTO FIX no link detected Realtek 8168/8169 cards]("http://ubuntuforums.org/showthread.php?t=538448")

Unfortunately, that didn't seem to work for me or I'm still doing something wrong.

Any assistance would be greatly appreciated!

A few of my symptoms:
[LIST]
[*]Attempts to ping my router fail
[*]Under Admin / Network, I set it to DHCP
[/LIST]

Here is output of some commands I saw other users post on other threads:

sudo ethtool eth0:
```
Settings for eth0:
	Supported ports: [ TP MII ]
	Supported link modes:   10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Supports auto-negotiation: Yes
	Advertised link modes:  10baseT/Half 10baseT/Full 
	                        100baseT/Half 100baseT/Full 
	Advertised auto-negotiation: Yes
	Speed: 100Mb/s
	Duplex: Full
	Port: MII
	PHYAD: 32
	Transceiver: internal
	Auto-negotiation: on
	Supports Wake-on: pumbg
	Wake-on: d
	Current message level: 0x00000007 (7)
	Link detected: yes
```

lspci -nn:
```
00:00.0 Host bridge [0600]: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333] [1106:3099]
00:01.0 PCI bridge [0604]: VIA Technologies, Inc. VT8366/A/7 [Apollo KT266/A/333 AGP] [1106:b099]
00:08.0 Multimedia audio controller [0401]: Ensoniq 5880 AudioPCI [1274:5880] (rev 04)
00:0a.0 Modem [0703]: PCTel Inc HSP56 MicroModem [134d:2189] (rev 04)
00:11.0 ISA bridge [0601]: VIA Technologies, Inc. VT8233A ISA Bridge [1106:3147]
00:11.1 IDE interface [0101]: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE [1106:0571] (rev 06)
00:11.2 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 23)
00:11.3 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 23)
00:13.0 Ethernet controller [0200]: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ [10ec:8139] (rev 10)
00:14.0 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 50)
00:14.1 USB Controller [0c03]: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller [1106:3038] (rev 50)
00:14.2 USB Controller [0c03]: VIA Technologies, Inc. USB 2.0 [1106:3104] (rev 51)
01:00.0 VGA compatible controller [0300]: ATI Technologies Inc Radeon RV250 If [Radeon 9000] [1002:4966] (rev 01)
01:00.1 Display controller [0380]: ATI Technologies Inc Radeon RV250 [Radeon 9000] (Secondary) [1002:496e] (rev 01)
```

And sudo lshw -C network:
```
  *-network
       description: Ethernet interface
       product: RTL-8139/8139C/8139C+
       vendor: Realtek Semiconductor Co., Ltd.
       physical id: 13
       bus info: pci@0000:00:13.0
       logical name: eth0
       version: 10
       serial: 00:20:ed:28:f1:86
       size: 100MB/s
       capacity: 100MB/s
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=8139too driverversion=0.9.28 duplex=full latency=32 link=yes maxlatency=64 mingnt=32 module=8139too multicast=yes port=MII speed=100MB/s
```

---

### Post by Porwah on 2008-05-16
Bump.

---

### Post by chili555 on 2008-05-16
Under Windows, I think the little box 'Allow the computer to stupidly wreck Ubuntu by turning off this device' should be unchecked. Then does the device get an IP address? Check with:```
ifconfig eth0
```What is the result when you do:```
sudo dhclient eth0
```If it just times out, please let us see:```
cat /etc/network/interfaces
```Please let us know.

---

### Post by Porwah on 2008-05-16
Thanks for that post.  I unchecked that box but still didn't have any luck though.

This issue could be just a dumb network configuration issue.  Is it possible for anyone to tell from the post above and the command results if my machine looks configured correctly? I don't mean to sound helpless.  I'm just a little unsure if I even have my network settings correct.

In my Network settings, it does say DHCP.  I have my DNS's added under that (appropriate) tab.  I don't know what Search Domains are.  Tell me, where is the IP of my Gateway (router) supposed to go??? On WinXP and in OS X I have to explicitly add that.  I can't recall doing that in the Ubuntu install.  And I can't figure out where it would go in that Network dialog with the 4 tabs.

I'm attaching the results of the commands mentioned above.  It looks like I still don't have an IP.  I still can't ping my Gateway.

In the cat of the interfaces, I see it's got an address in there.  I tried a manual configuration with a static IP and set the Gateway specifically there.  But doing that I couldn't ping the router and had no connection still.  (I really want DHCP, but just tried that to see if I got anywhere.)  For some reason that address I manually set and the gateway still show up in that cat of interfaces.  I don't understand that.

I hope this sheds a little more light on my issue.  Thanks for any help you can give.

Grr... just saw that the dhclient output is empty.  I definitely got results back but the redirect didn't work for some reason.  I'll flip back to Ubuntu side and try that again.

---

### Post by Porwah on 2008-05-16
OK... the dhclient results look meaningful.

```
Internet Systems Consortium DHCP Client V3.0.6
Copyright 2004-2007 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/sw/dhcp/

Listening on LPF/eth0/00:20:ed:28:f1:86
Sending on   LPF/eth0/00:20:ed:28:f1:86
Sending on   Socket/fallback
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 4
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 13
No DHCPOFFERS received.
No working leases in persistent database - sleeping.
```

So it's failing to get to my router, right? 

That 255.255.255.255 doesn't look right.  Does that have to do with a subnet mask? Again, on WinXP and OS X I put that in explicitly.  I didn't see where to do that in Ubuntu.  Mine should be 255.255.255.0.

---

### Post by chili555 on 2008-05-17
Your *interfaces* entries are inconsistent.> auto lo
iface lo inet loopback


iface eth0 inet dhcp
address 192.168.11.25
netmask 255.255.255.0
gateway 192.168.11.1

auto eth0Just for the moment, please *sudo gedit /etc/network/interfaces* and make it look like this:```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
**#**address 192.168.11.25
**#**netmask 255.255.255.0
**#**gateway 192.168.11.1
```Then restart networking:```
sudo /etc/init.d/networking restart
```Save and close gedit. Let us know what happens.

---

### Post by Porwah on 2008-05-17
First, thanks for your reply.

I have since put it an addon card NIC to see if that made a difference and if there was some issue with my onboard LAN chip.  Still no luck.

(Should mention I disabled onboard nic in Bios when new card added.)

I did what you suggested only using eth1 instead of eth0 because the os seems to be recognizing that as my nic now.

Restarted network and then got similar results.  Still can't ping router.

Interesting stuff from restarting network (these are retyped, not copied, sorry).  I got a line in there like:

```
There is already a pid file /var/run/dhclient.eth1.pid with pid 134519072
```

Is that anything to be concerned with?

There are 3 DHCPDISOVER lines that go to 255.255.255.255.  That just doesn't look right.  I don't know the mechanics of how DHCP works, but my subnet mask should be 255.255.255.0.  

I got a "No DHCPOffers received" line.
Then "No working leases in persistent database - sleeping."

I don't know what those mean.

---

### Post by caraboy on 2008-09-26
I have the same integrated network chip and I can`t get it to work on Ubuntu 8.04 server.

When I boot up the pc I get this error:

```
This (id 10ec:8139rev10) is not an 8139c+ compatible chip. 
Try the 8139too driver instead.
```So I can`t even see the card in /etc/network/interfaces. I have only lo.  

Any ideas? :confused:

---

### Post by Porwah on 2008-09-26
I was able to get on using a special boot parameter.  I think it was noacpi or something.  I think I had multiple threads on this chip asking for help.  One of them lists the correct parameter.

---

### Post by caraboy on 2008-09-27
> **Porwah said:**
> I was able to get on using a special boot parameter.  I think it was noacpi or something.  I think I had multiple threads on this chip asking for help.  One of them lists the correct parameter.

Could you please post the parameter that worked for you? I would be grateful.

---

### Post by Porwah on 2008-09-27
The parameter was noapic.  It should show on post #46 of this thread:

[http://ubuntuforums.org/showthread.php?t=538448&highlight=noapic&page=5](http://ubuntuforums.org/showthread.php?t=538448&highlight=noapic&page=5)

---

### Post by caraboy on 2008-09-29
Thanks, but it`s not working for me. :( It`s an integrated network card.

---

### Post by Porwah on 2008-10-01
FWIW, mine was too...

---

### Post by lessless on 2011-03-22
On fresh install Ubuntu 10.10 passing noapic to the kernel doesnt do the trick - the adapter still not communicating.
But as far as i can understand from dmesg APIC is still enabled (APIC mode: flat).
Is there eny good, proven solution for Ubuntu 10.10 and onboard ethernet except buy new network card?

---

