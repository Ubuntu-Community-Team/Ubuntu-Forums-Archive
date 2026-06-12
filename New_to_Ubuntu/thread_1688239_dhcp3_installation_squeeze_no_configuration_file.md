---
title: "dhcp3 installation squeeze no configuration file"
date: 2011-02-15
forum: New to Ubuntu
---

### Post by tendydon on 2011-02-15
I am trying to installed a dhcp server in my system(Debian squeeze) in 64bit machine DELL server T110 
I have installed a dhcpd server in the system using [FONT=Verdana]
[/FONT]
# apt-get install dhcp3-server

It is installed in the system but I cannot find the configuration file
 **/etc/dhcp3/dhcpd3.conf **there is no  dhcpd3 directory.
Similarly I couldnot find the init script **/etc/init.d/dhcpd3-server** too.
also I couldnot find binary file** dhcpd3**

I have uninstalled and reinstalled using following command but no luck

apt-get --purge remove dhcp3-server 
apt-get install dhcp3-server
It gives the messege
dhcp3-server is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded

I will be grateful to you guys if you could help me out.

---

### Post by 1ll3xc on 2011-02-15
Hello Tendydon,

The correct files with paths should be the following.

Configuration:
/etc/dhcp3/dhcpd.conf

Init-script:
/etc/init.d/dhcp3-server

Executable file:
/usr/sbin/dhcpd3

Cheers!

---

### Post by tendydon on 2011-02-16
**1ll3xc** thanks a lot for you suggestion :)
But there is no /etc/dhcp3/ directory and /etc/init.d/dhcp3-server script either.
Finally I found that 
the configuration file  in /etc/dhcp/dhcpd.conf 
also /etc/default/isc-dhcp-server to configure the interfaces .
Actually the service was isc-dhcp-server in debian squeeze instead of dhcp3

Cheers !!

---

### Post by bookscholar on 2012-10-09
Because its not named dhcp3 its just named dhcp

---

### Post by overdrank on 2012-10-09
[IMG]http://img147.imageshack.us/img147/5451/necromancing.jpg[/IMG]
From the _[Ubuntu Forums Code of Conduct]("http://ubuntuforums.org/index.php?page=policy")_.
> If a post is older than a year or so and hasn't had a new reply in that time, instead of replying to it, create a new thread. In the software world, a lot can change in a very short time, and doing things this way makes it more likely that you will find the best information. You may link to the original discussion in the new thread if you think it may be helpful.
Thread closed.

---

