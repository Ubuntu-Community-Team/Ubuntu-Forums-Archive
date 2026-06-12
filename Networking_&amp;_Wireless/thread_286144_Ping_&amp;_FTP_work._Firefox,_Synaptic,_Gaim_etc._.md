---
title: "Ping &amp; FTP work. Firefox, Synaptic, Gaim etc. Do Not."
date: 2006-10-27
forum: Networking &amp; Wireless
---

### Post by Leav on 2006-10-27
Hello and Thanks for taking the time to help me out :) 

My Brand new Edgy box is connected to a DSL modem/router.
I get an IP through DHCP and the connection works: I can browse into my router.

Using the network tools in ubuntu I can ping [www.google.com](www.google.com) and get a decent ping. no problems.

However when I open firefox and try to navigate to [www.google.com](www.google.com) I get an immidiate halt. not a "i'm trying to reach the web page - give me a minute" page just a "i'm not going to do that" page.

Also, synaptic can not connect anywhere and GAIM doesn't work either...

BUT!
FTP does work and I can navigate to my web server's FTP!

iv'e read a bit on the forums trying to solve my problem, but it seems that it has something to do with IPv6, which unless it is the new way that IP addresses work (longer addresses), I have no idea about.
(and if it is the new way they work, that's all i know about it.)

any idea how to fix my problematic connection?

Thanks!
-Leav

---

### Post by Leav on 2006-10-27
Ok got it.
after posting used the ipv6 tag to get some more info on the subject.

what I did, for future's sake:

made a file on my desktop called:
```
blacklist-ipv6
```
then edited it with gedit to insert:
```
#disable IPv6
blacklist ipv6
```
then used this opened the terminal, and navigated to the desktop.
in the terminal:
```
sudo cp blacklist-ipv6 /etc/modprobe.d/
```

Rebooted, and it works!

silly IPv6, the Internet is for IPv4!

-Leav

---

### Post by Leav on 2006-10-27
This sucks!
Synaptic still doesn't work. neither does GAIM.

just firefox works.

please help!

-Leav

---

### Post by bayvista on 2006-10-29
Same problem. I've submitted a Bug report.

Firefox OK. Synaptic, Pan NBG (no bloody good).

David

---

### Post by stream303 on 2006-10-30
Sounds like the dreaded DNS timeouts when pings work fine, but dns fails or times out - sometimes exposed by a funky /etc/resolv.conf file.  What does your /etc/resolv.conf look like?

Many times the internal dns of inexpensive routers can be a source of the problem, letting you time out in frustration until it gets to the dns addresses of your isp.

Just a thought to look at...

---

### Post by bayvista on 2006-11-05
Hi,

This is my /etc/resolv.conf:

nameserver 10.1.1.1
nameserver 192.168.0.1

Also, some output which may help:

david@linuxpc:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) dapper-backports Release.gpg
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg
  Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
david@linuxpc:~$


I can access the repositories using Firefox.

I have killed ipv6.

However, I am sure this problem is because I now go to my ISP via a router and modem. Before, I had an ADSL router which worked fine. I have also written to D-Link about this one. I think you are on the right track

Thanks

David  :p

---

### Post by handy on 2006-11-06
Hopefully [this how-to]("http://ubuntuforums.org/showthread.php?t=282034") will sort out your problem.

I think the DNS section of the how-to is what you need.

**[Edit:]** *By the way, the cause of these problems, are cheap windoze centric hardware (router/modem).*

---

### Post by AndrewS on 2006-11-06
> **Leav said:**
> Hello and Thanks for taking the time to help me out :) 

My Brand new Edgy box is connected to a DSL modem/router.
I get an IP through DHCP and the connection works: I can browse into my router.

Using the network tools in ubuntu I can ping [www.google.com](www.google.com) and get a decent ping. no problems.

However when I open firefox and try to navigate to [www.google.com](www.google.com) I get an immidiate halt. not a "i'm trying to reach the web page - give me a minute" page just a "i'm not going to do that" page.

Also, synaptic can not connect anywhere and GAIM doesn't work either...

BUT!
FTP does work and I can navigate to my web server's FTP!

iv'e read a bit on the forums trying to solve my problem, but it seems that it has something to do with IPv6, which unless it is the new way that IP addresses work (longer addresses), I have no idea about.
(and if it is the new way they work, that's all i know about it.)

any idea how to fix my problematic connection?

Thanks!
-Leav
FWIW I had a similar problem with Dapper and Edgy.  I found this workaround on the forum (can't remember where):

sudo gedit /etc/modprobe.d/blacklist

add the following (I put it at the end, might not matter):

alias net-pf-10 off

I think I had to reboot to get it to work.

Regarding getting the repositories, updates etc to work, again, feretting round the forum I got the following fix:

sudo gedit /etc/resolv.conf

I had a single entry there, giving my router's IP address for the nameserver.  I changed it to:

nameserver:203.8.183.1

Thsi works fine for a while, or until you reboot, then you have to do it all over again.  There is a fix for that too, but I can't get that to work (see [http://www.ubuntuforums.org/showthread.php?t=250149)](http://www.ubuntuforums.org/showthread.php?t=250149)).  Let me know if you know how to so this bit!

HTH

Andrew

---

### Post by handy on 2006-11-06
@Andrew; I think that [this how-to]("http://ubuntuforums.org/showthread.php?t=282034") is appropriate for you too.

**/etc/resolv.conf**

gets overwritten often, which has the effect of making the repo's, gaim, automatix download, skype... unavailable to us, though we can still browse the web. 

This problem strikes those of us with cheaply made router/modems.

We can do a variety of things to get our correct DNS addresses where they should be, just to have them replaced by our router's IP again!!

Using [this how-to]("http://ubuntuforums.org/showthread.php?t=282034") will stop that.

---

### Post by AndrewS on 2006-11-07
Handy

Many thanks, both tips worked a treat - no more editing resolv.conf every time, and Firefox is fine.  Thinking about it, these must be common problems for people installing Dapper/Edgy?  So I/m a bit surprised there isn't something in the install script about it.

Anyway, thanks again.  Don't know anything about getting the CS423x sound cards working in a Thinkpad do you?!?

Andrew

---

### Post by handy on 2006-11-07
I'm glad it worked, we love feedback! :) 

The problem is NOT Ubuntu's it is the modem/router's fault, some chipsets are really crap, they are just enough to work on windoze & bugger all more smarts are built into them.

As time goes by we learn, next time I have to buy a modem/router, I will be asking a few questions on the forum for sure.

Have you searched the forum's for your soundcard, it has probably been done?

If you do no good searching, try post in the **Multimedia & Video** forum?

[This link may be helpful?]("http://ubuntuforums.org/showthread.php?t=205449")

---

### Post by AndrewS on 2006-11-07
Hi

I wasn't getting at Ubuntu and I quite understand it is a router manufacturer problem - just that there must be a lot of folks out there stuck with those routers!

Thanks for the link, I had seen it but it didn't allow me to fix it.  There are quite a lot of posts in the  M&V forum, I'll keep working through the suggestions there.  Others have got it to work so it must be possible.  One post did refer to "the chip from hell" though!

Andrew

---

### Post by AndrewS on 2006-11-08
Just for information, Szabi's suggestions in [this thread ]("http://www.ubuntuforums.org/showthread.php?t=230076")got the Thinkpad making noises, but I still need to do some reading on symbolic links.  It obviously isn't as simple as making a text file with the instructions, then following the code given by Szabi...  I'm a bit worried about whether I've got ACPI etc installed - more reading!

Andrew

---

