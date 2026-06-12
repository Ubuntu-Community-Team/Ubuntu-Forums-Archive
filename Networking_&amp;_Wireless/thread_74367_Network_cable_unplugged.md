---
title: "Network cable unplugged?"
date: 2005-10-11
forum: Networking &amp; Wireless
---

### Post by coolcehb on 2005-10-11
I have two PCs connected to each other with a network cable. One laptop with just Windows XP on it, and one desktop computer on which i dual boot Ubuntu and Windows ME. When i'm in ME i can browse through the laptop's shared files, and vice versa, but when i'm in Ubuntu, the laptop with Windows XP just says "A network cable is unplugged".

I have enabled eth0 from System-->Administration-->Network (which almost took two minutes!), and installed Samba using "sudo dpkg -i samba.<something>", which was successfull, because samba now shows as installed in Synaptic. Is there something I have forgotten to do (or done wrong)?

I also have internet connection on the Laptop, using a PCMCIA card, but i can't get the USB Wireless network adapter (listed as "Acer (??) WarpLink 802.11b Adapter" in lsusb) to work in Ubuntu, so i can't do any apt-get installs...

Any help will be appreciated.

---

### Post by garretjax on 2005-10-11
There are a couple things more you need to do.
In order to 'see' each other on the network, both computers must have ip addresses set to be in the same range - ie 192.196.1.* also the cable must be a cross over cable in order for them to access each other.
under linux to set ip address command is ifconfig eth0 192.196.1.<1-255> 
under windows you can do it from network properties on tcp/ip protocol.

Hope this helps
G

---

### Post by mlomker on 2005-10-11
> "A network cable is unplugged".

As garretjax mentioned, you'll need to acquire a crossover cable.  It's possible that the Windows driver is capable of doing the crossover function in software but the Ubuntu driver will not.

> I also have internet connection on the Laptop, using a PCMCIA card, but i can't get the USB Wireless network adapter (listed as "Acer (??) WarpLink 802.11b Adapter" in lsusb) to work in Ubuntu, so i can't do any apt-get installs...


Have you [installed ndiswrapper]("http://www.ubuntuforums.org/showthread.php?t=25683") and loaded the Windows driver?

---

### Post by coolcehb on 2005-10-12
Thanks alot for good responses!

My Ubuntu now has the IP 192.196.1.1, where I am able to ping myself. I configured the Laptop to have the ip 192.196.1.2, but Windows still says that a Network cable is unplugged so i was unable to test the ping there (It just said "Response from 83.108.160.0: The destination network cannot be reached". How the heck does it get response from 83.108.160.0 when i ping 192.196.1.2?

It probably has something to do with that I'm not using a crossover cable. But i'm a totally newb :confused: What is a crossover cable? A just have a "normal network cable" going directly from the first computer's network card to the other's. Why should there be a problem with that?

---

### Post by coolcehb on 2005-10-12
And another noob question is it bad to have an ipadress that ends with 0?:
[QUOTE=garretjax]ifconfig eth0 192.196.1.<1-255>[/QUOTE]

---

### Post by mlomker on 2005-10-12
> How the heck does it get response from 83.108.160.0 when i ping 192.196.1.2?

A very good question unless you have Internet connection sharing configured.  It shouldn't work if the cable is disconnected (you probably have a green status light or two on the network cards to verify connectivity as well).

> Why should there be a problem with that?

Normally computers connect to a hub or switch and not directly to another computer.  A crossover cable flips the pinout of the cable at one end of the connector so that the transmit wire plugs into the other card's receive pin.  You could also go to your local computer store and buy a hub or switch.  A small switch should be $40 or less.

---

### Post by coolcehb on 2005-10-12
Aha, i see, the ping utility actually tried to ping 192.196.1.2 on the internet. But Windows is able to use a non-crossover cable. Are you sure there is no Linux program that can use that?

---

### Post by garretjax on 2005-10-22
Noth that i know of. If you are using a switch in between the two computers, or a hub, most are intelligant enough to do the crossing for you.  But to connect two computers directly you pretty much WILL need a cross-over cable.  Depending on the length, I know i can usually get one here for about $14.00 (CAD) -- Just make sure it is cross over.  This is another place that windows has adapted to allow any user to network, where linux still requires that you know a bit about what your doing.  Not that thats a bad thing, both have benifits, i just find i learn more the hard way, thats one of the reasons i use linux.

As for some of your other questions, i don't recall exactly but i think ip's have to be between 1 - 255  - where (again, i am trying to remember something from a class months back) the 192 and 196 ranges are reserved for home network type uses. most commonly you see IPs in the form of 192.168.1.<1-255> of 196.168.<1-255>.<1-255>  but most of this is only convention. The key thing is that all computers on your network have to be in the same range [first 3 parts of the IP must be the same]. how you arrange after that is purely arbitrary. 


I really don't know why your ping is getting a response from that 83 ip. Are you connected to the interent with this box at the time you are pinging ?


hope some of this helps if you are  still having problems.

GJ

---

