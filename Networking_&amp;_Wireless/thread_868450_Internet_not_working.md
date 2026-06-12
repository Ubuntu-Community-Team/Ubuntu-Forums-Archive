---
title: "Internet not working"
date: 2008-07-23
forum: Networking &amp; Wireless
---

### Post by Walter Melon on 2008-07-23
I recently put Ubuntu on my desktop and it installed without a problem and I changed the home address on Firefox to google.  google opens up and every time I search anything it works fine, but whenever I try to go anywhere else it doesn't work.  It just keeps loading.  :confused:

Thanks in advance

---

### Post by superprash2003 on 2008-07-24
could be a DNS problem, try changing DNS servers to opendns. their ips are 208.67.222.222 and 208.67.220.220

---

### Post by Karyn on 2008-07-24
I seem to have the same problem. The only thing Firefox can load is pages from google. I tried using the IPs from OpenDNS, but then not even google loaded.

I can log in on MSN with Pidgin and ping all IPs I've tried, though.

---

### Post by Walter Melon on 2008-07-28
Changing the dns servers didn't work.  I thought something went wrong on the install, but I tried to use the internet when I was running the live cd and it was the same problem.  And it's not my router because I took the ethernet cable and put it directly from my modem to my computer.  Any more ideas?  Thanks for the help

---

### Post by Walter Melon on 2008-07-31
bump

---

### Post by drwest on 2008-07-31
I have this same problem.  Installed ubuntu hardy heron.. fired up firefox... google loads... I can search - and I get results... but the pages won't load... updates won't run either.

I turned off ipv6
- no change
I added domain name servers 208.67.222.222, 208.67.220.220
- no change
I looked at the other xp machines on my network, used the DNS listed on those boxes
- no change
I have tried reinstalling ubuntu
- no change

Any ideas?

Thanks in advance.

---

### Post by Walter Melon on 2008-07-31
Sorry man, but I still have the same problem. I think we need some help from someone who is an expert at networking on Ubuntu.

---

### Post by drwest on 2008-07-31
I found the solution that worked for me!

Here is what I did.

Logged into my router.  Changed "MTU" to "Manual".  Changed 1500 to 1492.  Rebooted my computer.

I found the info here:
[http://ubuntuforums.org/showpost.php?p=4514356&postcount=12](http://ubuntuforums.org/showpost.php?p=4514356&postcount=12)

Good luck!

---

### Post by Karyn on 2008-08-01
> **drwest said:**
> I found the solution that worked for me!

Here is what I did.

Logged into my router.  Changed "MTU" to "Manual".  Changed 1500 to 1492.  Rebooted my computer.

I found the info here:
[http://ubuntuforums.org/showpost.php?p=4514356&postcount=12](http://ubuntuforums.org/showpost.php?p=4514356&postcount=12)

Good luck!

Since I don't have a router, this might not be what I'm looking for. But I'll give it a try anyway.

EDIT: Appearently *something, somewhere* is set to 1500, since pmtu is 1500 when I do tracepath in the terminal. I put in "mtu 1492" in my interfaces file. But pmtu is still 1500. I guess that's because I can't change it globally...

---

### Post by rrrockmanx on 2008-08-01
Unfortunately, I'm experiencing the same problem, and changing MTU didn't work either.

First of all, all the Firefox preloaded bookmarks, web pages with URL starting with [http://en-us.www](http://en-us.www)... , are perfectly working.
All other pages and everything is NOT.

Ping functions for every host, but not for my DNS servers. It functions for my router IP, but the router config page won't show up in Firefox when going to its IP.
Connection is ok with both DHCP and static IP configurations, and I configured my router in both PPPoA and PPPoE mode, but had same problems.
I have a US Robotics Sureconnect, and a wired at it.

I also tried disabling iPV6 from Firefox, and system-wide (but in this case, I don't know if I made things right).

I'm in Italy and use Tiscali provider, but I hope this doesn't matter. For you to know, however, had this same problems with all linuxes except an old version of Gentoo.

One friend of mine told me it must have to do with the network daemon Ubuntu uses, which gives problems with my poor router.

If you could tell me more about the way Ubuntu manages networking, and eventually a way to replace and/or tweak the network daemon/connection manager, I could try to hack a little bit more before declaring I need to change OS or router...

---

### Post by drwest on 2008-08-03
I don't know if this helps or not... but I did find that after running the bittorrent program in ubuntu (and getting AWESOME speeds)... it screwed something up and I am now right back where I was when I first posted earlier!  Argh!

I think my next steps are to reinstall and try to go through the steps that were successful previously... and then stay away from downloading torrents using the program in ubuntu.

---

### Post by Walter Melon on 2008-08-03
I don't have an option to change the MTU on my router.  My desktop is on a wired connection to my router.  I only use the wireless router for my laptop (on which Ubuntu and networking work fine).  I thought it was the router so I connected it directly from my cable modem, but that didn't work.  

And as for the program for torrents, I use Azureus (vuze).  hasn't given me a problem yet.  although it might take a little while to get used to it

---

### Post by Walter Melon on 2008-08-05
bump

---

### Post by drwest on 2008-08-07
Walter - what is the nic card you are using?  I am using an onboard nic sis190.  Since we both have the same problem I am curious if we also have the same ethernet card.

---

### Post by Karyn on 2008-08-08
I also have a SiS 190 (integrated). Maybe that could be it? Though I read here ([http://geeksofdoom.com/2007/04/23/shuttle-ss21t-as-a-web-server-on-a-budget/](http://geeksofdoom.com/2007/04/23/shuttle-ss21t-as-a-web-server-on-a-budget/)) that internet worked right away when installing Fedora on the same barebone PC I have.

---

### Post by drwest on 2008-08-08
I also have barebone (shuttle) pc... here is where I am at now.

After (re)install of ubuntu I launch firefox and it hangs with the progress bar at 50%.

I have ethernet cable going from sis190 ethernet card to linksys router.

I can ping google.com, ubuntu.com, the router, and other pc's on my network succesfully.

My router shows my ubuntu pc in the dhcp routing tables.

I have configured network manager to dhcp, edited /etc/dhcp3/dhclient.conf to read:

prepend domain-name-servers 192.168.1.1, 208.67.220.220, 208.67.222.222;

on router, set MTU to "manual" and 1491

edited /etc/network/interfaces to read:

auto lo
iface lo inet loopback

auto eth0
iface eth0 inet dhcp
pre-up/sbin/ifconfig $IFACE mtu 1491

ifconfig shows that I have an ipaddress and am using MTU 1491,  no tx errors but a lot of rx errors.

I tried:

modprobe sis190

and nothing happened.

lspci -nn 

shows ISA bridge ... SiS966... 1039:0966

uname -r

shows linux kernel 2.6.24-19-generic

dmesg | grep 00:04.0

shows no ISA bridge errors

I am now out of ideas.  Help?  Any experts out there?

---

### Post by drwest on 2008-08-09
bump

---

### Post by drwest on 2008-08-09
bump

---

### Post by Karyn on 2008-08-12
My internet is working!! And the solution was really stupid, but not something I would have thought of. I just turned off the computer, unplugged the power cable, plugged it in again (after a couple of minutes) and then turned on the computer and booted into Ubuntu.

I found the solution in this thread: [http://ubuntuforums.org/showthread.php?t=878388&page=3&highlight=sis190](http://ubuntuforums.org/showthread.php?t=878388&page=3&highlight=sis190), the first post on the page.

I hope this will work for you too!

---

### Post by drwest on 2008-08-12
I did the same thing last night and mine is working too!

---

### Post by Walter Melon on 2008-08-29
Sorry I took so long to respond drwest. To answer your question, yes I have the same ethernet card as you - sis190.  This method worked for me too, but it is a temporary fix.  After I used windows and started ubuntu, the same problem was there.  We've figured out the problem, so the question is now - how do I reinitialize the network card?

---

### Post by kissg1988 on 2008-10-01
Hi there,

I also have a SiS190 NIC on my system and experienced some strange issues with it, using the latest driver. I saw randomly dropped frames, which were originating from hosts on my local network. The bug only affected local traffic, I didn't have any problems with internet-related stuffs.

Yesterday I decided to drop away the latest driver, take the original one (which is available on the official site of SiS), and patch it to make it compatible with recent kernel versions. After some searching on Google, I managed to compile it for the latest kernel version. 

Please check this driver, maybe it will solve your problems, too.
There's a readme file in the package, don't forget to read it before compiling.

Best regards
George

---

