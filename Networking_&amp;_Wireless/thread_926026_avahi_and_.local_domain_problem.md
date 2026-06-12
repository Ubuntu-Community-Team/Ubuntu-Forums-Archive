---
title: "avahi and .local domain problem"
date: 2008-09-21
forum: Networking &amp; Wireless
---

### Post by ghaster on 2008-09-21
Hello,

Im trying to setup avahi-daemon & netatalk to work on my linux server withouth success.


(The reason for all this effort is for my apple macbook to be able to make backups to the server using time machine in Leopard)


While I've been following this [[COLOR="Red"]guide[/COLOR]]("http://holyarmy.org/2008/01/24/time-machine-backup-to-linux-via-netatalk"), I've found out that I have an active "unicast .local domain" running. 

Syslog gives me this message: 
starting Avahi mDNS/DNS-SD Daemon: avahi-daemon* avahi-daemon disabled because there is a unicast .local domain

I've read the thread [[COLOR="Red"]Avahi unicast .local domain[/COLOR]]("http://ubuntuforums.org/showthread.php?t=425379&highlight=unicast+.local"), among alot others, but not being able to solve the problem with these means.

Tried that router trix (since I've got an d-link 624+) without better luck.

[COLOR="DarkOrchid"]So now I'm trying to find out how to disable/remove the "unicast .local domain" function..[/COLOR]

Hoping for someone who could help me with this, what configfiles are there to be modified etc...

//ghast

---

### Post by nickeh on 2009-06-13
Same here set the domain in the router but no change. 
Avahi is still complaining.

EDIT: Solved it by changing to OpenDNS [http://www.opendns.com]("http://www.opendns.com/")
My ISP had a unicast at .local so that explains why changing the router didn't work

---

### Post by GlenMH on 2009-11-10
I have 2 machines: 1 a Dell laptop running the desktop version of 9.10 and putting the domain in to the router has fixed that machine.

I also have an Acer Aspire One netbook running 9.10 UNR and putting the domain in the router has not fixed that....

---

