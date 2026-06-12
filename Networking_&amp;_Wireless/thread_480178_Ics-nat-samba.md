---
title: "Ics-nat-samba"
date: 2007-06-21
forum: Networking &amp; Wireless
---

### Post by StGeorge on 2007-06-21
I originally posted this in April and have not spent too much time using Ubuntu as my wife needs me to be in Winblows to access the internet for her work.
This posting had many views but no answers, so it seems this is a common problem.
It is a shame as my reason for installing Ubuntu is cos I am sick and tired of Microsoft and Software designed for Winblows constantly thinking that people out there have nothing better to do than spend their lives dipping into their pockets or spending vast amounts of time upgrading.
I have Ubuntu 6.06 installed on the beginning of my D: 120GB drive whilst my Windows 98SE is installed on my C: Drive which is only 10GB.
I really would like to start working with Ububtu and leave Windows.
Below is the Posting I put up in April:


I am running Windows 98SE on my desktop and use ICS (Internet Connection Sharing) for a Newlink 5 way Ethernet Supply to different rooms. This desktop now also has Ubuntu 6.06 as well. I do not want wireless connection. I do not want an internet hub. I simply want to allow laptops to access the internet through the existing desktop.
The other laptops do not have Ubuntu or Linux installed. They are running XP or Vista at the moment.
Could anyone tell me how to use Ubuntu to allow these OS's to access the internet.
I have allowed NAT or ICS on FireStarter but this does not solve the problem.
I am not bothered about file sharing but if this must be done to make it easier then so be it.
Any suggestions would be welcome.

---

### Post by spd106 on 2007-06-21
I think this wiki page is very informative about connection sharing.
[https://help.ubuntu.com/community/Router](https://help.ubuntu.com/community/Router)

Sadly it doesn't cover dhcp and dns yet, though you should be able to install and configure dnsmasq without too much difficulty. The /etc/dnsmasq.conf file is far more user friendly than most config files. You might also find this high level article to be too.
[http://www.enterprisenetworkingplanet.com/netos/article.php/3377351](http://www.enterprisenetworkingplanet.com/netos/article.php/3377351)
There are probably a million others like this one on google, but it covers most of the basics.

---

### Post by StGeorge on 2007-06-21
Thanks anyway but no good.
I installed dnsmasq but I cannot edit the config file though Root Terminal or Terminal as Permission is denied.
Firestarter cannot start Firewall.
I have lost my internet connection.
I am now back in windows where I will stay, probably until there is a window interface designed for this common problem.
Basically half a day wasted again.
I tried all suggestions back in April, another half a day wasted.
Firestarter says that eth1 not ready.
Firestarter does not configure Internet Connection Sharing either.
Nothing Works.
Maybe a future Ubuntu release will solve this problem.

---

### Post by SqRt7744 on 2007-06-22
sudo apt-get remove dnsmasq

.... this should at least get you your internet connection back!  Do you have any friends who use linux?

---

### Post by StGeorge on 2007-06-23
After Shutting Down and Re Starting my internet came back.
Problem is I do not wish to mess with it much more as there seems to be many ways to to get this internet connection sharing going.
Maybe I have too many conflicts now.
Firestarter cannot start the Firewall.
I am not sure about iptables.
I am not sure about dnsmasq.
Will post when I have a solution.
Any ideas would be welcome though.

---

