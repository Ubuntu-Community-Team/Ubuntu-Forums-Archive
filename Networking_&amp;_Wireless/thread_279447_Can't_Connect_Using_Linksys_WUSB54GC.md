---
title: "Can't Connect Using Linksys WUSB54GC"
date: 2006-10-18
forum: Networking &amp; Wireless
---

### Post by sublime_ndg on 2006-10-18
Hi there, semi-noob here (brief stint with Gentoo, then Fedora).  Just installed Ubuntu yesterday, and I'm very impressed.  This forum is great, but I just can't find a solution for this, as there are so many variations of the same problem.

I have a Linksys Wireless-G USB Adapter, model WUSB54GC, and I'd like to connect to my wireless router using it.  I followed the guides to get there; I installed ndiswrapper (driver installed is rt73, system recognizes it), installed Wifi-Radar, and installed Network Manager.

When I try to connect to the network using System->Administration->Networking, the system does recognize my wireless card.  When I click on "Properties," it finds my home network, and I select that.  I type in the WEP Key (yes, it's correct), and click OK, the OK again.  I open Firefox, but no internet.

When I try to connect using Wifi-Radar, it always ends up saying "Could not get IP address"

Here are the results of:

iwconfig:
```
wlan0     IEEE 802.11g  ESSID:off/any
          Mode:Auto  Frequency:2.412 GHz  Access Point: Not-Associated
          Bit Rate:54 Mb/s   Tx-Power:20 dBm   Sensitivity=-121 dBm
          RTS thr:2347 B   Fragment thr:2346 B
          Encryption key:off
          Power Management:off
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

```

ifconfig:
```
wlan0     Link encap:Ethernet  HWaddr 00:16:B6:9D:53:48
          inet6 addr: fe80::216:b6ff:fe9d:5348/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)

```

iwlist wlan0 scan:
```
wlan0     Scan completed :
          Cell 01 - Address: 00:18:39:45:DD:3C
                    ESSID:"Home"
                    Protocol:IEEE 802.11g
                    Mode:Managed
                    Frequency:2.437 GHz (Channel 6)
                    Quality:0/100  Signal level:-48 dBm  Noise level:-256 dBm
                    Encryption key:on
                    Bit Rates:1 Mb/s; 2 Mb/s; 5.5 Mb/s; 11 Mb/s; 18 Mb/s
                              24 Mb/s; 36 Mb/s; 54 Mb/s; 6 Mb/s; 9 Mb/s
                              12 Mb/s; 48 Mb/s
                    Extra:bcn_int=100
                    Extra:atim=0
                    Extra:wpa_ie=dd180050f20101000050f20201000050f20201000050f2020000

```

Any ideas as to why I can't fully connect?  The only thing I could see that was weird (and I'm sure I'm missing a lot) is that under ifconfig, my IP address is funky.

Thanks for your help, and I hope to be using Ubuntu for quite some time!

---

### Post by sublime_ndg on 2006-10-18
Bump

---

### Post by sublime_ndg on 2006-10-19
Anyone?  Help please!!! :(

---

### Post by jerrallan on 2006-10-19
Hello, I am having similar problems with a LinksysWUSB54G.  What I have found out is that there is no association with the access point.  You notice that you haven't got many responses.  I think there is a reason why that is the case.  One of my few responders indicated that wireless is not Ubuntu's strong suit.
Good Luck
Jerry

---

### Post by sublime_ndg on 2006-10-19
Thanks Jerry.  Can you explain exactly what you mean by "no association with the access point?"  If you mean that the wireless card can't see the wireless router, I'd disagree.

When I try to configure the network via System->Administration->Networking, my network is detected, along with my neighbor's network.  These are the same two networks my XP machine picks up when scanning.  I enter in the Key, and exit out, but still no internet.

I think what I'm going to try and do is re-configure the router this weekend, perhaps without encryption, and see if I can connect.  We'll see what happens.

---

### Post by jerrallan on 2006-10-20
Judging from the iwconfig you did, you can't associate with an access point either.  For my computer access point is 192.168.0.1,I think.  When I change the frequency channel at the router connection, iwconfig on the wireless computer shows that change.

So ubuntu recognizes the usb device and it is working properly.

On another url one guru said this:
" ...Now proceed to see if it's associated with the access point, using the iw-tools. Type "iwconfig wlan" as root. It should tell you if the interface is associated with any access points. If not, you could try changing a couple of parametres - setting an ESSID manually for instance with iwconfig wlan0 essid mynet (assuming mynet is your essid), or changing the mode the interface operates in (for instance iwconfig wlan0 mode managed - or ad-hoc etc...) Until you get the interface to associate with the AP, you're coming no nearer. You can also test if the interface can "see" the AP at all, using "iwlist wlan0 scanning" - provided the interface supports scanning.

If these commands show your interface as being already associated with the AP, your problem probably lies in not having acquired an IP lease from the DHCP server running on the AP (provided there's DHCP activated). You can manually fetch a lease by typing "dhclient wlan0", or "dhcpcd wlan0" or "pump wlan0"
etc... "

I tried dhclient and it did not fetch a lease, but did not recognize dhcpcd or pump as a command.  Maybe this would be helpful to you.  It hasn't worked for me [yet].  

I have also tried disabling security, and iwconfig shows the change by indicating that it is multicast. I have tried changing to WPA-PSK.  Nothing has worked so far.  
I am new to linux, but find it fascinating.

If you get a solution, let me know.

Good luck
Jerry

---

### Post by jerrallan on 2006-10-22
Okay, after beating my head against the wall for a week or so, I went back through the threads on the great instructions on how to install a driver for WUSB54G driver. One commenter stated he succeeded using rausb.

I uninstalled ndiswrapper. I went to the /etc/modprobe.d/blacklist file and commented out the section to blacklist the rt2570.

I rebooted and went to System>Administration>Networking and configured rausb and came up with a familiar old problem:the screen froze up and I had to reboot.

So I went to the command line and
entered sudo iwconfig rausb0 essid <XXXXX>
then entered sudo iwconfig rausb0 encryption on
then         sudo iwconfig rausbo encryption <XXXX-XXXX-XX>

and I had an internet connection.

On reboot, I found out that I had to go through the procedure again. Plus, I had to pump for a connection by adding:
sudo dhclient rausb0.
I put this in a script and and do it after rebooting.

This is a workaround, and I can maintain an internet connection until rebooting.  Any suggestions for a permanent fix?
Jerry

---

### Post by sublime_ndg on 2006-11-06
Just wanted to give an update on this:

I never did get my WUSB54GC to connect.  I tried everything on these boards, but no luck.

I continued to use that card with my XP machine, and it worked just fine.  However, the card got dropped, and I ended up returning it and I got another one.  Before I went to replace it, I looked up this page: [https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported]("https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported") to make sure that I got a card that was compatible.

I ended up going with the D-Link WNA-2330.

I got home, plugged it in, and tried to configure it.  Once again, the system recognized the card, but no connection.

Finally, and I should have tried this a long time ago, I just reset the router's settings.  Turns out that the router had WPA encryption, and I have read a bit about how Linux doesn't always play nice with WPA.  So I reset it to WEP, reconfigured the connection on my Ubuntu machine, and voila!  It connected, and now it works great.

I read somehwere that the WNA-2330 doesn't have the best signal strength but I disagree.  I connected from everywhere around my house, with no loss of strength.

I think that the WUSB54GC would have worked as well.  I thought about resetting the router a while back, but I just never did.  Since I got Ubuntu to recognize the card, I believe that the method for setting up the WUSB54G works for the WUSB54GC as well.

So thanks for your help, Jerry.  I was this close to calling it quits with Ubuntu until I could get a laptop that had an internal card, but fortunately, I can keep going, and I'll be back to these boards for more advice.

---

### Post by deusknight on 2007-01-25
I too am having tremendous problems with this same device.  I've noticed that the LED doesn't even light up on it, even though it is recognized by Ubuntu (Edgy Eft I think I have) and listed in the Networking GUI thing (<- ya I'm a n00b).  At any rate, I'm guessing there are some configuration files that need to be manually edited and perhaps some commands that need to be run on it to make it work?  I've been through a million forums on this topic and each of them suggest something different, and I've tried em all... :(  Oh and I've tried it with both WEP and WPA... no luck...

---

### Post by deusknight on 2007-01-25
Oh and by the way... what is rausb??  My computer lists the card as wlan0, do I need to change that?:confused:

---

### Post by scorptig on 2007-04-28
wusb54gc linksys
ubuntu feisty dawn 7.04 i386

So far nobody seems to know how to configure.
One page says use ndiswrapper, another ralink, tools are available, WiFi Radar, I see
network, I can't use network.

I really would like A Clear To The Point Step By Step Instruction.
Nearly 2 weeks I,ve looked at Forum, and the instructions are incomplete.

So someone at »Ubuntu has to clarify, the mess.

---

### Post by Grimy on 2007-08-01
This adapter does work if you use ndiswrapper. You can easily get the windows drivers at the linksys website and then use this guide to set it up.

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper]("https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper")

 I've used it in several other distros and ubuntu and it works great every time.

---

### Post by hendricks on 2007-08-03
Hey guys, I've come up with a solution for wusb54gc (it seems like a very popular device!). I use ndiswrapper (32bit or 64bit, depending on your distro) and it works for Ubuntu and Kubuntu. To the guy who got it to work with rausb, congrats! I could never get mine to work. Just follow the directions on the page here:

[http://ubuntuforums.org/showthread.php?p=3127959]("http://ubuntuforums.org/showthread.php?p=3127959")

Its really easy and it works. Put the stuff on your computer and type in one command. Couldn't be simpler.

  --Hendricks

---

### Post by kevdog on 2007-08-03
Since this requires the rt73 driver, you need to download, compile, and install the serial monkey rt73 drivers.  This fix is a known solution.  Im not sure where all the debate comes from.  The definite thread on how to do this is here:

[http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey](http://ubuntuforums.org/showthread.php?t=400236&highlight=serialmonkey)

There is no use screwing around with network configuration parameters until you have the wireless driver installed correctly

---

### Post by bigngamer92 on 2008-02-12
I have no encryption on my Router and my WUSB54GC recognizes the Network with about 84% strength. My first time into Ubuntu I tried to connect and it went online.  But within 10 minutes (and during a download too) it decided to stop working.  All attempts to connect to the network that is still appearing fail.  I realize now that I don't need ndiswrapper as the card is described as an out of the box card but it still does not explain my lack of Internet.

---

### Post by MadeR on 2008-04-15
in the past i had problems with wireless card.
the solution was always using the windows drivers with ndiswrapper.

---

