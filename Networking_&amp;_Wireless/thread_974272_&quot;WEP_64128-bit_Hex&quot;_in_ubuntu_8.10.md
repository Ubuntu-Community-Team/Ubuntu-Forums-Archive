---
title: "&quot;WEP 64/128-bit Hex&quot; in ubuntu 8.10"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by uros.mil on 2008-11-07
Hi,

I have moved from ubuntu 8.04 to ubuntu 8.10. But now I can't connect to wi-fi.
In ubuntu 8.04 I would choose "WEP 64/128-bit Hex" enter my 26 long pass and wi-fi worked as expected.
In ubuntu 8.10 there is NO option for "WEP 64/128-bit Hex", only "WEP 128-bit Passphrase" and "WEP 40/128-bit Key". Neither of those can log me to wi-fi.

How to overcome this?

Thanks,
Uros.

---

### Post by radi777 on 2008-11-08
same problem for me.... ubuntu 8.04 worked ok wif wifi. ubuntu 8.10 doenst work at all. I go back to Windows xp. after a lot of bad experiences wif linux. Now I know what windows really is: its the best OS by far.Plug and play. everything works just out of box and there is no wired nerd code and confic typing stuff.
I sick of all this linux stuff that cost sooo much time.....disapointed!

---

### Post by Psicodelico on 2008-11-08
I have the same  problem. For a while the solution is: Install WICD.

---

### Post by neogeek on 2008-11-08
I was connecting to my 64-bit WEP router all fine yesterday until I did the updates. This morning, the network manager became 40/128 instead.
I could change my router WEP to 128 but I was thinking I should solve the problem instead as I may encounter other 64 WEP elsewhere.

Reading this thread, I downloaded Wicd and it is working fine for me now.

Thanks!

---

### Post by uros.mil on 2008-11-08
Hi,

I have installed "WICD" and now wi-fi works. Even after suspend wi-fi is present.
Thanks to Psicodelico for pointing to this useful app.
Now I'm happy Ubuntu user again. :D

Uros.

---

### Post by CHOPS 125 on 2008-11-23
I had the same problem, worked fine until I ran updates in 8.10.

---

### Post by jarchie219 on 2008-11-30
Hoe can I get and install WCID if I don't have network connectivity under Ubuntu?  I have connectivity with WinXP.

---

### Post by mircomaster on 2008-12-15
This is sooo stupid man! How can you releae this version without ckecking
ANY possible WLAN configuration??? 
:confused:

Same Problem (F****) Release don't support 64 bit HEX WEP key. 

And now?

No connection to the internet, so apt-get install wicd is impossible


THIS REALY SUCKS!!!!!!!!!!!!!!!!!!!!!!!!!!


Connection to the internet is nearly as importend as a working kernel, man!! I think many people will go back to Windows, now

BAD, BAD, Thing, like releasing a not working kernel....

I'm so pi***t off

---

### Post by Cris(c) on 2008-12-28
I believe there is a way to make the wi-fi work without having to install wicd. Here is how I did it:

1) Add the following repositories to update network-manager:

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main

2) run apt-get update

After this, your network manager should be able to receive wep 64/128-bit Hex keys.

Hope it helps,

Cristian.

---

### Post by scoobard on 2009-01-30
this is a total embarrassment for linux and ubuntu. how can they screw up such a simple yet crutial part of what having a computer is about - connecting to the internet. i was having an ace time on ubuntu, and now i just can't be arsed with it anymore. i've tried to install wcid, unsuccessfully, and adding the repositories you mentioned, again, unsuccessfully. so many people use 64bit wep! serious mistake!!

---

### Post by braddock on 2009-02-16
I'm chiming in on this as a veteran of pre-1.0 kernel Linux.  This Network Manager WEP situation is by far the worst I've seen in an Ubuntu release.  I keep hoping the next update will fix it but so far none has.

I enter my 64-bit WEP key into Network Manager.  Sometimes it immediately connects ONCE, sometimes it does not, but it never remembers the WEP key the next time I try to log into the network, and it never automatically logs in once I've left the network.

I've fallen back to an /etc/network/interfaces configuration, which "often" works with a manual ifdown/ifup, but NM appears to interfere with it at times.

This is on a Dell E1505 "Ubuntu Laptop" that came pre-installed with Ubuntu 18 months ago.

Please let someone bring back flat text config files over this unmanageable NM registry.  I never thought I'd live to see the day that Linux could have a corrupted registry!

---

### Post by Favux on 2009-02-16
Hi braddock,

This workaround may apply to your situation:

[http://ubuntuforums.org/showthread.php?t=1010650]("http://ubuntuforums.org/showthread.php?t=1010650")

---

### Post by ttapping@hotmail.com on 2009-04-13
Count me as another thoroughly disappointed ubuntu tire kicker. Absolutely cannot get wep security working. Must have put 8 hours in on it for my wife's new netbook. I was thoroughly jazzed over the Chinese language support.
i really wanted to get away from the Evil Empire but failed.

Way to make a 10 year vet of the industry feel really stoopid...

---

### Post by ktrnka on 2009-04-13
To all in this Thread: I cannot STRESS how much you should NOT be using WEP at all, ANYWHERE. It is an extremely sad excuse for a wireless security measure. If your router does not support WPA.. I think it's time for an upgrade.

[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9015559]("http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9015559")

---

### Post by Rohaq on 2009-04-17
It's not always that simple: For example, my university uses 128-bit WEP for its network, due to some compatibility issues, though I think that they're considering upgrading to a form of WPA soon.

We were using 64-bit WEP to demonstrate its weaknesses in the form of WEP key cracking, followed by the use of a rogue DHCP and DNS server :)

Now we have to use a 128-bit WEP key, which will take considerably longer to crack :(

---

### Post by chili555 on 2009-04-17
> If your router does not support WPA.. I think it's time for an upgrade.For some of us here, throwing money at the problem is not a solution. Network Manager ought to do its job correctly. 

For this exact reason, I do not use Network Manager. I set my WEP details in /etc/network/interfaces. It connects properly every time. When I take my laptop out of town, to a hotel that offers free wifi, I comment out my details and scan and iwconfig and connect perfectly.

It's very sad that Network Manager is a frustration for many of us, rather than an aid. It's also very sad that lots of desktop machine owners struggle with connections when the machine will never be lugged down to the cyber cafe, university or coffee shop. My recommendation to desktop stay-at-home machine owners is to uninstall Network Manager immediately; you have no need for it.

---

### Post by Chamelion on 2009-04-28
I have been using Ubuntu for a few years now. I have learned a little bit in this time, but I do not have the time to get to much into changing things by writing into files etc.
I just tried Intrepid Ibex on my wives eeepc. I cannot get onto the Internet because of this. Not so much of a problem because she wants to get wireless usb dongle and does not need our main connection. I do not have the time to try the various possible workarounds. Correct me if I am wrong but I believe that the Long support version Ubuntu does not have as good as support for usb wireless.  
Ubuntu is the main Linux distribution anybody who wants to try Linux will probably get to use.
With these sort of problems a lot of potential new users will go straight back to M$.
Especially Net Book users who give a great opportunity to introduce Linux.
It does not matter if something is not so safe or safer. People want to use what they know. They can learn, but it is not a good idea to turn them of so quick.
Ubuntu is a great Distro and by far a too sophisticated operating system to have faults like this.
Big mistake to not fix this before release.
Ok, I have finished venting.Back to the eeepc.:lolflag:

---

### Post by mickathome on 2009-05-22
I'm having the same problem. Just can't seem to get it to work.

Ever since the Upgrade to 8.10 an it all went bad. Unsecured wireless works but I cannot connect to my network or any other
wireless network with WEP. Everything worked great in 8.04.

I've tried all sorts of fixes from forums but nothing works so far.

Dell 600m

Linux tazl 2.6.27-14-generic #1 SMP Wed Apr 15 18:59:16 UTC 2009 i686 GNU/Linux

>lshw -C network
  *-network:0             
       description: Ethernet interface
       product: NetXtreme BCM5705M Gigabit Ethernet
       vendor: Broadcom Corporation
       physical id: 0
       bus info: pci@0000:02:00.0
       logical name: eth0
       version: 01
       serial: 00:0f:1f:a1:c3:54
       size: 100MB/s
       capacity: 1GB/s
       width: 64 bits
       clock: 66MHz
       capabilities: pm vpd msi bus_master cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt 1000bt-fd autonegotiation
       configuration: autonegotiation=on broadcast=yes driver=tg3 driverversion=3.94 duplex=full firmware=5705-v3.16 ip=192.168.15.103 latency=32 link=yes mingnt=64 module=tg3 multicast=yes port=twisted pair speed=100MB/s
  *-network:1
       description: Wireless interface
       product: PRO/Wireless LAN 2100 3B Mini PCI Adapter
       vendor: Intel Corporation
       physical id: 3
       bus info: pci@0000:02:03.0
       logical name: eth1
       version: 04
       serial: 00:04:23:7d:12:db
       width: 32 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list ethernet physical wireless
       configuration: broadcast=yes driver=ipw2100 driverversion=git-1.2.2 firmware=712.0.3:3:00000001 latency=32 link=no maxlatency=34 mingnt=2 module=ipw2100 multicast=yes wireless=unassociated
  *-network DISABLED
       description: Ethernet interface
       physical id: 2
       logical name: pan0
       serial: 1e:42:b7:a8:27:5d
       capabilities: ethernet physical
       configuration: broadcast=yes driver=bridge driverversion=2.3 firmware=N/A link=yes multicast=yes

------------------------------------------------
Tried wicd.
Removed and reinstalled the network manager.
Can't remember the name but installed the kernel back modules.

Any ideas?

Thanks,

Mick

---

### Post by ByeByeMS on 2009-06-14
> **chili555 said:**
> For some of us here, throwing money at the problem is not a solution. Network Manager ought to do its job correctly. 


If I wanted to upgrade my hardware or have stuff stop working every time I upgraded software on my computer I would have stayed with Micro$oft!

---

### Post by mickathome on 2009-06-15
Agreed.

Does anybody know if this is fixed in Ubuntu 9.x?

Really not having any luck with 8.10. May have to go back to 8.04
but if I'm goign to wipe out the partition to reinstall I might 
as well give 9.x a chance.

Just like to know if I'm wasting my time.

Thanks,

Mick

---

### Post by munky99999 on 2009-06-15
Wep 40/128bit key is the hex key? At least that is how I used it.

You simply cant have the colons in the key.

12:34:56:78:90:12

The real key is 123456789012

---

### Post by webdevelopment on 2009-09-16
doesnt work for me in 9.04, this is really a joke (ubuntu)

does anyone who makes ubuntu read this?

---

### Post by webdevelopment on 2009-09-16
> **chili555 said:**
> For some of us here, throwing money at the problem is not a solution. Network Manager ought to do its job correctly. 

For this exact reason, I do not use Network Manager. I set my WEP details in /etc/network/interfaces. It connects properly every time. When I take my laptop out of town, to a hotel that offers free wifi, I comment out my details and scan and iwconfig and connect perfectly.

It's very sad that Network Manager is a frustration for many of us, rather than an aid. It's also very sad that lots of desktop machine owners struggle with connections when the machine will never be lugged down to the cyber cafe, university or coffee shop. My recommendation to desktop stay-at-home machine owners is to uninstall Network Manager immediately; you have no need for it.

i can edit files, but what are the usage instructions for iwconfig? is it preinstalled with ubuntu?  this takes me back to the stone ages and if i have to do this i might as well use smoke signals (but still tell me how to scan with iwconfig please...)

---

### Post by chili555 on 2009-09-16
You will need to stop Network Manager first:```
sudo /etc/init.d/NetworkManager stop
```Then let's scan:```
sudo iwlist wlan0 scan
```You should see your network. Then do:```
sudo iwconfig wlan0 essid yournetwork
sudo iwconfig wlan0 key 096f280e2b open
sudo dhclient wlan0
```Please be sure your key is HEX, that is, either 10 or 26 characters and it's entered with lower-case letters, as above, no dashes, colons, etc.

I have an experimental laptop that I got for very cheap, to test various bleeding edge things. It connects perfectly using Network Manager to my WEP network. I was actually shocked, but I've kept it in place.

Both of my desktop machines had Network Manager exorcised upon installation.

I think the developers of Ubuntu (who are different from the developers of Network Manager) would suggest you might have better luck with Ubuntu 9.04.

---

### Post by webdevelopment on 2009-09-16
> **chili555 said:**
> You will need to stop Network Manager first:```
sudo /etc/init.d/NetworkManager stop
```Then let's scan:```
sudo iwlist wlan0 scan
```You should see your network. Then do:```
sudo iwconfig wlan0 essid yournetwork
sudo iwconfig wlan0 key 096f280e2b open
sudo dhclient wlan0
```Please be sure your key is HEX, that is, either 10 or 26 characters and it's entered with lower-case letters, as above, no dashes, colons, etc.
 
I have an experimental laptop that I got for very cheap, to test various bleeding edge things. It connects perfectly using Network Manager to my WEP network. I was actually shocked, but I've kept it in place.
 
Both of my desktop machines had Network Manager exorcised upon installation.
 
I think the developers of Ubuntu (who are different from the developers of Network Manager) would suggest you might have better luck with Ubuntu 9.04.
 
i have 9.04
 
i've installed wicd and it still wont connect... wicd sees my network at least, but it wont let me specify the ssid
 
is there a way to get network manager to function properly?

---

### Post by chili555 on 2009-09-16
> i have 9.04I guess I was confused by the title of the thread.> wicd sees my network at least, but it wont let me specify the ssidI'm more confused! If it sees your network, doesn't Wicd already know your ESSID? Why does it need to specified?

---

### Post by jhofer2 on 2010-04-13
I first ran into this problem when I reformatted my hard drive and decided to upgrade from 9.04 to 9.10. I tried the other solutions mentioned here, and none worked. I finally reinstalled 9.04 and received a prompt from terminal about a proprietary driver for my Broadcom wireless card. I chose to install it, and now my wireless works perfectly, even though it still doesn't provide an option for 64-bit. I don't know if there's a way to install the driver on 9.10, but this fix does hold up through upgrades.

---

### Post by Michl on 2010-04-15
> **Cris(c) said:**
> I believe there is a way to make the wi-fi work without having to install wicd. Here is how I did it:

1) Add the following repositories to update network-manager:

deb [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main
deb-src [http://ppa.launchpad.net/network-manager/ubuntu](http://ppa.launchpad.net/network-manager/ubuntu) intrepid main

2) run apt-get update

After this, your network manager should be able to receive wep 64/128-bit Hex keys.

Hope it helps,

Cristian.

I'm having trouble finding the key for this.  Release.gpg does
not import for me.  I saved in many ways, including as key.txt.

---

### Post by techdude on 2010-05-24
> **chili555 said:**
> You will need to stop Network Manager first:```
sudo /etc/init.d/NetworkManager stop
```
Tried this on a laptop running Karmic. I simply get an error saying that the process cannot be found.

The manual connection method suggested lets me find the network, but it simply won't connect.
Do I have a problem or am I missing something out somehow?
Adapter is a Linksys WPC54G laptop card, and I'm using the Windows Wireless Drivers utility in Ubuntu. I can connect to my router, and to the Internet, using an ethernet cable, but this is a pain because it means I can only use the laptop by standing next to the router. 
What do I need to do to make it work?

---

### Post by chili555 on 2010-05-24
> What do I need to do to make it work?It may not be Network Manager that is not cooperating; it may be the driver. Please open Applications > Accessories > Terminal and do:```
ndiswrapper -l
iwconfig
```Post the result.

Does Network Manager see your network? Does it ask for your key? Does it try to connect?

---

### Post by techdude on 2010-05-24
Using the ndiswrapper -l,
I get 

"lsmvnds : driver installed
device (11AB:1FAA) present
lstinds : driver installed"

These are my wireless adapter drivers.

---

