---
title: "network problem on ubuntu 7.04"
date: 2007-04-22
forum: Networking &amp; Wireless
---

### Post by Piviul on 2007-04-22
I've already post this thread to Installation & Upgrades but none answered me. Please someoe can try to help me?

I've upgraded my ubuntu edgy to feisty and I have encontoured no problems except I can't reach internet any more... I can ping a site but I can't browse it with Firefox, I can ping my pop mail address but thunderbird can't get my messages, I can ping the ubuntu repository sites but aptitude can't use them, I can ping my adsl router but I can't reach the web interface from firefox... It's a very strange case and I can't understand where the problem is... 

The network seems have no problems because another PC on the same network have no problems and before this upgrade all was working  properly...

Perhaps some more information can be usefull.

I have no iptables rule:
> 
antonella@antonella-desktop:~$ sudo iptables -L
Password:
Chain INPUT (policy ACCEPT)
target prot opt source destination

Chain FORWARD (policy ACCEPT)
target prot opt source destination

Chain OUTPUT (policy ACCEPT)
target prot opt source destination



This is my routing table
> 
antonella@antonella-desktop:~$ sudo route
Kernel IP routeing table
Destination Gateway Genmask Flags Metric Ref Use Iface
192.168.30.0 * 255.255.255.0 U 0 0 0 eth0
link-local * 255.255.0.0 U 1000 0 0 eth0
default 192.168.30.1 0.0.0.0 UG 0 0 0 eth0


When I try to update my system from the shell prompt I can see
> 
antonella@antonella-desktop:~$ sudo aptitude update
0% [Accesso in corso]

but never more happens. I have to type Ctrl-C to break the command.

This is my sources.list
> 
antonella@antonella-desktop:~$ cat /etc/apt/sources.list | grep ^deb
deb [ftp://na.mirror.garr.it/mirrors/ubuntu-archive/](ftp://na.mirror.garr.it/mirrors/ubuntu-archive/) feisty main restricted multiverse universe
deb [ftp://na.mirror.garr.it/mirrors/ubuntu-archive/](ftp://na.mirror.garr.it/mirrors/ubuntu-archive/) feisty-updates main restricted multiverse universe
deb [ftp://na.mirror.garr.it/mirrors/ubuntu-archive/](ftp://na.mirror.garr.it/mirrors/ubuntu-archive/) feisty-security main restricted multiverse universe


So I've tried to connet via ftp to the repository:
> 
antonella@antonella-desktop:~$ ftp na.mirror.garr.it
Connected to na.mirror.garr.it.
220 ProFTPD 1.2.10 Server (Debian) [193.206.140.37]
Name (na.mirror.garr.it:antonella): anonymous
331 Anonymous login ok, send your complete email address as your password.
Password:
230-Welcome, archive user [email]anonymous@host231-30.pool8250.interbusiness.it[/email] !
230-

and no more messages are displayed and I have to press Ctrl-C...

Then I've changed the repository and I've selected the other italian one in http and I have tried to download Release.gpg
> 
antonella@antonella-desktop:~$ wget [http://ubuntu.fastbull.org/ubuntu/dists/feisty/Release.gpg](http://ubuntu.fastbull.org/ubuntu/dists/feisty/Release.gpg)
--19:05:01--  [http://ubuntu.fastbull.org/ubuntu/dists/feisty/Release.gpg](http://ubuntu.fastbull.org/ubuntu/dists/feisty/Release.gpg)
           => `Release.gpg'
Risoluzione di ubuntu.fastbull.org in corso... 194.116.84.5
Connessione a ubuntu.fastbull.org|194.116.84.5:80... connesso.
HTTP richiesta inviata, aspetto la risposta...

and I had to press Ctrl-C once more...

Please help me I have no internet any more and I have to use my brother winzoz pc to connect to the internet...

Piviul

---

### Post by Piviul on 2007-04-22
I've found the issue: if I change router my new feisty has no network problems... but the the router has no problem too because only feisty can't browse the internet using this router: windows can and edgy too is able using this router.

Someone can help me to solve feisty  incompatibility with this router? The router is a "base sagem f@st 3001". Perhaps it's a IPV6 incompatibility? Someone know how can I disable IPV6 on feisty?

Thank you very much.

Piviul

---

### Post by G4HZA on 2007-04-22
This article will give you some insight into the likely reason why.

http:// articles.techrepublic.com.com/5100-1035_11-6174075.html

Roger

---

### Post by Piviul on 2007-04-23
Roger, you are a genious!!! Now I can browsr the internet with feisty too.

Thank you very, very, very and very much!!!!

Piviul

---

### Post by leemind on 2007-05-09
I'll second that! Following that link solved my exact same problems, which I thought were never going to be sorted, since they were soooo weird (I could get google, but not much else) =D> =D> Thankyou!

---

### Post by skisky on 2007-07-29
your THE MAN dude...

---

### Post by RetroDan on 2008-04-17
I am having this exact same problem. Everything seems to work fine. Ping, etc. but for some reason FireFox will not DNS. I can however plug in a numerical ip address no problem.

Unfortunately the link listed in the above post that points to the solution is a dead link.

Can someone please help. Thank you.

---

### Post by evenstranger on 2008-04-28
RetroDan, There is a space at the start of the link try this one instead :

[http://articles.techrepublic.com.com/5100-1035_11-6174075.html](http://articles.techrepublic.com.com/5100-1035_11-6174075.html)

I have a similar problem with a hardy heron install, it will ping and connect to local machines but can't browse the internet or access the apt repositories. Have tried the setting in the above link but didn't help.

---

