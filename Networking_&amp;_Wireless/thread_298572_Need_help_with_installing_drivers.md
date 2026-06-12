---
title: "Need help with installing drivers"
date: 2006-11-12
forum: Networking &amp; Wireless
---

### Post by Snoopy1966 on 2006-11-12
Hello,
This has been a huge stumbling block to get my wireless going on my desktop.  Reading tons of stuff and it all seems to hard for a new person like me to Linux. Reading at the Wiki page for ndiswrapper, I looked at cards supported.  I have the Linksys WMPG54G v4.1 adapter.  I found it and it said to get the driver from ralinkltech.  I downloaded it, but I do not have a clue how to use it.  I am using the KDE desktop on Ubuntu.  At least I think I am.  I installed Dapper Ubuntu and then the KDE desktop. This is what it said at Wiki.  I have the file, but I need help to install it.   It sounds like I do not need ndiswrapper for this correct?  

EDIT: This is the link I used for the Wiki page [http://ndiswrapper.sourceforge.net/mediawiki/index.php/List](http://ndiswrapper.sourceforge.net/mediawiki/index.php/List)

EDIT again:  Looking at this further. Do I need to install this in Windows first?

```
Card: Linksys #[WMP54G v4.1], 54mbps -- [link here|List#WMP54G v4.1] 
Chipset: Ralink RT61 
pciid: 1814:0301 and 1814:0302 
Driver: Don't use driver that ships with card, it didnt work with ndiswrapper. Use the close source driver from Ralink http://www.ralinktech.com. It compiles for 2.4 and 2.6 kernels. 
Other: The rt2x00 Open Source Project (http://rt2x00.serialmonkey.com) have now a driver - but realy beta. 
Other: The Ralink driver works great. It is not a plug and play, you need your kernel headers, the appropiate gcc (3.4) but when you can link it together and put it where it loads at startup, it works great. I am using WPA without any problem
```

---

### Post by FrodoB on 2006-11-12
You have two paths you can go:

1) Use the Ralink rt61 driver, this will use a kernel module.

2) Use ndiswrapper, this uses Windows ndis drivers.

When you look at the documentation keep them separate as what applies to one does not to the other.

There should be good documents on the forum for both methods. I would try rt61 first, but that is just my preference. Unarchive the download and find any files that are called readme, readme.txt or their uppercase equivalents.

Someone will help out if you do not understand what it is asking you to do.

---

### Post by Snoopy1966 on 2006-11-13
Thanks for the reply.  Do I install the rt61 in Windows first?

---

### Post by abbeychase on 2006-11-13
can you explain what you mean when you say "wireless on my desktop"?  Also, when you install a driver in windows, you can't use it in linux.  They are usually proprietary and linux is not a MS operating system.

Also, I use the same router, what's the problem?  I don't use any 3rd party drivers to get it working.  All i need are the drivers for my ethernet card.

---

### Post by Snoopy1966 on 2006-11-13
OK sorry for not explaining very good.  I have two desktops.  One where my router is that has the Linksys WRT54G Router.  The PCI-G adapter is WMPG54G v4.1 in mt second desktop that receives the signal.  I can see it working in Networking tools, but I can not get it to connect.  I did not find a read me file in the rt61 driver I downloaded.  If you use the link I provided, it is under the L section and then number 14.  I downloaded the Linux version as well, but I have no clue on how to install it.  I think I see the problem now.  I downloaded the Windows one and the Linux one.  Obviously I need to use the Linux, duh to me.   These .tar .gz files have me very confused on how to install them or even where to extract them.  I even read the How to install anything in Ubuntu and that is a little over my head right now.  I understand some of it.  

So what should I do then?  Get rid of the driver in Widows first, then try to connect?  I have the Ethernet card, and that is what I am using now.  50 feet of it to connect to my router.  I know there is a learning curve here to all this stuff.  I am very new to all this, so please forgive all the basic questions.  I am dizzy from reading so many links and tutorials and I do not know what applies to me, our even how to follow some of these very complex set ups. Thanks for the help.  I really hope I can get wireless working for me.  50 feet of Ethernet cable does not really look so nice running through my apartment :)

---

### Post by phelixnyc on 2006-11-13
I have had trouble even logging on to my routers setup page. Im using a Linksys router (WRT54G v.5). Can some one please tell me where to begin fixing this problem?

---

### Post by FrodoB on 2006-11-13
Snoppy1966;

I think that you could either do the hard thing and deal with building the rt61 driver on your Ubuntu machine, which I am trying to do at the moment in order to make you some instructions, or you could swap the positions of your machines in your apartment and install the wireless on the Windows machine, which I am assuming will work fairly easily.

The only reason that I say this, is that the rt61 driver for Linux is in pretty poor shape compared to the rt73 driver that I am using. The Make file does not even install the software for you and I have not got it quite figured out yet. If you swap machine locations you can deal with Linux Wireless after you get a little more experience.

Let us know what you decide to do.

---

### Post by phelixnyc on 2006-11-13
Well I have two hdd's on main pc. One Linux, one Windows and I have laptop that connects to my router. Iam attempting to access my start up page from my main pc. Iam not sure if that changes your suggestion.

---

### Post by Snoopy1966 on 2006-11-13
OK Thanks for the reply.  I think I will leave the computers where they are now.  I can deal with the cable until I get this going.  So should I download the rt73 driver then and use that one then?

Question that might help solve all these problems.  With the Linksys  router I have, can I install any PCI adapter that will work with Linux without all these headaches?  Or does it have to be a Linksys adapter card in the desktop that receives the signal?

---

### Post by FrodoB on 2006-11-13
No the rt73 is not for your device, it is just the Ralink driver that I use and it works well.

You need the rt61 and it is not as easy an install. I still have not got it figured out yet.

If money is not object, here is where I got my working rt73 device, a Belkin F5D7050 ver 3000:

[http://www.newegg.com/Product/Product.asp?Item=N82E16833314011](http://www.newegg.com/Product/Product.asp?Item=N82E16833314011)

It is not as easy to install as you might like.  Here is what you have to do for it, see my post in:

[http://www.ubuntuforums.org/showthread.php?t=296281](http://www.ubuntuforums.org/showthread.php?t=296281)

It is rather involved as you can see, but it does work in the end. Don't buy the device even if you want to until you can get through the whole process of compiling and installing the driver.

I am sure the rt61 device can be made to work as well, but I do not have a device to work with, so I can't give exact instructions.

Wireless in Linux takes everything back 10 years in terms of user  friendliness for new users. It usually works well once you have it going, but getting there can be really difficult depending upon which devices you have.

The right way is to do a lot of research, determine which devices you can work with and then even before buying them try to get the drives compiled on your system. If you buy first you may never get it to work.

Best of luck with whatever you decide to do.

---

### Post by FrodoB on 2006-11-13
Another card that is fairly easy to install compared to the others is the Belkin F5D7050 ver 4000. It has a Zydas zd1211b chip in it and the card costs around $40 at Wal-Mart. If you buy one of those you can check the outside of the carton and it will tell you what version it is:

Here is what the driver install procedure looks like for it:

[http://www.ubuntuforums.org/showthread.php?t=295843](http://www.ubuntuforums.org/showthread.php?t=295843)

---

### Post by Snoopy1966 on 2006-11-13
Thanks for the replies.  This card the Belkin F5D7050 is a PCI card?  I think I would prefer a PCI card over a USB for speed reasons.  I think the PCI cards are faster, just going on what I have read.  So hopefully that card will work with the Linksys router?  That install does not look to bad.  I might be able to muddle my way through it.  Any other cards that you know of that will work too?  The USB one was a good price but I did not see it at any stores to buy, just on-line.  I just did a search for it.  Maybe if I have a few choices I can pick from I will go down to Best Buy and see if I can find one.  Can it be a G or B card since the Linksys router supports that signal?  OK thanks again for the help. :)

---

### Post by Snoopy1966 on 2006-11-13
Hello I thought I would post this before I go any further in making a purchase of a new card.  I can see may card and I see packages being sent and received. When I type iwconfig in the Terminal I get this

```
lo        no wireless extensions.

eth0      no wireless extensions.

ra0       RT61 Wireless  ESSID:""
          Mode:Auto  Frequency:1 MHz  Bit Rate=54 Mb/s
          RTS thr:off   Fragment thr:off
          Link Quality=0/70  Signal level:-121 dBm  Noise level:-111 dBm
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

sit0      no wireless extensions.


```

It looks like I have the RT61 already installed.  Any ideas from here?  Thanks

Here is ifconfig too

```
eth0      Link encap:Ethernet  HWaddr 00:0C:F1:FB:86:42
          inet addr:192.168.1.101  Bcast:192.168.1.255  Mask:255.255.255.0
          inet6 addr: fe80::20c:f1ff:fefb:8642/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:11315 errors:0 dropped:0 overruns:0 frame:0
          TX packets:10909 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:10163203 (9.6 MiB)  TX bytes:1850679 (1.7 MiB)

lo        Link encap:Local Loopback
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:59 errors:0 dropped:0 overruns:0 frame:0
          TX packets:59 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0
          RX bytes:2972 (2.9 KiB)  TX bytes:2972 (2.9 KiB)

ra0       Link encap:Ethernet  HWaddr 00:16:B6:5A:3F:B0
          inet6 addr: fe80::216:b6ff:fe5a:3fb0/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:10270 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6776 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:882165 (861.4 KiB)  TX bytes:0 (0.0 b)
          Interrupt:225

```

How about this too dhclient

```
Internet Systems Consortium DHCP Client V3.0.3
Copyright 2004-2005 Internet Systems Consortium.
All rights reserved.
For info, please visit http://www.isc.org/products/DHCP

can't create /var/lib/dhcp3/dhclient.leases: Permission denied
Can't create /var/run/dhclient.pid: Permission denied
drop_privileges: could not set group id: Operation not permitted

```

---

### Post by FrodoB on 2006-11-13
Known to Work in Ubuntu 6.10 Edgy Eft, pretty much plug and play.

Beware, if a model has a version change then all bets are off.

I have seen each of these work on someone's Edgy Eft system.

PC CARDS (PCMCIA)

802.11b:

SMC 2532W-B                  802.11b High Power PC Card 200mW Prism Chipset, has an internal antenna, can take an external as well

SMC 2635W                    802.11b PC CARD Ralink rt2400 Chipset

SMC 2635W V.2                802.11b PC CARD Ralink rt2400 Chipset

EnGenius NL-2511CD Plus EXT2 802.11b High Power PC Card 200mW Prism Chipset, Requires external antenna

802.11g:

Link Sys WPC54G              802.11g TI ACX Chipset not sure which one, this is an older card so new versions may not have the same chip

D-Link DWL-G650              802.11g AirPlusXtremeG Atheros


Anything with an Atheros chipset is usually the best for PC Cards. 

Anything that says it is Atheros G or Atheros Super G
is supposed to work in PC Card and PCI designs. 
But be aware that Linux madwifi drivers do not work at
all on Atheros USB designs.  

There are PCMCIA cards out there that use the Ralink rt2500 series and they should be
fine as well, but I have not seen one for testing.

I would stay away from anything with a TI chipset as TI does not cooperate with 
anyone who wants to make open source drivers. If you have an opportunity to  get
a card cheap then go for it, but do not seek them out.

For USB the F5D7050 ver 3000 and ver 4000 will work.

---

### Post by Snoopy1966 on 2006-11-13
Thanks for all the info.  So even though I can see my card I have now, is it useless to try to connect to it?  Any options?

I am using Dapper also.  I did not want to try Edgy because it was newer and reading through here at the forums said it would be better to start with Dapper.  

I will write the list down and go out and see if I can find any of these cards or USB adapters.  I have to go out anyway, so why not have some fun.

Anything different if I am using Dapper as far as adapters?

---

### Post by FrodoB on 2006-11-13
I have not used wireless on Dapper, so I cannot say.

---

