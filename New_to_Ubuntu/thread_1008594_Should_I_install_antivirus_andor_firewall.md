---
title: "Should I install antivirus and/or firewall?"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by jolly_grunt on 2008-12-11
I had recently installed Ubunto 8.10 but then made the switch to  Xubuntu. 

I've been using it just for web browsing (firefox with noscript), playing videos, music, burning dvd's, and playing some of the games that are widely available through synaptic.

I don't plan on printing from it, networking it with other pc's, sharing files, using it as a webserver, downloading torrents, using any email program or anything like that.

I have this computer sitting behind my routers firewall connected via ethernet.

having said that, do I need to install an AV program or software firewall?

---

### Post by howefield on 2008-12-11
I'd say you were safe enough, given you have a hardware firewall protecting you and your installation should be safe from virus attack, particularly given your "sober" usage habits.

---

### Post by Duck2006 on 2008-12-11
> I have this computer sitting behind my routers firewall connected via ethernet.

having said that, do I need to install an AV program or software firewall?

A fire wall is built in ubuntu so no to the fire wall.

[https://wiki.ubuntu.com/UbuntuFirewall](https://wiki.ubuntu.com/UbuntuFirewall)

As for AV software if you are E-mailling and passing them to a win system then you may want to have one.

[http://ubuntu-ky.ubuntuforums.org/showthread.php?t=765220](http://ubuntu-ky.ubuntuforums.org/showthread.php?t=765220)

[http://ubuntuforums.org/showthread.php?t=176753](http://ubuntuforums.org/showthread.php?t=176753)

---

### Post by carml on 2008-12-11
In my humble opinion ):Pif you plan not to use at all programs of P2P or other you don't need a firewall;an antivirus is not needed unless you share files with PC using OS Windows.

---

### Post by andrew.46 on 2008-12-11
Hi,

There is a great post on these forums that you should read that discusses many aspects of security under Ubuntu:

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

All the best.

  Andrew

---

### Post by rhcm123 on 2008-12-11
> **jolly_grunt said:**
> I had recently installed Ubunto 8.10 but then made the switch to  Xubuntu. 

I've been using it just for web browsing (firefox with noscript), playing videos, music, burning dvd's, and playing some of the games that are widely available through synaptic.

I don't plan on printing from it, networking it with other pc's, sharing files, using it as a webserver, downloading torrents, using any email program or anything like that.

I have this computer sitting behind my routers firewall connected via ethernet.

having said that, do I need to install an AV program or software firewall?


I found it hard to belive too, but linux can actually get virus's. Not as many as windows or macs, but yes, virus's. However, some of the more basic bash script virus's won't run on windows, and any good email service will prevent you from sending executables (such as gmail).

---

### Post by tuxxy on 2008-12-11
Only if your regularly sharing files with or accessing another Windows drive/partition.

---

### Post by cardinals_fan on 2008-12-11
Yes and no.  A firewall is worth having (see [this guide]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html")).  Antivirus apps are worthless on any platform.

---

### Post by jimmy the saint on 2008-12-11
Antivirus software is like banning nail-clippers at the airport. There may be a case where it would prevent some nut-job from taking the plane over (if the flight crew was really nervous about their manicure), but its pretty useless against the real threats.  Well written virii get past the software for a while because the software works based on a blacklist.  A virus must be caught, classified, and blacklisted in order to be detected and prevented.  We only know of the viruses that have been found, how many haven't been???

Like the TSA, antivirus software is a good measure to make you feel better, just don't rely on it to keep you safe.  After all, two foot steel knitting needles are perfectly allowed by the TSA and all the vista spyware is allowed by antivirus software!!

Enough ranting.  What they said.  If you are sharing with windows, install the software to cleanse your files.  AND DON"T VISIT/DOWNLOAD SHADY SITES/FILES!!

---

### Post by rhcm123 on 2008-12-12
> **tuxxy said:**
> Only if your regularly sharing files with or accessing another Windows drive/partition.

I am transferring files and i automount my windows partiton and have never had a problem. that said, i (by i, i mean my windows machines) are cowering behind 2 firewalls and only transfer openoffice files.

Life is sweet! :lolflag:

---

### Post by roshanjose on 2008-12-12
I personally dont think you need a firewall untiland unless you are in some file sharing mode or any other sever type.....

ubuntu has an inbuilt firewall that keeps away hackers / crackers....

---

### Post by cardinals_fan on 2008-12-13
> **roshanjose said:**
> 
ubuntu has an inbuilt firewall that keeps away hackers / crackers....
Only if enabled (see my link on page 1)

---

### Post by rhcm123 on 2008-12-15
> **cardinals_fan said:**
> Only if enabled (see my link on page 1)

vim? it's disabled by defualt.

---

### Post by cardinals_fan on 2008-12-15
> **rhcm123 said:**
> vim? it's disabled by defualt.
Eh?  Vim is an editor [**the** editor ;)], and has little to do with the firewall (iptables).

---

### Post by rhcm123 on 2008-12-16
> **cardinals_fan said:**
> Eh?  Vim is an editor [**the** editor ;)], and has little to do with the firewall (iptables).

sorry, i meant ufw. How did I get that and vim confused... i need some sleep... :lolflag:

---

### Post by handydan918 on 2008-12-16
> **rhcm123 said:**
> I found it hard to belive too, but linux can actually get virus's. Not as many as windows or macs, but yes, virus's. However, some of the more basic bash script virus's won't run on windows, and any good email service will prevent you from sending executables (such as gmail).

BS!

I think I called you on this once before. 


Did you ever find a link to the linux virus database?
No? 
That's because there aren't any. 
Well, none that work...
Faugh.

Better yet, never mind the link. Just send me the virus. You can PM me. I'll give you the URL of a drop.io account.

---

### Post by rhcm123 on 2008-12-16
> **handydan918 said:**
> BS!

I think I called you on this once before. 


Did you ever find a link to the linux virus database?
No? 
That's because there aren't any. 
Well, none that work...
Faugh.

Better yet, never mind the link. Just send me the virus. You can PM me. I'll give you the URL of a drop.io account.

The most common form of a linux virus or worm is an SSH bruteforce. Others include Bliss and Nuxbee. A virus can even be as simple as malicious code suggested here on the forums, such as a forkbomb.

I don't have virus's lying around, and I don't particularly want to send my little bag of tricks over to you. :) (I put on a white hat occasionally and test out various things on my dummy server)



ANTI-VIRUS SOFTWARE:

For striaght-up GNU linux:
[http://www.clamav.net/](http://www.clamav.net/)
This is a free anti-virus that works cross platform with windows.

For mac: 
[http://www.symantec.com/norton/macintosh/antivirus](http://www.symantec.com/norton/macintosh/antivirus)
It's not linux, it's "UNIX"... with a bash shell. It's close enough for government work. 


Also, might i suggest WIKIPEDIA?
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)
Unfortunatley, i fell into the trap too of beliving that linux is virus free. Wrong.

Everything gets virus's. Windows, however, because it is coded in C and controls 93% of all computer os's, is much more attacked, leading to the assumption that windows is inherently flawed. It isn't: it's just so scrutinized the tiniest holes are ripped wide open.

Linux isn't attacked because it has 1 or 2 % of the market. It also is the os of choice run by hackers, and they don't like to attack their brethren. Want to know a mac virus? It's called OS 10.5. Macs are imitation linux. Linux for people who don't want linux. :)

And so, i end this with the simple statement: Linux can and does get virus's. It just happens very rarely, and isn't as widespread as windows.

---

### Post by handydan918 on 2008-12-16
> **rhcm123 said:**
> The most common form of a linux virus or worm is an SSH bruteforce. Others include Bliss and Nuxbee. A virus can even be as simple as malicious code suggested here on the forums, such as a forkbomb.

I don't have virus's lying around, and I don't particularly want to send my little bag of tricks over to you. :) (I put on a white hat occasionally and test out various things on my dummy server)



ANTI-VIRUS SOFTWARE:

For striaght-up GNU linux:
[http://www.clamav.net/](http://www.clamav.net/)
This is a free anti-virus that works cross platform with windows.

For mac: 
[http://www.symantec.com/norton/macintosh/antivirus](http://www.symantec.com/norton/macintosh/antivirus)
It's not linux, it's "UNIX"... with a bash shell. It's close enough for government work. 


Also, might i suggest WIKIPEDIA?
[http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses](http://en.wikipedia.org/wiki/List_of_Linux_computer_viruses)
Unfortunatley, i fell into the trap too of beliving that linux is virus free. Wrong.

Everything gets virus's. Windows, however, because it is coded in C and controls 93% of all computer os's, is much more attacked, leading to the assumption that windows is inherently flawed. It isn't: it's just so scrutinized the tiniest holes are ripped wide open.

Linux isn't attacked because it has 1 or 2 % of the market. It also is the os of choice run by hackers, and they don't like to attack their brethren. Want to know a mac virus? It's called OS 10.5. Macs are imitation linux. Linux for people who don't want linux. :)

And so, i end this with the simple statement: Linux can and does get virus's. It just happens very rarely, and isn't as widespread as windows.

Yet more unsupported opinion. The most credibilty-destroying statement anyone could make;

> Linux isn't attacked because it has 1 or 2 % of the market.
Brilliant. According to netcraft, somewhere between 40 and 60% of webservers are running Linux. Why crack a desktop when you can pwn a server!?

Because you can't. 

Again.

If you want to put on the black hat, PM me and I'll send you my public IP addy. 

Let's see if you can get past a NAT router, first..


LULZZ!!!111oneoneone!!

Pfft...

---

### Post by chronographer on 2008-12-16
I heard that there are malicious applications (not necessarily viral) which are running on Linux web servers. As these are always on they make great hosts for the command and control centres of massive distributed bot nets (all running on windows boxes).

It seems obvious to me that there would be viruses (in terms of malicious software) which runs on Linux, it is just that none have taken off and that the separation of root and users makes it much harder to escalate programs ... Viruses are harder to write on Linux, but there are still viruses. Ditto OSX.

---

### Post by cardinals_fan on 2008-12-16
> **handydan918 said:**
> BS!

I think I called you on this once before. 


Did you ever find a link to the linux virus database?
No? 
That's because there aren't any. 
Well, none that work...
Faugh.

Better yet, never mind the link. Just send me the virus. You can PM me. I'll give you the URL of a drop.io account.
First, viruses are no longer a major problem.   Filtering by ISPs and webmail providers has cut down significantly on the number of viruses in the wild.  Most of what are now called "viruses" are really various trojans or bits of spyware.  These are spread by user incompetence through various social engineering schemes, and could easily be written for Ubuntu.  A limited-user-by-default policy is helpful, but if the user just blindly enters their password to install apps, it is no protection.

My point?  Malware problems on any OS are related solely to user competence, or the lack thereof.
> **handydan918 said:**
> 
Brilliant. According to netcraft, somewhere between 40 and 60% of webservers are running Linux. Why crack a desktop when you can pwn a server!?

...because cracking a [well-managed] server requires some serious time, effort, and ability.  Malware that takes advantage of user ineptitude is easy to write and easy to spread.

---

### Post by rhcm123 on 2008-12-19
> **handydan918 said:**
> Yet more unsupported opinion. The most credibilty-destroying statement anyone could make;


Brilliant. According to netcraft, somewhere between 40 and 60% of webservers are running Linux. Why crack a desktop when you can pwn a server!?

Because you can't. 

Again.

If you want to put on the black hat, PM me and I'll send you my public IP addy. 

Let's see if you can get past a NAT router, first..


LULZZ!!!111oneoneone!!

Pfft...

I have a spare laptop that i experiment on, and one of my favorite things to do is the black hat. I drop the server behind a NAT firewall, and it runs a basic web server, which i then try to break into.

I also do this the other way around. I setup a malicious site on my laptop, and see if the experimental computer can connect, get the bad code, and then have it auto-execute.

The first option works easy. I've actually ssh'ed to it on port 80 (!). The second one, not so much. :)

And why crack a desktop and not a server? Because most servers are hiding behind firewalls that drop all connections except 80 (http) and 443 (https) and occasionally ftp (21) if they need it, and the rest of the ports auto-drop the connection.

Most desktops have the ports at least exposed, if not purely open! Some ISP's take to dropping IDENT, IMAP, etc for their clients because these are such attacked ports!

My server has 8080 open (as my isp blocks 80 to prevent cheap and easy web hosting... grr). 22 for ssh, 21 for ftp, 10000 for webmin. 25 for SMTP, 110 for POP3, 143 for IMAP.

> **handydan918 said:**
> Let's see if you can get past a NAT router, first..
If you really think a basic NAT router can protect you, you are sadly mistaken. If I can get through NAT to a windows machine, then I can cerainly do it for a linux machine.

---

