---
title: "Creating a wireless adhoc network"
date: 2010-04-24
forum: New to Ubuntu
---

### Post by ambient007 on 2010-04-24
I would like to setup a wireless connection between my laptop (karmic) and my fiancee's (winXP, until I convince her to let me setup a dual boot ;)) .
 
The idea being that when my pc is connected to the web via ethernet, she will also be able to browse.
 
It would be great be able to do it so no matter which computer is connected via ethernet, the other can go on via wireless.
 
I do not hav and would rather not purchasea wireless router.
 
Also it would be great if the network could be confirgured so we can share files netween machines.
 
 
 
 
I'm somewhat of a linex newb, does anyone have some clues on how to do this?
 
 
I tried it once before when I was still running winXP, it was a gingantic pain in the *** and I couldn't get the internet connection sharing to work.

---

### Post by ambient007 on 2010-04-24
bump, anyone?

---

### Post by tom.swartz07 on 2010-04-24
I could only think of a way to create a wireless to wired ad-hoc network. I do it all the time for my Xbox 360. :P

ALTHOUGH! if you did have 2 ethernet ports on your computer, you could do the same thing- just have one in and one out.
If its a desktop, definitely stop by your local computer shop and pick up an ethernet card (PCI or something of the sort) they just plug in and cost a heck of a lot less than a router. youre looking at somewhere around $5 if you install it yourself.

Ill post the guide for internet connection sharing, you just have to substitute the wireless in for the ethernet in in your case. [http://linuxers.org/howto/how-share-internet-with-other-computers-linux](http://linuxers.org/howto/how-share-internet-with-other-computers-linux)

---

### Post by ambient007 on 2010-04-24
> **tom.swartz07 said:**
> I could only think of a way to create a wireless to wired ad-hoc network. I do it all the time for my Xbox 360. :P

ALTHOUGH! if you did have 2 ethernet ports on your computer, you could do the same thing- just have one in and one out.
If its a desktop, definitely stop by your local computer shop and pick up an ethernet card (PCI or something of the sort) they just plug in and cost a heck of a lot less than a router. youre looking at somewhere around $5 if you install it yourself.

Ill post the guide for internet connection sharing, you just have to substitute the wireless in for the ethernet in in your case. [http://linuxers.org/howto/how-share-internet-with-other-computers-linux](http://linuxers.org/howto/how-share-internet-with-other-computers-linux)


Cool thanks a lot for that, it's a laptop so no-go with the ethernet card.

That looks like a really good link, I'll hopefully be able to figure it out using that. (I'm still wrapping my head around Ubuntu).

---

### Post by ambient007 on 2010-04-24
So I got:

daniel@daniel-laptop:~$ sudo apt-get install dhcp3-server
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Suggested packages:
  dhcp3-server-ldap
The following NEW packages will be installed:
  dhcp3-server
0 upgraded, 1 newly installed, 0 to remove and 3 not upgraded.
Need to get 373kB of archives.
After this operation, 872kB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) karmic-updates/main dhcp3-server 3.1.2-1ubuntu7.1 [373kB]
Fetched 373kB in 4s (75.1kB/s)       
Preconfiguring packages ...
Selecting previously deselected package dhcp3-server.
(Reading database ... 141934 files and directories currently installed.)
Unpacking dhcp3-server (from .../dhcp3-server_3.1.2-1ubuntu7.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for ureadahead ...
ureadahead will be reprofiled on next reboot
Setting up dhcp3-server (3.1.2-1ubuntu7.1) ...
Generating /etc/default/dhcp3-server...
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]
invoke-rc.d: initscript dhcp3-server, action "start" failed.


Failed? that's not right is it?

---

### Post by ambient007 on 2010-04-24
So tried to continue with the setup as the link describes, ignoring that 'fail' message because I don't know what it means.

Of course it doesn't work. The other computer seems to connected to the wlan but cannot get an internet connection. 

At the end I tried to run: [I]sudo /etc/init.d/dhcp3-server restart
As that was an instruction.

It gave:  * Stopping DHCP server dhcpd3                                           [fail] 
 * Starting DHCP server dhcpd3                                                   * check syslog for diagnostics.
                                                                         [fail]



:confused:
[/I]

---

### Post by 3rdalbum on 2010-04-24
You actually don't need Firestarter to accomplish this; Network Manager can do it much easier than that HOWTO states.

Left-click the Network Manager applet and choose "Create New Wireless Network". Choose a name for your network and the security method and password. When you connect to your modem via Ethernet, it should all Just Work; if not then go into Edit Connections and check that the IPv4 Settings for the wireless connection is listed as "Method: Shared With Other Computers".

I speak with at least some authority as I have created an ad-hoc wireless network in this way.

---

### Post by ambient007 on 2010-04-24
Well I got 



to work. Looks like I messed up a seting in firestarted.

How ever the other computer (WinXP) can see the network and connect but cannot get onto the internet.

Will I need to specify an IP on that machine?

Also it often loses the network "obtaining network address" or something (just a guess, that computer is in Japanese).

---

### Post by ambient007 on 2010-04-24
> **3rdalbum said:**
> You actually don't need Firestarter to accomplish this; Network Manager can do it much easier than that HOWTO states.

Left-click the Network Manager applet and choose "Create New Wireless Network". Choose a name for your network and the security method and password. When you connect to your modem via Ethernet, it should all Just Work; if not then go into Edit Connections and check that the IPv4 Settings for the wireless connection is listed as "Method: Shared With Other Computers".

I speak with at least some authority as I have created an ad-hoc wireless network in this way.


hmmm thanks, now I've gotta figure out how to undo what I've done and start again.


Thanks alot though.

---

### Post by cap10Ibraim on 2010-04-24
> **3rdalbum said:**
> You actually don't need Firestarter to accomplish this; Network Manager can do it much easier than that HOWTO states.
Yes it's very easy but the internet is not shared 
for windows 7 I use the great program connectifyme

---

### Post by ambient007 on 2010-04-24
Just can't seem to get the receiving computer to connect to the internet when it's on the network. And when it IS on the network, it often drops it. 

damn.

---

