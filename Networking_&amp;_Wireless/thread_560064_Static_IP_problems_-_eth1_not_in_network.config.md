---
title: "Static IP problems - eth1 not in network.config"
date: 2007-09-25
forum: Networking &amp; Wireless
---

### Post by holdie on 2007-09-25
so I'm trying to set up my static IP with our router, and I've got my network-manager configured to connect as one.  However, when I check my router, it says that my computer is logged in as one of the DHCP spots, and it would appear that my computer is actually DHCP-ing into the router even though I've told it to use static...

I've checked the /etc/network/interfaces file and everything *except* eth1 (the one I'm using) is there.  I was wondering if there's maybe some other configuration file I haven't found yet that has the eth1 information and which is telling my computer to use DHCP...

any ideas?
thanks

---

### Post by SpiritIsReality on 2007-09-26
howdy
my /etc/network/interfaces
@p3:~$ cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.***.***
netmask 255.255.255.0
gateway 192.168.***.***

your auto eth1and the rest should be listed in this file like the eth0 above is.
only your addresses will be different, most likely.
the gateway is the ip of the router.
then you could reboot and see if you're on.
or sudo /etc/init.d/networking restart
or sudo ifdown eth1 and then
sudo ifup eth1
I'm not sure
man ifup
see /etc/network/interfaces here
[http://aboutdebian.com/network.htm](http://aboutdebian.com/network.htm)
there's lots out there
[http://www.google.ca/search?hl=en&q=linux+networking&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+networking&btnG=Google+Search&meta=)
please post back here if you have any further trouble, so we can hopefully get some help from
somebody and get you mobile. haha! (static, mobile, surfing)

trails

---

### Post by holdie on 2007-09-26
yeah, that's what I'm saying though, when I look at the interfaces config file, I've got entries of eth0, eth2, and such, but it skips eth1...seeing as how I'm using eth1 to connect, I figure the configuration for it has to be somewhere and I'm trying to figure out where...otherwise, could I just configure eth0 to be static and start using that one?

oh, and by the way, if memory serves I tried simply inserting an eth1 entry into the file and, for lack of a better phrase, it made my computer quite unhappy...(I had to boot in safemode and take out the eth1 entry and it started working fine again)

---

### Post by kyphi on 2007-09-26
You can do all the configuring necessary in System -> Administration -> Networking.

The default gateway is eth0 and DHCP is fine.  Make sure that there is a tick next to 'Enable this connection' and leave the other fields on that screen blank.

Under General, you have to enter your domain name (name@isp.net).
Under DNS you need to add the servers DNS code (111.111.1.111)
Under search domains put the name of your ISP (ISP.net).

Does that help?

---

### Post by SpiritIsReality on 2007-09-26
howdy
kyphi ...thanks. hope that works

holdie ...I'm curious
could you please post 
ifconfig -a
cat /etc/network/interfaces
lspci
dmesg | grep eth
netstat -r


discovering hardware from outside the box. found this...
[http://www.google.ca/search?hl=en&q=linux+ethernet+lspci+dmesg+grep&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+ethernet+lspci+dmesg+grep&btnG=Google+Search&meta=)
[http://jbakshi.50webs.com/Linux_tutorial/Hardware_detection/Hardware_Detection.html](http://jbakshi.50webs.com/Linux_tutorial/Hardware_detection/Hardware_Detection.html)
multiple cards on one machine, found this
[http://learnlinux.tsf.org.za/courses/build/net-admin/net-admin-all.html](http://learnlinux.tsf.org.za/courses/build/net-admin/net-admin-all.html)
[http://learnlinux.tsf.org.za/courses/build/net-admin/ch01s08.html](http://learnlinux.tsf.org.za/courses/build/net-admin/ch01s08.html)

trails

---

### Post by holdie on 2007-09-26
so after some further looking I discovered two things

A. my interfaces file actually *did* have the eth1 entry, it was just waaay down the screen after a big blank entry...

B. after rearranging the text file, I rebooted my network, and upon connecting again my ip was static...if this doesn't hold up then I'll check back, but it would appear that for now the problem is fixed.

---

### Post by SpiritIsReality on 2007-09-26
howdy
sounds good

trails

---

### Post by holdie on 2007-09-27
well, unfortunately as is not well that ends well apparently...

my static IP is good for a while, but when I restart my computer it boots up and uses DHCP to connect to our router via eth1 (the one that is defined as static in interfaces)...if I manually go in, put auto eth1 before the iface stuff, then reboot init.d, then reconnect wireless, I've got a static IP address...however, as soon as I reboot the computer or whatever it immediately goes back to DHCP and auto eth1 is shifted to the bottom of the interfaces text file...

are there ghosts in my computer or am I doing something wrong here?

---

### Post by SpiritIsReality on 2007-09-27
howdy
good question.
I think we have to do some searching for how the /etc/network/interfaces is getting overwritten.
man and google to the rescue I hope.

trails

---

### Post by SpiritIsReality on 2007-09-27
>  cat /etc/network/interfaces
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

> ~$ man 5 interfaces
NAME
       /etc/network/interfaces  - network interface configuration for ifup and
       ifdown

DESCRIPTION
       /etc/network/interfaces contains network interface configuration infor&#8208;
       mation  for the ifup(8 ) and ifdown(8 ) commands.  This is where you con&#8208;
       figure how your system is connected to the network.

       Lines starting with &#8216;#&#8217; are ignored. Note that end-of-line comments are
       NOT supported, comments must be on a line of their own.
if I was me I'd keep the 

# The loopback network interface
auto lo
iface lo inet loopback
address 127.0.0.1
netmask 255.0.0.0

auto eth0
iface eth0 inet static
address 192.168.*.***
netmask 255.255.255.0
gateway 192.168.*.*

and comment out all the others until such time as I figured I needed one, then uncomment them.

#auto eth1
#iface eth1 inet dhcp whatever

System > Admin > Network
and set things up for eth0
then
```
sudo /etc/init.d/networking restart
```

trails

---

### Post by SpiritIsReality on 2007-09-27
reconnect wireless......my bad
I think you're supposed to use wlan0 for that.
[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)
trails

---

### Post by holdie on 2007-09-27
yeah, since I'm not using a wired connection, I just commented out everything except for eth1 and restarted init.d, this seems (once again) to have fixed the problem...I'll just uncomment eth0 if I need to use wired again

---

### Post by SpiritIsReality on 2007-09-28
ok
so you can use eth1 for wireless.
that's interesting....

just for the heck of it have a look at this with nic cards.
some guys are havin' a rough ride.
[http://ubuntuforums.org/showthread.php?t=538448](http://ubuntuforums.org/showthread.php?t=538448)
[http://gentoo-wiki.com/HARDWARE_RTL8168](http://gentoo-wiki.com/HARDWARE_RTL8168)

trails

---

### Post by holdie on 2007-10-04
alright so this is getting frustrating, it's connecting with DHCP again, so I figure I'll put in my interfaces file

```
auto lo
iface lo inet loopback


iface eth0 inet static
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1


iface eth1 inet static
wireless-essid ______
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1


#auto eth2
#iface eth2 inet dhcp

#auto ath0
#iface ath0 inet dhcp

auto wlan0
iface wlan0 inet static
wireless-essid ______
address 192.168.1.2
netmask 255.255.255.0
gateway 192.168.1.1




auto eth1
```

any ideas as to why I'm using DHCP here?

---

### Post by SpiritIsReality on 2007-10-04
howdy
If anybody knows the answer just shout.
OK 
What I've been looking at lately are these two links.
Ubuntu Server Guide
[https://help.ubuntu.com/7.04/server/C/](https://help.ubuntu.com/7.04/server/C/)
and ch. 25 at Rute
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz) about right here [http://rute.2038bug.com/node28.html.gz#SECTION002840000000000000000](http://rute.2038bug.com/node28.html.gz#SECTION002840000000000000000)
I found that when it talks about the /etc/network/options file, it's deprecated in debian and now
the file /etc/sysctl.conf is used. 
you could see noob12 comment here [http://ubuntuforums.org/showthread.php?t=563315](http://ubuntuforums.org/showthread.php?t=563315) something in the configuration. In that case it may be in the dhcp3.conf .
I hope the answer is posted here. Until then, I'm looking for an answer too.
It's in the configuration files and the startup scripts that run those configuration files somewhere ,
reckon ?
buds

ps. if you could post how you make the scroll window I'd appreciate it. you could make a how to, post a link or ?

---

### Post by holdie on 2007-10-05
well i haven't solved the problem yet, but if you look at the top of the text box where you're typing your message, there's a number symbol...that's the symbol for "code" so if you highlight the text then press that, it will appear as a code box in the post

---

### Post by holdie on 2007-10-05
by the way, I've found that when my computer boots, it automatically uses the DHCP address, however if I use the init.d restart, then it will start using static.  I went to admin-sessions-startup processes to see if dhclient was there or something, but it's not...any ideas?

---

### Post by SpiritIsReality on 2007-10-06
howdy
holdie ...[http://ubuntuforums.org/showthread.php?p=3485355#post3485355](http://ubuntuforums.org/showthread.php?p=3485355#post3485355)
buds

I suggest that you post a new thread about the current problem.
buds

---

### Post by bapoumba on 2007-10-08
I have the same kind of issue. This happens when switching from DHCP to static IP on the same device. 
the best I have found is:
```
sudo pkill dhclient 
```
after restarting the network with a static IP.

---

### Post by SpiritIsReality on 2007-10-08
> **bapoumba said:**
> I have the same kind of issue. This happens when switching from DHCP to static IP on the same device. 
the best I have found is:
```
sudo pkill dhclient 
```after restarting the network with a static IP.thankyou !!!

---

