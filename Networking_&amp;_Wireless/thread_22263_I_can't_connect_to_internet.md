---
title: "I can't connect to internet"
date: 2005-03-26
forum: Networking &amp; Wireless
---

### Post by lord_taran on 2005-03-26
Hi!
I use Ubuntu Hoary. I have a cablemodem and a ethernet card (DHCP). I never had problems with that but today, after I have updated the system, I can't connect.

---

### Post by zarathustra on 2005-03-26
Did you try changing kernel? I tried using one from the unofficial repositories, and it seemed to lose my wireless device, so reverted to an official release and it was all right.

---

### Post by Burgundavia on 2005-03-26
Try sudo dhclient eth0
if you get an error about a missing semi-colon, do this:

'
request subnet-mask, broadcast-address, time-offset, routers,
	domain-name, domain-name-servers, host-name,
	netbios-name-servers, netbios-scope, interface-mtu;
'

On the last line, there should be a comma between netbios-scope and interface-mtu. If there isn't add one. This will solve your issues.

Corey

---

### Post by arctic on 2005-03-26
you are not the only one. several persons have posted that their network didn't function after an update. all of them have updated the dhcp-client, which is faulty. there is a simple fix for this.
type in a terminal

sudo gedit /etc/dhcp3/dhclient.conf

go to line 21. there will be an entry saying

netbios-name-servers, net-scope interface-mtu;

now simply add a comma between the last two entries, so that you get

netbios-name-servers, net-scope, interface-mtu;

now save, exit and run sudo ifup eth0. it should work then.

edit: damn... i was 30 seconds too late. :lol:

---

### Post by oobuntoo on 2005-03-26
I'm having the same problem. Adding comma doesn't fix my problem. Is there anything else that could have caused this?

---

### Post by fracan on 2005-03-26
Long time reader/searcher, first time poster.

Thanks for the help, it worked like a charm for me!  The Ubuntu community is awesome!

Edit:  Huh, I guess I have posted once before.  Must've forgot.

---

### Post by oobuntoo on 2005-03-27
Is it normal to get message like this when I did "sudo dhclient eth0" ?


Internet Systems Consortium DHCP Client V3.0.1
Copyright 2004 Internet Systems Consortium.
All rights reserved.
For info, please visit [http://www.isc.org/products/DHCP](http://www.isc.org/products/DHCP)

sit0: unknown hardware address type 776
sit0: unknown hardware address type 776
Listening on LPF/eth0/00:50:8d:e9:2c:c4
Sending on   LPF/eth0/00:50:8d:e9:2c:c4
Sending on   Socket/fallback
DHCPREQUEST on eth0 to 255.255.255.255 port 67
send_packet: Message too long
DHCPREQUEST on eth0 to 255.255.255.255 port 67
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 7
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 18
send_packet: Message too long
DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 20
send_packet: Message too long
No DHCPOFFERS received.
Trying recorded lease 192.168.2.33
Usage: ping [-LRUbdfnqrvVaA] [-c count] [-i interval] [-w deadline]
            [-p pattern] [-s packetsize] [-t ttl] [-I interface or address]
            [-M mtu discovery hint] [-S sndbuf]
            [ -T timestamp option ] [ -Q tos ] [hop1 ...] destination
No working leases in persistent database - sleeping.

---

### Post by TravisNewman on 2005-03-27
Please watch where you post.

---

### Post by lord_taran on 2005-03-27
Hi to all!
Thank you for your answers, it worked! And sorry for the bad place, i had four or five tabs and I thought that i've posted in hoary->network, sorry :(

---

### Post by areku on 2005-03-27
Hi, i use warty...   and i do all you post here and nothing... i type gedit /etc/dhcp3/dhclient.conf but my in line 21 is: 
 netbios-name-servers, net-scope; 
without interface-mtu;


i don't know how to fix it...

help me pls... :S


thx.

---

### Post by fracan on 2005-03-27
Don't apologize -- the mod should move the thread to the correct place, not scold you and then move along like his job's done.

---

### Post by areku on 2005-03-27
someone want help me??

---

### Post by ibs on 2005-03-29
I am having the same problem as areku. There is no interface-mtu in my dhclient.conf file. I had recently upgraded to Hoary via Synaptic.

---

### Post by arctic on 2005-03-29
[QUOTE=areku]Hi, i use warty...   and i do all you post here and nothing... i type gedit /etc/dhcp3/dhclient.conf but my in line 21 is: 
 netbios-name-servers, net-scope; 
without interface-mtu;


i don't know how to fix it...

help me pls... :S


thx.[/QUOTE]
 as you are using warty, i guess your problem is not really the dhclient.conf, but the infamous ipv6 problem. take a look here. maybe it works for you.
[http://www.ubuntuforums.org/showthread.php?p=22132#post22132](http://www.ubuntuforums.org/showthread.php?p=22132#post22132)

---

### Post by learning_bird on 2005-03-30
Hi to all.

This is my first post. Two weeks have passed using Ubuntu Hoary Preview and I'm well impressed with Ubuntu : last Gnome 2.10, good design ( for a Linux distro, I'm spoiled since I'm a Mac OS X user ), debian reliability and apt-get and Synaptic ( I'm becoming lazy with Synaptic, I don't even want to do ./configure make && make install anymore ) and good harware recognition as it is the first Linux distro that autoconfigured the Intel wireless chipset on my Centrino Laptop...it was as easy as with my iBook. The only downside is making multimedia to work : no way untill now to make mplayer or VLC to play decently QuickTime or WindowsMedia files.

But that's not the scope of this post. I'm having a similar problem as those showed on this thread. Yesterday I reinstalled Ubuntu with the March 28th daily Hoary Preview and things went very well. Surfing the internet was no problem. Later I added a lot of repositories to the sources list in order to download Java, libdvdcss flash and mplayer plugins and all that stuff so I could try again to configure Multimedia. 

When I reloaded Synaptic to refresh the database with the new repositories it broke my Internet connection, which affected also the iBook on his side. which also lost connection. The problem persisted today and it was only  fixed by commenting all of the non Ubuntu official repositories and turning off and on the adsl modem to regain internet connection. I've never seen such thing in my life!

I then went through a fastidious proccess of uncommenting the non official repos ono by one and then refreshing Synaptic eachtime and Synaptic only broke internet on a small number of them, including curiouly the debian repos us.debian.org and non-us.debian.org.

Can someone shed some light on what could have happened? BTW, as in areku's case I also don't have any reference to interface-mtu on my /etc/dhcp3/dhclient.conf file.

Thanks to all.

---

### Post by arctic on 2005-03-30
[QUOTE=learning_bird]Hi to all.

This is my first post. Two weeks have passed using Ubuntu Hoary Preview and I'm well impressed with Ubuntu : last Gnome 2.10, good design ( for a Linux distro, I'm spoiled since I'm a Mac OS X user ), debian reliability and apt-get and Synaptic ( I'm becoming lazy with Synaptic, I don't even want to do ./configure make && make install anymore ) and good harware recognition as it is the first Linux distro that autoconfigured the Intel wireless chipset on my Centrino Laptop...it was as easy as with my iBook. The only downside is making multimedia to work : no way untill now to make mplayer or VLC to play decently QuickTime or WindowsMedia files.[/quote]
have you read the howto for multimedia in the hoary section of this forum? there is a lot on vlc, mplayer etc.
> But that's not the scope of this post. I'm having a similar problem as those showed on this thread. Yesterday I reinstalled Ubuntu with the March 28th daily Hoary Preview and things went very well. Surfing the internet was no problem. Later I added a lot of repositories to the sources list in order to download Java, libdvdcss flash and mplayer plugins and all that stuff so I could try again to configure Multimedia. 

When I reloaded Synaptic to refresh the database with the new repositories it broke my Internet connection, which affected also the iBook on his side. which also lost connection. The problem persisted today and it was only  fixed by commenting all of the non Ubuntu official repositories and turning off and on the adsl modem to regain internet connection. I've never seen such thing in my life!

I then went through a fastidious proccess of uncommenting the non official repos ono by one and then refreshing Synaptic eachtime and Synaptic only broke internet on a small number of them, including curiouly the debian repos us.debian.org and non-us.debian.org.

Can someone shed some light on what could have happened? BTW, as in areku's case I also don't have any reference to interface-mtu on my /etc/dhcp3/dhclient.conf file.

Thanks to all.
i have never experienced nor heard something like that. have you mixed your system repositories with debian and ubuntu mirrors? if this is the case, maybe it is a collision from sorting data when trying to connect to the mirrors, sending partially identical data to your box and your network subsequently into a block hole...

---

### Post by learning_bird on 2005-03-30
Thanks arctic for your answer.

About multimedia I've made what's on the how-to, downloaded the mplayer 586, docs , fonts and mozilla-mplayer packages and didn't installed the VLC mozilla plugin that in the previous Ubuntu install didn't worked and colided with the mplayer plugin. Mplayer can play mov files that one has to download, the streamings like those on Apple's QuickTime trailers site usually play but not until the end, they suffer the 99% problem, don't have sound  neither controls and mov files embeded on flash there's no way. VLC don't even starts to play the streamings. Curiously, on Mac OS X, VLC is an excellent app, that has served me many times.

I'll try later to install wine  and use the Windows apps to do the job. Any good faqs or how-to's about wine on ubuntu?

On to the Synaptic problem. As I said I've never seen such thing also. That mixing of debian and ubuntu repos could cause any kind of collisions inside the ubuntu structure, that I can understand but affecting also the iBook...?! Anyway ubuntu is debian it shouldn't be so confusing.

Would it be wise to follow the answer to the wiki FAQ "Can I use both Ubuntu and Debian packages together?" ( [http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-15.7453904394](http://www.ubuntulinux.org/support/documentation/faq/helpcenterfaq.2004-09-15.7453904394) ) ?

---

### Post by bakotaco on 2005-04-03
Adding the comma after in the dhclient.conf solves an older dhcp3-client bug.

The newer bug which causes the "**send_packet: Message too long**" related errors is caused by some dhcp server (for example many adsl/cable modems) which can't return mtu information. You should remove "interface-mtu" from the list of requests that dhclient issues in dhclient.conf.

Also see ubuntu bug 8241 ([https://bugzilla.ubuntu.com/show_bug.cgi?id=8241](https://bugzilla.ubuntu.com/show_bug.cgi?id=8241)) for more information.

Bas Ko

---

