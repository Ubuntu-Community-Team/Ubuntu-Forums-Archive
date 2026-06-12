---
title: "Please help I can't connect to Internet"
date: 2008-08-22
forum: Networking &amp; Wireless
---

### Post by danthemanvsq on 2008-08-22
I'm new to linux but I'm an experienced computer user.  Here are the specs to my machine:
Compaq Presario SR2150NX
Celeron 3.46GHz
1.50 GB Ram
NVidia GeForce 8500GT
Realtek RTL8139/810x Built in NIC
Att DSL connected to a buffalo WHR-G54S router

I Can't connect to anything, I get no ping from my DNS numbers.  Here are the trouble shooting steps I've tried so far:
- sudo gedit /etc/modprobe.d/blacklist
code blacklist 8139cp
- sudo gedit /boot/grub/menu.lst
 added line of code "pnpbios=off pnpacpi=off" & " noacpi pnpacpi=off"
- gksu gedit /etc/network/interfaces
added code "iface eth0 inet dhcp"

Nothing works and I'm about to pull out my hair.  I can connect when I boot to Vista but I can't get anything from Ubuntu and I also tried to by pass my router and go strait to the dsl modem. Please Please someone help.

---

### Post by sdide on 2008-08-22
ok.

Tell us how your computer is connected (cable/wireless)?

What is the inside network addresses (behind the router).
You can check that on the Vista installation by typing ipconfig in a cmd-shell - it will list ip-address and default gateway.

After that we can start debugging your linux networking.

---

### Post by alfie white on 2008-08-22
Rather than clutter up the place, I have a very similar problem.

I use static IP address's on my small network. The machine has a realtek ethernet card, the network is wired.

internal system info 
IP 192.6.8.1
subnet 255.255.255.0
Gateway 192.6.8.20.
(cable modem via router)

the install goes for DHCP, I used the network settings to change to static as above, verified in  text editor that the changed had been saved. I can see other machines (windows) on the network but can not access the internet. As You need access to the net to update the system etc I have uninstalled Ubuntu.  What do I need to do to ensure internet access to allow a proper install.

---

### Post by sdide on 2008-08-22
Hey, 
alfie white:
Those addresses sounds a bit ticky.
192.6.8.0/21 belongs to Hewlett Packard company.

A normal private network would be in the ranges 
192.168.0.0/16
10.0.0.0/8
172.16.0.0/12

That aside usually the gateway would be .1 
in your case 192.168.0.1 
and the ip-address, probably DHCP obtained, would be 192.168.0.20

the other way around is possible, but its not standard.

---

### Post by alfie white on 2008-08-22
> **sdide said:**
> Hey, 
alfie white:
Those addresses sounds a bit ticky.
192.6.8.0/21 belongs to Hewlett Packard company.

A normal private network would be in the ranges 
192.168.0.0/16
10.0.0.0/8
172.16.0.0/12

That aside usually the gateway would be .1 
in your case 192.168.0.1 
and the ip-address, probably DHCP obtained, would be 192.168.0.20

the other way around is possible, but its not standard.


It's internal address only, so they can be any number you decide on. The gateway is 192.6.8.20, and the machine is 192.6.8.1- and they have worked on other flavours of Linux, and do work internally on Ubuntu, I just can not get Ubuntu onto the internet. I thought I would give Ubuntu a try, as it is supposedly the most user friendly, and I want to have a play with the multimedia set up it offers.

---

### Post by sdide on 2008-08-22
> **alfie white said:**
> It's internal address only, so they can be any number you decide on. The gateway is 192.6.8.20, and the machine is 192.6.8.1- and they have worked on other flavours of Linux,  ... 

Indeed it works, unless ofcourse you want to reach a service which HP incidentially put at 192.6.8.0/24, because your router will route such a request back to you and it wont work. 
It might work, but its a really bad idea to use public address space on a local network. Why not use the address-space IANA reserved for it?

On the choice of gateway at .20 and address a .1 - thats fine if you are so 
inclined. (again tho - I do not see why, you want to break best practice)
 
Can you ping the gw (192.6.8.20) from the machine?
What is the content of the file 

/etc/resolv.conf

---

### Post by alfie white on 2008-08-22
> **sdide said:**
> Indeed it works, unless ofcourse you want to reach a service which HP incidentially put at 192.6.8.0/24, because your router will route such a request back to you and it wont work. 
It might work, but its a really bad idea to use public address space on a local network. Why not use the address-space IANA reserved for it?

On the choice of gateway at .20 and address a .1 - thats fine if you are so 
inclined. (again tho - I do not see why, you want to break best practice)
 
Can you ping the gw (192.6.8.20) from the machine?
What is the content of the file 

/etc/resolv.conf

The numbering system is to fit in with a company in france, I log onto their servers and printers, as they do mine. It is what it is, and has to stay that way. Best practice in this case seems to mean follow convention. I can ping any of the machines on the internal network, I just can not get onto the web. I can not tell you what the content of the file is, I have uninstalled Ubuntu. It appears that on install it decides you will be on a DHCP system, and looking through the various problems people are having, does not want to move away from that. I was trying to see if I had missed something obvious at the install stage, but it appears not. Thanks for the time and replies, but if I decide to have play with Linux any further I will return to Suse.

---

### Post by danthemanvsq on 2008-08-22
> **sdide said:**
> ok.

Tell us how your computer is connected (cable/wireless)?

What is the inside network addresses (behind the router).
You can check that on the Vista installation by typing ipconfig in a cmd-shell - it will list ip-address and default gateway.

After that we can start debugging your linux networking.

Ip address 192.168.11.2
gateway 192.168.11.1
subnet mask 255.255.255.0
dns 208.67.222.222 208.67.220.220
set up as static ip on vista so I could us utorrent. ports on router open for utorrent, xbox live & TVersity media server.

---

### Post by kinetek on 2008-08-22
Make sure that you have the proper DNS entries in the /etc/resolv.conf file.

This could be an actual address, or the IP of the router that provides the DHCP lease.

---

### Post by danthemanvsq on 2008-08-22
> **kinetek said:**
> Make sure that you have the proper DNS entries in the /etc/resolv.conf file.

This could be an actual address, or the IP of the router that provides the DHCP lease.

The DNS numbers are correct also I can't connect to anything not just the net.  I get no net traffic at all.  The only thing that will ping is my own ip.  can't ping gateway dns or webpage

---

### Post by danthemanvsq on 2008-08-22
Come on guys I know one of you out there knows how to trouble shoot  my network.

---

### Post by Golden Blunder on 2008-08-23
I could not get browser to connect to setup pages on router.Then for some unknown reason it just did .Try switching everything on off and reloading Ubuntu as I did nothing command wise.Strange stuff.

---

### Post by pfdevil on 2008-08-23
Just adding my 2 cents to the mix. Is your router DHCP enabled. The easiest way I found when struggling with the Wireless setup is to set the router to DHCP then allow Ubuntu to configure your wireless. Setting ip and all.
Then try to connect to your router. If successful enter the information gathered via the DHCP setup manually. Then disable the DHCP again. And continue from there.

---

### Post by danthemanvsq on 2008-08-23
I'm connected to my router via hard wire.  It works on the Vista boot, when I'm in Ubuntu I can't even connect when I'm pluged directly into my dsl modem.

---

### Post by Golden Blunder on 2008-08-23
I think I've already given you the best answer

---

### Post by danthemanvsq on 2008-08-23
**Problem Solved!!!** I pluged the dsl modem directly into the machine and noticed that the NIC light was off.  So I inspected the BIOS and found that compaq had a WOL power managemet enabled on the NIC so I disabled that & presto I'm online.  I have a feeling that WOL has something to do with Windows.  I hate microsoft a little more now.  Thank you folks for all your help it was greatly appreciated.
-Dan

---

### Post by Golden Blunder on 2008-08-23
Glad Your sorted out but its not windows fault more of a bios glitch as it should have detected it and I was pretty sure it wasnt Ubuntu related .Switching on the computer after the modem was switched on should make the bios auto detect if not faulty.Check for a M/B bios update.

---

