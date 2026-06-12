---
title: "basic networking questions - host &amp; domain names"
date: 2008-02-23
forum: Networking &amp; Wireless
---

### Post by bluepowder7 on 2008-02-23
just got a few VERY BASIC questions about home networks that frankly i don't know the answer to and just don't understand how they work.

within the context of my home network (LAN), what exactly is a host name and what is a domain name?  can one exist without the other (or with the other being blank)?

where do i check what my current host and domain names are, and where do i change them?  do i make a change on each PC and network printer, or on the router, or both?

do "name service" relate to a home network?  stuff like DNS, NIS, LDAP, etc.


i'm (still) trying to set up one of my computers as a file and print server (i have 2 printers, a new color inkjet that's already networked, and an older HP laser that's on a parallel port so it has to be hooked up to a PC), so i guess i need to know how the host names and domain names interact so that i can move files between PC's and whatnot.  up until now, i've just used each computer independently, so i never learned these fundamentals.


.

---

### Post by nixscripter on 2008-02-24
Hello.

Here is my opinion on your questions, speaking as someone who has set up many networks, but is by no means an expert (others should feel free to correct me).

> **bluepowder7 said:**
> 
within the context of my home network (LAN), what exactly is a host name and what is a domain name?  can one exist without the other (or with the other being blank)?

A hostname is what the computer calls itself, and tells anyone who asks what it is. Generally, all computers have a hostname. A domain name is what the network you belong to calls itself, and that is used for routing purposes. For home networking, you don't need one. IP addresses work fine for finding things if a router is properly configured.

> **bluepowder7 said:**
> 
where do i check what my current host and domain names are, and where do i change them?  do i make a change on each PC and network printer, or on the router, or both?


In Ubuntu, you can check your host name by opening a terminal and using the command: ```
uname -n
``` and you can set it with: ```
sudo hostname 'my-new-name'
```

> **bluepowder7 said:**
> 
do "name service" relate to a home network?  stuff like DNS, NIS, LDAP, etc.


Usually, that stuff is handled by your ISP. Your router asks for DNS servers (where other hostnames outside your network, like google.com, get looked up) and just tells your computers what they are when they connect to it. Again, you don't have to worry about that if everything is done properly.

> **bluepowder7 said:**
> 
i'm (still) trying to set up one of my computers as a file and print server (i have 2 printers, a new color inkjet that's already networked, and an older HP laser that's on a parallel port so it has to be hooked up to a PC), so i guess i need to know how the host names and domain names interact so that i can move files between PC's and whatnot.  up until now, i've just used each computer independently, so i never learned these fundamentals.
.

You don't need to worry about domain names in this case. As for host names, they are just for human convenience. I suspect that you may have to use IP addresses anyway, because unless you do some serious configuration, the computers won't ask each other for their host names, and the router that connects them won't keep track.

All of this is very general. If you would be more specific about particular computers, situations, programs, and networking topology (i.e. what's connected to what), I might be able to give you a more specific answer.

Hope this helps.

---

### Post by Iowan on 2008-02-24
Besides **uname -n**,  you can also learn the hostname with **hostname**.  
Although not the same thing, occasionally **workgroup** replaces **domain** - (primarily on Samba-based systems). You *_can_* set up your network so you can ping/connect by hostname rather than IP address (either local DNS, **hosts** file, or (maybe) WINS).

---

### Post by ruy_lopez on 2008-02-24
adding names/addresses to each system's "/etc/hosts" usually suffices. You don't have mess around with the hostname command. If you can't be bothered keeping the /etc/host files in sync, install dnsmasq on one system and use that system as a DNS server for the other hosts.

You can put any name you want in /etc/hosts. /etc/host maps a names to an address. The address is used for the connection, not the hostname.

---

### Post by bluepowder7 on 2008-02-24
ok, hostname i now understand.  found the field for it too while trying to set my wireless laptop for static IP (System - Admin - Network - General tab).  cool!  so, my laptop's host name is apparently "greg-laptop" which is simple enough.  i did also notice a field there for a domain name, which was blank.

you mentioned workgroup in the windows world.  hmm, i do remember that.  those workgroup names were set on each PC, and if i recall right they all had to match so that computer1 could share files and stuff with computer2.  would i need to just pick a domain name and enter it at each computer?

so, the router doesn't need to know anything, right?  there's no host names or domain names (workgroup names) stored anywhere in the router?

my topology is like this:

* DSL modem connects to Linksys WRT54G router
* wireless laptop (Ubuntu 7.10, static IP) with host="greg-laptop" and domain=blank
* desktop PC (win2k, winxp, Ubuntu 7.10, all static IP, wired), haven't set the host or domain/workgroup yet, but will probably call it host="greg-desktop" in all 3 OSes
* file/print server that i'm trying to get running (having issues with installing and booting) that's gonna run 7.10 Server hopefully, and i'll need to share files between it and the desktop & laptop, and let the other PCs print to the laser printer that's connected to this server's parallel port
* inkjet printer that has a network interface, static IP, wired, all PCs need to print to it

so, all those are just hooked up to the Linksys router.  3 wired, 1 wireless

up until i got the bright idea to set up a file/print server, those PCs just shared the internet connection and inkjet printer (which i don't think cared about host names or domain / workgroup names).  then i ran out of hard drive space, and decided i need a central storage spot, hence the server and all my questions about what this stuff actually is.  (amazing i got this far without knowing those)


.

---

