---
title: "[help] ubuntu: configuring ics on it"
date: 2007-11-26
forum: Networking &amp; Wireless
---

### Post by Mdakait on 2007-11-26
as topic explains i m setting up ics - ' internet connection sharing' between ubuntu n windows vista//xp now i followed this link
[http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

now when i wrote this first
' apt-get install dnsmasq ipmasq '
it gave me this syntax
'root@mdakaitpc:/home/mdakait# apt-get install dnsmasq ipmasq
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Couldn't find package dnsmasq"

then again i tired and got this

'root@mdakaitpc:/home/mdakait# apt-get install dnsmasq ipmasq
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?'

help please ... am in urgent need to set it up !!

p.s i checked other similar thread but they all were having different errors

regards
mdakait

---

### Post by ZipoTe on 2007-11-26
> 'root@mdakaitpc:/home/mdakait# apt-get install dnsmasq ipmasq
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

This is because you're probably running "synaptic" at the time you "apt-get"

and the other error is obvious, the packet doesn't exist :wink:

**EDIT:** In my debian i can download the packet so, i don't know why you can't

---

### Post by Mdakait on 2007-11-27
that problem solved i used update manager and downloadd all updates and tired again and it workd .. bt now the problem is ... i m not a expert bt my 2nd eth card is disabled it says
this " eth0:avahi" on network monitor .. it has not ips no nuthin .. only macid .. where can i enable it .. ??

thanks for answers i really appricate it .. u dun knw how many forums i been thru to get the answer .. :) ..

---

### Post by dragon_788 on 2007-12-29
the issue is that you were root, but the database got locked when you were trying to use it. When you open and close update manager it also locks the database, If you don't use sudo or root it won't unlock it, and once you unlocked it with Update Manager you were verified as able to use it. ;)

---

