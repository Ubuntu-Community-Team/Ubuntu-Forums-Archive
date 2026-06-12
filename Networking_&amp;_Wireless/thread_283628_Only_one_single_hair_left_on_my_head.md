---
title: "Only one single hair left on my head"
date: 2006-10-24
forum: Networking &amp; Wireless
---

### Post by hairshirt on 2006-10-24
Hello one and all,

I don't post very often here as I'm often able to find the help I need from this wonderful forum and the spiffing people that dewl within it.  However, I can't get my head around the problem I'm having with the web server I'm attempting to setup.  The attached diagram will hopefull explain all.  As always, I would be thankful of any help offered.

Many thanks.

---

### Post by metalheart on 2006-10-24
I personally would connect modem to router, server and some heavily network using PCs also to the router and use hub for other connections.

---

### Post by mips on 2006-10-24
=D>=D>=D>=D>=D>

Well I give you 10/10 for the diagram. A bit more explanation might be a good thing.

I will look at this tomorrow and see if I could assist, bed time 4 me now...

---

### Post by hairshirt on 2006-10-25
Thank you for taking the trouble to reply MIPS, I thought I'd explained the situation quite well in my diagram, however, I will attempt to explain a little further.

Of course I know what metalheart was talking about and if I had an 8 port route I may very well have considered the option.  I would like if possible to stick with me plan as outlined within the diagram.

The route I would web traffic to and from the server is marked in red.

I have an account with with DynDNS.com
(****.homelinux.com)

Setup host as: server1.****.homelinux.com (have also tried just: ****.homelinux.com both have thus far been to no avail.)
I have already been here: [http://www.howtoforge.com/perfect_setup_ubuntu_6.06](http://www.howtoforge.com/perfect_setup_ubuntu_6.06) & here: [http://www.ubuntuforums.org/showthread.php?t=223805&highlight=setup+web+server](http://www.ubuntuforums.org/showthread.php?t=223805&highlight=setup+web+server)

My ISP leaves Port 80 Open

As common, my ISP dishes-out access via DHCP

I'm pretty sure I have to setup a dummy NIC card on the server so that I can assign to it the ip address provided to me by DynDNS and then, somehow, link the DHCP connection on Eth0 to that IP address.  Don't know how to do it though.  In Suse it seems pretty straight forward but the overall installation is not as good (IMO) as Ubuntu.

I would be glad of any help, thanks again.

---

### Post by Buffalo Soldier on 2006-10-25
> **mips said:**
> =D>=D>=D>=D>=D>

Well I give you 10/10 for the diagram.

Only if every question in here is accompanied with a super diagram like this :)

---

### Post by hairshirt on 2006-10-25
Ta very much

---

### Post by hairshirt on 2006-10-25
Hello, Hello... Any help out there? ](*,)

---

### Post by hairshirt on 2006-10-25
Is there anyone out there who can help me get this server up and running this side of Christmas?

---

### Post by mips on 2006-10-25
Apologies, I had hassles of my own to sort out this morning.

I assume your ISP is assigning you multiple public IPs via DHCP ?

Have you had a look at:
[http://ubuntuguide.org/wiki/Dapper#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service](http://ubuntuguide.org/wiki/Dapper#How_to_assign_Hostname_to_local_machine_with_dynamic_IP_using_free_DynDNS_service)
[http://www.ubuntuforums.org/showthread.php?t=128175](http://www.ubuntuforums.org/showthread.php?t=128175)
[http://www.ubuntuforums.org/showthread.php?t=283745](http://www.ubuntuforums.org/showthread.php?t=283745)
[http://www.ubuntuforums.org/search.php?searchid=9134656](http://www.ubuntuforums.org/search.php?searchid=9134656)

Another option would be to:
Modem->Router->Hub

This way you can hang everything off the router and hub in the 192.168.1.0 network.

---

### Post by hairshirt on 2006-10-25
I did think of doing that but I sofar have my mind set on doing it the way as setout on my diagram.  I can't understand how or why it's proving so difficult doing it this way.

---

### Post by tturrisi on 2006-10-25
The only thing I see that is a problem is the network design.
I would:
1. connect cable modem to router wan port.
2. connect 2 servers & 1 pc workstation (most used) to router
3. connect hub to router uplink port
4. connect 2 printers & 1 pc (least used) to hub
5. use router port forwarding to forward port 80 and other necessary ports such as 21 to lamp server
6. use router port forwarding to forward the SMTP & POP ports to mail server.
7. if have room on the hub, plug the ap into it & if not, get a switch w/ more ports instead of a hub.

That done, there will be no problems as all lan systems will be able to use printers & access the servers via their respective client applications.

generally, I prefer switches over hubs because they are:
1. more secure
2. faster

---

### Post by mips on 2006-10-25
Did you have a look at those links, especially the 1st one ?

---

### Post by tturrisi on 2006-10-25
additional:
1. most linksys routers have built in support for dynamicdds so no need for a dyndds client running on the lamp server.

2. it would also be just as easy to omit the dedicated mail server & setup mail handling on the lamp server.

---

### Post by hairshirt on 2006-10-26
Thanks guy... You've really been a great help.  On reflection, I will rethink the layout of the network despite the fact that I still think it a good layout.  I did consider tturrisi's suggestion some time ago so I think I'll go back to that idea.  Mips, many thanks for the links... I have to say that I've been to all those places before...  Do you know, I curse the day I bought that G4.  I just wish I had the guts to sling-it

Thanks again chaps, Mark.

---

### Post by mips on 2006-10-26
> **hairshirt said:**
> Do you know, I curse the day I bought that G4.  I just wish I had the guts to sling-it


Put it in a box and fedex/dhl it to me, I've never played with a Mac before :mrgreen: 

Seriously, just run the mail stuff on the other server.

---

### Post by tturrisi on 2006-10-26
What elae I would do:
I would setup that G4 as a dedicated firewall box for the server.  Stick it inbetween the server & the router.  Why?  Because your isp allows port 80 & your router is going to get hammered with port scans that will inform kiddies of open ports on the network.  I would run a thin client on the G4, a firewall linux boot cd.  Configs save to a floppy.  It would be interesting & fune to get working.  And imho is better than just using iptables on the server cause if mess up iptables then cannot use the server period.

---

### Post by hairshirt on 2006-10-27
Thanks again both you guys.  Thats a very interesting suggestion, tturrisi.  I hadn't given that any thought.  What do you mean by: "thin client"?  Would a ppc install of ubuntu be the best for this role?

I love Ubuntu apart from the silly name and the default installed desktop.  Moreover, I love this forum.  Thanks again chaps.

---

### Post by tturrisi on 2006-10-27
> **hairshirt said:**
> Thanks again both you guys.  Thats a very interesting suggestion, tturrisi.  I hadn't given that any thought.  What do you mean by: "thin client"?  Would a ppc install of ubuntu be the best for this role?
[http://www.webopedia.com/TERM/T/thin_client.html](http://www.webopedia.com/TERM/T/thin_client.html)
[i]thin kl&#299;´&nt) In client/server applications, a client designed to be especially small so that the bulk of the data processing occurs on the server.

Although the term thin client usually refers to software, it is increasingly used for computers, such as network computers and Net PCs, that are designed to serve as the clients for client/server architectures. A thin client is a network computer without a hard disk drive, whereas a fat client includes a disk drive.[/i]

There are bootable "live" linux distros that consist solely of the stripped down bare essential operating system along with scripts to control iptables.  Some of these can be configured via a browser on another comp & some must manually edit iptables.  They "run" in a RAM Drive much like "live Ubuntu".  No HD is necessary, but if have one the configs made can be saved to it or a floppy, so the defaults & modified can be restored at reboot of the live cd.

examples:
[http://www.livecdlist.com/?pick=All&showonly=Firewall&sort=&sm=1](http://www.livecdlist.com/?pick=All&showonly=Firewall&sort=&sm=1) 
[http://www.wifi.com.ar/english/cdrouter.html](http://www.wifi.com.ar/english/cdrouter.html) (wIRED or Wifi)

---

