---
title: "Intrepid: Very slow internet"
date: 2008-11-03
forum: Networking &amp; Wireless
---

### Post by gofes on 2008-11-03
Hello.

Since the upgrade to Intrepid my Internet (home broadband -> wireless router) has become very sluggish. Firefox is taking about a minute to open each page, when it was almost instant prior to the upgrade. 
I have tried to download a file but I am only getting speeds of 22 KB/s where I used to get about 100 KB/s.

The other PC attached to my network seems to be running fine, so I'm pretty sure the problem my end.

Any suggestions?

---

### Post by JemW on 2008-11-03
> **gofes said:**
> Hello.

Since the upgrade to Intrepid my Internet (home broadband -> wireless router) has become very sluggish. Firefox is taking about a minute to open each page, when it was almost instant prior to the upgrade. 
I have tried to download a file but I am only getting speeds of 22 KB/s where I used to get about 100 KB/s.

The other PC attached to my network seems to be running fine, so I'm pretty sure the problem my end.

Any suggestions?

Finding the same - time for a cup of coffee while FF decides to open...very frustrating. I was hoping on Swiftweasel, but it seems there's no build yet.

---

### Post by JemW on 2008-11-03
> **gofes said:**
> Hello.

Since the upgrade to Intrepid my Internet (home broadband -> wireless router) has become very sluggish. Firefox is taking about a minute to open each page, when it was almost instant prior to the upgrade. 
I have tried to download a file but I am only getting speeds of 22 KB/s where I used to get about 100 KB/s.

The other PC attached to my network seems to be running fine, so I'm pretty sure the problem my end.

Any suggestions?

P.S You're not another NVIDIA proprietary driver user are you? See other posts on this - may be the culprit. I'm going to disable NVIDIA drivers and see..

---

### Post by gofes on 2008-11-04
I have (sort of) fixed the slow Internet problem I was having.

I am running ubuntu on a laptop with a build in wifi chip. I blacklisted the modules (is that the correct term?) associated with the internal card, and used a wifi PCMCIA I had lying around. 
All now seems to be fine, so I guess the problem is something to do with the internal wifi chip I was using.

Not really a solution I know.

---

### Post by jamouneau on 2008-11-05
Similar experience, but got mine to work. 

First tried a livecd install and my network connection sounds about like yours, so slow as to be unusable. All the other computers on my lan were doing fine, as had 8.04 before the install.  

The tweaks needed to get 8.04 working (my computer is a Lenovo Thinkpad T61p) had no impact on 8.10.
Changes made in 8.04 were: 

added to /etc/sysctl
net.ipv4.tcp_sack = 0
net.ipv4.tcp_window_scaling = 0

changed/added to /etc/modprobe.d/aliases
alias net-pf-10 off
alias net-pf-10 off ipv6

With these changes both wired and wireless network connections worked fine in 8.04.

Re-installed 8.04 and got it networking again (changed as above). Decided to try update manager (avoided this before as torrent download of the livecd was much faster).

Update process was slow.  At the prompt "/etc/sysctl file is customized, do you want to keep or replace this file?" I kept the file. Did not see a prompt on the aliases file (but the update kept the modified one).

My wired nic is now working fine with 8.10 and my network and internet speeds are as fast as under 8.04. I don't have wireless setup so haven't checked that.

Real puzzling at how the same changes under update manager worked while they didn't with a livecd install.

By the way, the Nvidia driver is working great.

Hope this helps.

---

### Post by AlexOK on 2008-11-07
OK, I'm having the same problem. I was unable to find what exactly is causing the behaviour, I have very extremist approaches when it come to those issues. I have being looking for an answer and found tons of other peoples complaining about the same issue, there are many suggestions that might or might not fix the problem, I tried all of them without any result.
I came across the idea of the nvidia driver,mentioned above, I uninstalled it, no luck. ipv6 turned off, no luck, dns changes, no luck.
What I do know if that there is an update that causes the problem. Which one, I don't know, didn't have the time to research and point out the culprit. I noticed when I'm connected to the Cisco VPN at work, the problem is gone, so, definitely is a problem with the network components that is being downloaded with an ubuntu update. Since I'm unable to find out where the problem might be, I just decided to re format and re install Intrepid again, but this time without allowing the system to run any updates at all.
So far so good, I was able to install everything I need and want with zero difficulties, my internet is blasting fast now, however, no updates are being installed on my systems, and I guess it will remain in that way for a long long time until Ubuntu fix this issue before I decide to turn the updates back on.
Sorry, I suppose to come with a solution, this is not a real solution, but it works for me.

---

### Post by Rab22 on 2008-11-11
Similar experiences.  I just installed Intrepid today and my connection is slow.

I've tried a few hacks to no avail.

Wondering what could be causing this now... :(

---

### Post by a_toff on 2008-11-14
Same problem here. Fresh install of Intrepid. On a network with one other machine (iMac running OS X 10.4) which gets very high wifi speeds. 

iMac's wifi speeds in the range of 400 kb/s
Ubuntu laptop wifi speeds <1 to about 5 kb/s

Of course when I use a wired connection, the Ubuntu laptop gets the high speeds that I'd expect. Using wifi I can barely surf the web in Firefox, and can't even think of installing or updating packages.

(Running the proprietary Broadcom STA wirless driver.)

---

### Post by pravin03 on 2008-11-16
same problem for me too.
While with Hardy,I got 140Kbps download speed.But my Ibex is not climbing well over the bandwidth peak.
Is this a bug?

---

### Post by lifestream on 2008-11-17
I used to get 300kbps downloading stuff on Firefox, torrents, updates...

Now I'm lucky to get 5000 BYTES. I might as well downgrade to Dial up:P

If it matters, my WiFi card is Intel Pro 3945ABG [Golan]


I made my boyfriend sit next to me, next to the router, to test the speed, and he's downloading stuff really fast.

---

### Post by lifestream on 2008-11-17
[B]WHOA!!! BY THE POWER OF GRAY SKULL!!!
[/B]
I was using OpenDNS instead of my ISP' and, I decided to disable to see if it would make a difference.

IT DID. As soon as I clicked OK, my speed went up to 300kbps. OH YEAH!!!
BTW this was on wicD.

Still, I wonder why it wont work with openDNS.. It did just fine in Hardy...

---

### Post by lifestream on 2008-11-17
This is pure torture...
When I turned off OpenDNS net speed skyrocketed... but it's down again.

-____-

---

### Post by odeno on 2008-11-18
same problem here too. At first install everything was fine. I installed system updates and everything is slow as ever. Everything works fine off the liveCD so it must be an update. tried turning off ipv6, changing mtu size etc to no avail.

ubuntu 8.10
amd athlon 3000+
dual boot with xp

are there not some eggheads somewhere working on this - seems to be a fundamental problem with the latest and greatest release?

---

### Post by pravin03 on 2008-11-18
> are there not some eggheads somewhere working on this - seems to be a fundamental problem with the latest and greatest release?

is there any way out in your EGGHEAD,odeno?

---

### Post by odeno on 2008-11-19
I changed the mtu size to 1492 and this solved the issue!

To check your mtu simply enter 

>ifconfig

Mine was set to 1500. To change it to 1492 simply enter:-

> ifconfig eth0 mtu 1492

Obviously change "eth0" to whatever your mtu size is.

---

### Post by robertyou on 2008-11-22
> **odeno said:**
> I changed the mtu size to 1492 and this solved the issue!

To check your mtu simply enter 

>ifconfig

Mine was set to 1500. To change it to 1492 simply enter:-

> ifconfig eth0 mtu 1492

Obviously change "eth0" to whatever your mtu size is.

Wow man, that's a confirm!
By any chance you can explain how the magic number works?

---

### Post by robertyou on 2008-11-22
Here's the post explaining everything and the method to set correct MTU permanently.

[http://ubuntuforums.org/showthread.php?t=872346&highlight=mtu+internet](http://ubuntuforums.org/showthread.php?t=872346&highlight=mtu+internet)

---

### Post by styfle on 2008-11-24
> **odeno said:**
> I changed the mtu size to 1492 and this solved the issue!

To check your mtu simply enter 

>ifconfig

Mine was set to 1500. To change it to 1492 simply enter:-

> ifconfig eth0 mtu 1492

Obviously change "eth0" to whatever your mtu size is.

OMG it worked for my wlan0
Thank u so much!

---

### Post by ecoxmit on 2009-01-19
Having the same problem. The mtu trick above didn't solve my problem. (broadcom 4322). any other ideas?

---

