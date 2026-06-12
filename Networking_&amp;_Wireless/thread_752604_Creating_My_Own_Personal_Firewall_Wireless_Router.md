---
title: "Creating My Own Personal Firewall/ Wireless Router"
date: 2008-04-11
forum: Networking &amp; Wireless
---

### Post by Justinisme on 2008-04-11
I am trying to find an OS that Serves as a firewall and "wireless router" with DHCP
Just getting sick of my POS d-link crappin out every 45 minutes. i have updated the firmware, and nothing helped.

I do download alot, so i was hoping to make use of some spare parts i have lying around.

If anyone can help here are the Things i have in my possession to use, yet again money is Very limited, and just to be able to pull it off would be cool

an Old DELL 1ghz tower, with 256mb ram, and a 30g HD
A Belkin Wireless G Desktop Card model - F5D7000v7

and 2 RealTek NIC's

here is what i would like to do

Internet (Modem)
           |
           |
           |
           |
Dell Server(In Place of D-link Router, using the Wireless Card, i would like my wireless machines to connect to it.
           |
           |
16 Port Router (connect to each PC.

If anyone knows of an OS i could do this with that supports my config, please let me know

if you need anymore info also let me know.
THANKS TO ALL IN ADVANCE

---

### Post by superprash2003 on 2008-04-11
ubuntu server 7.10 or ubuntu desktop 7.10 .. you will need to enable internet connection sharing - [http://wiki.steenbe.nl/?p=29#more-29](http://wiki.steenbe.nl/?p=29#more-29)

---

### Post by Justinisme on 2008-04-13
will that let me reconfigure the wireless NIC to be used as a "AP"?

---

### Post by superprash2003 on 2008-04-13
well with a wireless card you can connect only one pc to it.so yes one pc can get internet access wirelessly..the others can get internet through your 16port router

---

### Post by Justinisme on 2008-04-13
i followed the website that you had showed, it does now serve DHCP addresses, but i can not get the internet from it. i have checked and double checked the settings on the page and done additional research but cant find anything, i also decided to not use it as a wireless AP, i wud rather put it from like this

MODEM
|
|
UBUNTU PC
|
|
16 port
|
|
my pcs and d-link) use the 16 port for my pcs, and the dlink for everyone elses wireless, as long as my internet dont go out, idc bout anyone else in the house, as long as they can ****try to get on**** lol


i am using Ubuntu 7.10 server

thanks

---

### Post by superprash2003 on 2008-04-14
go to the command prompt or terminal of the pcs that are connected to the 16 port router.. and type ping google.com and post results here.. it could just be  a DNS problem

---

### Post by kevdog on 2008-04-14
I applaud your efforts, however you might want to look into the dd-wrt project, where this has already been done before and offers more features than what you could believe.  Of course it requires you have a certain router type in that its not compatible with all routers.  Its really useful, and secure since its been evolving now for a couple of years.
[http://www.dd-wrt.com/dd-wrtv3/](http://www.dd-wrt.com/dd-wrtv3/)

---

### Post by Justinisme on 2008-04-14
The Results Of The Ping were

"Unknown Host google.com"

so i do believe that it is DNS related, 

and as for Kevdog, i looked into the DD-WRT and i do not have a router that is compatible with it, and although that might be a quicker fix, i do really want to get this going with part i already have, thanks for the idea tho

---

### Post by superprash2003 on 2008-04-14
what OS are the clients running? if linux, follow this to setup DNS [http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html](http://prash-babu.blogspot.com/2008/04/how-to-configure-dns-servers-in-linux.html)

---

### Post by Justinisme on 2008-04-14
I am running Ubuntu 7.10 Server, and on the Client Slackware 12. 

I did follow that tutorial on the DNS servers, and did input the DNS ips into my dhcpd.conf, but still no internet,

Any and all help is very necessary,

---

### Post by superprash2003 on 2008-04-14
then there could be something wrong with the ICS part.which adapter is connected to the internet and which is connected to the router?(eth0 or eth1 etc etc)

---

### Post by Justinisme on 2008-04-14
Thanks all, i was using Ubuntu, but found a much more user friendly Firewall, and it is preconfigured from the get go....

PFsense

Uses FreeBSD 6.2 system with OpenBSD's PF filter rules.

Very Secure Very Stable, and VERY VERY VERY VERY straight forward.

Thanks to all that posted.

to check out PFsense for yourself, Click [PF Sense]("http://www.pfsense.org")

thanks

---

