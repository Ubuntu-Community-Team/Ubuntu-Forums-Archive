---
title: "Help with dual NIC setup"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by Akovia on 2008-02-07
Hi,

I've been trying to work out a &#8220;not so standard&#8221; network for a few days now and keep running into dead-ends. I have posted for help in other forums but either there is no solution or it's more than anyone is willing to bite off. In any case, there seem to be some really helpful people in this community and figured it couldn't hurt to try for help here.

**Design Goals:**

I am trying to have my host OS and my Virtual Machine Guests use separate NIC cards.

**Equipment and Software:**

Host Machine = x86

CPU = AMD Athlon 64 FX-62 Dual Core

M/B = Asus Crosshair

Ethernet = nVidia nForce NIC (x2)

**Network Hardware:**

Arris Cable Modem (also IP Phone)

Linksys WRT300N (Inet Gateway 192.168.1.x)

Linksys WRVS4400N (10.0.0.x)

**Software:**

Host = Windows XP SP2

[INDENT]Kerio Firewall 2.1.5[/INDENT]

Guests = Virtualbox 1.54

[INDENT]Ubuntu 7.10 (W/Guest Additions)
[/INDENT]
[INDENT]XP SP2[/INDENT]

[INDENT]Windows 98[/INDENT]


I think that's all the relevant information but can add anything I missed on request.


I want to add a little more detail so it can be understand why I'm trying to do this and the problems I've run into so far. My machine was bought mainly for gaming and graphics and I'd like to streamline it to do just that and use virtual machines for as much of everything else as possible. I want my host machine to have access to the internet to get updates for software and such but will use one of my virtual machines for most of my internet activities and LAN access. My host machine does not need any type of local network access and would like to close those ports on my host.

After messing around for quite a while and trying some of the information I found that is relevant I've run into some roadblocks. First and foremost, I haven't found a way to completely circumvent the host firewall with my guest machines. I want my guest VMs to have complete access to the outside world without interference from the host machine. Secondly, I haven't found a way to tell my host OS to only use the NIC I specify. It seems like there should be a registry setting or some other way to direct the host to only use NICx but I haven't found it.


The diagram below shows how I have it set up now which is the closest I've gotten to my goal.


[IMG]http://eidolen.zftp.com//images/Forumpost/Ubuntu/VboxNetDiagMed.jpg[/IMG]

To me this doesn't seem to be such a far out notion but I can't find any information on doing a setup this way. I am happy to read any information I am pointed to to help myself with this issue and am not asking for a handout, but I'm trying to do this quicker than taking a couple online courses before I can get some joy.:)

Thank you in advance for any and all information that might help my cause. 

Best Regards,
Akovia

---

### Post by Akovia on 2008-02-08
Could anyone even suggest a place I might find help? I know it's a cross platform issue and tried Virtualbox forums first but it seems they won't help anyone that doesn't speak code. Trying to get help from M$ on hooking up Open Source software is a joke unto itself and I wouldn't be using it all if I didn't need a few things. Which is why I'm trying to make the switch.

I realize I could go the dual boot route if all else fails but the convenience of Vbox is very nice and other than this issue with networking, is working better than expected. In fact, finding the images they had for download was the first link to converting me over to Ubuntu so I'm grateful. Just a little disappointed they are not very community oriented if you are not a programmer.

I would like to start working with Firestarter but am afraid it will interfere with Kerio on the host system and don't want twice the work trying to undo things so I'm kinda in a holding pattern.

Any advice would be welcomed.
Akovia

---

### Post by dieselpower on 2008-02-08
VMWare does this as far as I know. VMWare has much better networking, to the point VBox is useless to run servers on after I tried VMWare. The only catch is VBox seems much faster. You can run VMPlayer, which is nice for end user desktop stuff, but you have to either build your images in VMWare Server or use an online service. Or you can just run out of VMWare Server. I believe you can still get free licenses for server. I know this is not answering your question, but it may be an alternative if someone else does not come along with more networking knowledge then me. I should know, running a wireless ISP, but I'm a little network challanged every once in awhile ;)

---

### Post by Akovia on 2008-02-10
Thanks for the reply diesel, I looked at VMWare before VBox and and though it looks really polished, it comes at a polished price if you want more than just the basics. After having such a good experience so far with ubuntu, I'm really finding it difficult prying myself away from open source software, even with some of the short-comings.

I guess I'll just keep asking around and trying to learn in the process to see if I can solve my dilemma. (Been spending a good bit of time lately studying bash, grep, regex's, sed, etc...) I get so frustrated searching Google to dead-end after dead-end that I have to take a break sometimes. Hopefully someone in the know will post a good link that can point me to some qualified help or resources that will get me closer.

Thanks again.
Akovia

---

### Post by imbroglioj on 2008-06-14
If you or someone else is still looking, here are two suggestions.
First, the free VMWare server is plenty powerful -- so good that I would pay for it.  Second, if you want to enjoy your virtual life, you should make Linux the host if at all possible.  The Windows memory management seems to be pretty bad, so that Linux host and Windows guest is a powerful pair (speed + convenience), but Windows host and Linux guest is noticeably less acceptable.  Example:  on the same machine, I can run 4-6 times(!) as many heavy-duty applications (including an XP virtual machine) with Linux host as compared to an XP host.  If your Linux has all the drivers you need, then a Windows guest is the way to go.  (You will have to call Microsoft for a new activation number.)  I have even had luck installing XP as a guest from those dratted "recovery" disks, at least on a Dell.

---

