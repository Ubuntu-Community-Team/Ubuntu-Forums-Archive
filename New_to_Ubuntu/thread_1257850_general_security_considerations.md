---
title: "general security considerations"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by am65 on 2009-09-04
Hello, I come from Windows and I'm a bit obsessed with security because I had to reinstall Windows three times in the last 5 years due to malware, virus and so on. So I installed a firewall and periodically made scans of the whole system with free antivirus tools.

In Ubuntu, do I need also to install a firewall and an antivirus or is it safe enough with the default installation?

Thanks

---

### Post by tomBorgia on 2009-09-04
Hi,

You'll find that out of the box the system is fairly secure - It should be fine behind a domestic router as long as your not planning on running internet facing services (webserver, ftp etc)... There is no real malware as such but you still need to be careful installing software from untrusted sources. 

You can harden the system as much as you like by installing a firewall (such as iptables) and locking out any unused ports, switching off certain services & using difficult-to-guess passwords. There are plenty howto guides out there... linux in general is widely used for webservers and has as good a security record as any o/s.

---

### Post by Hospadar on 2009-09-04
Firewall:
Not really needed:
First off understand that there really is no "installing" of firewalls in linux.  If you want to block ports, you may freely do so, but any blocking will be done by netfilter, which is controlled by iptables, which is in turn controlled by some convenient interface like ufw (uncomplicated firewall).  Netfilter is built into the kernel.  So - If you feel the need to block certain ports or IPs or whatever, you can use ufw or some other frontend to do so.  That said, It's not generally needed.  If you are using a router at home or elsewhere, you *really* don't need to block ports since the router blocks all ports automatically.

As for virus scanning, you can certainly scan for stuff, but it's probably not really necesary.  I've had a home server up for about 2 years now, scanning every week and haven't detected a single virus.  Let's face facts, if you are a malware writer, you could target 90% of people on windows, or >1% of people on linux.

If you want to scan, I'd use clamav, it has a command line interface, there are some graphical interfaces, but I wouldn't bother, all you do is a) update database with 'freshclam', and then b) scan with 'clamscan' at home I use a cron job to automatically update and scan once a week.  It's probably a good idea to scan occaisonally, but you'll never have anything like the norton system-tray ever-scanning madness. (It's totally unnecesary, and even on windows is something of a smoke-screen)

If you practice reasonable safety measures (try to limit your usage of mysterious russian porno and warez, don't send your password to that nigerean prince who is just *dying* to wire you 20 mil) you'll be totally fine.

---

### Post by mbzn on 2009-09-04
I general the standard install is (safe), no guarantee.

I have never had any anti virus or whatever programs windose use for it's false sense of security, and have never had a problem with viruses in Linux. However there is some steps you can take if you are really concerned just search it on the forum, but i wouldn't worry about it unless a) you connect or transfer data to a win machine
       b) you access you win partitions in Linux

In both cases there will be no effect in Linux but the windose machine might get infected

---

### Post by HiImTye on 2009-09-04
since you asked two questions, really, I'll answer you in two parts.
malware:
you really don't need to worry about viruses. virus scanners for linux scan for windows viruses to stop linux machines from spreading them to windows machines. that said, if you have a windows machine on your network that you actively share files with, you should probably install an antivirus program. I recommend [Avast!]("http://www.avast.com/eng/avast-for-linux-workstation.html")
the main part of the malware/virus question for linux is in terms of installing software from unknown sources. make sure the source is reputable (do a quick google search, for example. odds are if there is a problem with the source there will be threads about it).
make sure you don't enter your administrator password for things that don't seem like they need them. obviously you will need to enter your password to install programs and perform administrative duties but if a program asks you to enter a password or run as root for say, to listen to music then you should wonder why you need to. if you never insert a password for things that shouldn't require them then generally you should be ok. I would also give a read over on the sticky thread about malicious commands on here. it's either in this forum or the general help forum

firewall:
if you are behind a router on your network you should be fine. if you are not or you want to feel more secure then give ufw or gufw a go. they're fairly easy to configure and there's lots of documentation on them. gufw is a graphical way to set up your firewall

---

### Post by mikechant on 2009-09-04
> the main part of the malware/virus question for linux is in terms of installing software from unknown sources. make sure the source is reputable (do a quick google search, for example. odds are if there is a problem with the source there will be threads about it).

Coming from a windows environment, the important point to emphasize about this issue is *always install from the repositories* if possible. Your gui package manager - add/remove programs or the more comprehensive 'synaptic' (or the command line equivalents) should *always* be your first port of call when installing software and should cover 99% of your needs. The software in the repositories is checked and crptographically signed and (virtually) guaranteed to be malware free.

Only install from outside the repos if the package you need is not available or you really need a more up to date version.

---

### Post by HiImTye on 2009-09-04
> **mikechant said:**
> Coming from a windows environment, the important point to emphasize about this issue is *always install from the repositories* if possible. Your gui package manager - add/remove programs or the more comprehensive 'synaptic' (or the command line equivalents) should *always* be your first port of call when installing software and should cover 99% of your needs. The software in the repositories is checked and crptographically signed and (virtually) guaranteed to be malware free.

Only install from outside the repos if the package you need is not available or you really need a more up to date version.
I concur

---

### Post by BbUiDgZ on 2009-09-04
If you want a nice GUI front end for your iptables install firestarter

either use synaptic or in terminal type
```
sudo apt-get install firestarter
```

you can get [clam anti-virus](http://www.clamav.net) for the linux platform but this is more for the protection of windows machines on your network that might be accessing file shares on your ubuntu machine (used mostly for e-mail and file share servers).

---

### Post by oldos2er on 2009-09-04
The OP might want to read [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by ayenack on 2009-09-04
> **tomBorgia said:**
> 
You can harden the system as much as you like by installing a firewall (such as iptables).

Just like to say iptables is already installed as standard in ubuntu. So is [UFW]("https://wiki.ubuntu.com/UbuntuFirewall") which is a front end for iptables you can install a GUI for UFW if desired to.

GUFW For GUI. Easy way to use UFW:-

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

UFW For command line. Harder way to use UFW:-
[https://help.ubuntu.com/8.04/serverguide/C/firewall.html](https://help.ubuntu.com/8.04/serverguide/C/firewall.html)

Also I like like to have rkhunter installed.

It can be installed like this.

**sudo apt-get install rkhunter**

And run like this.

**sudo rkhunter -c -sk**

If you need help understanding rkhunter type this in terminal.

**sudo rkhunter --help**

---

### Post by am65 on 2009-09-04
Thanks for all your comments and suggestions. I'll need some time to digest it. But it seems that I can relax as long as I do not surf dangerous places or install unreliable software.

In the short term I will not have important documents in Ubuntu.

---

