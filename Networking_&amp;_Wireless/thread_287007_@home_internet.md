---
title: "@home internet"
date: 2006-10-28
forum: Networking &amp; Wireless
---

### Post by roger_s on 2006-10-28
Hi all,

I'm trying to connect to th internet using ubuntu dapper. My ISP uses DHCP and hostnames. Meaning that you need to have a hostname set like cp*****-x. This hostname is unique and provided by the ISP. 

I have tried several things using the DHCLIENT, but I do not get any IP address. The network card itself is working fine.

When I set the IP address manually IP address, dns, hostname, etc.. evrything works fine. But when the IP address expires I have no internet connection anymore. Does anyone have any idea how to get this to work (and not switching to a different ISP)?

Thanks in advance

Roger

p.s. the ISP is called @home. [www.home.nl](www.home.nl)

---

### Post by frenkel on 2006-10-28
Searching with google, take a look at the first hit:
[http://www.google.nl/search?hl=nl&q=%40home+linux&btnG=Google+zoeken&meta=](http://www.google.nl/search?hl=nl&q=%40home+linux&btnG=Google+zoeken&meta=)

Detailed explanation how to set it up for Debian. Ubuntu is Debian based, so you can even do what it says literally.

Did you even try to search before posting?
Man, so much people are just posting before searching...

---

### Post by trubblemaker on 2006-10-28
I don't think that posting is a bad idea to get an answer to a question, but you do need to due some searches, there are some network managing software out there, (usually for laptops but should do the job for you)  that can help you with you issue.

---

### Post by squibT on 2006-10-28
> **trubblemaker said:**
> I don't think that posting is a bad idea to get an answer to a question, but you do need to due some searches, there are some network managing software out there, (usually for laptops but should do the job for you)  that can help you with you issue.

This forum is loaded down with posts asking the same questions over and over again...I started to ignore them. How much help is that. Not searching is lazy....just plain lazy...the answers are right there in Google or here.

---

### Post by handy on 2006-10-28
We learn as we go... It took me **ages** before I new how to do everything in the universe...

Especially how to be kind... :KS

---

### Post by squibT on 2006-10-28
> **handy said:**
> We learn as we go... It took me **ages** before I new how to do everything in the universe...

Especially how to be kind... :KS

Big Baby...How about reasonable...its reasonable to do a little research first. This forum is brimming with solutions to almost every problem and has multiple answers and resources if you use the search button. Google even points here.

You evidently haven't learned enough if you don't think a simple search is a valid request...
>>Not searching is lazy....just plain lazy...the answers are right there in Google or here>>

That is not an unkind statement, it is a fact and a push in the right direction.

---

### Post by roger_s on 2006-10-29
Ok, maybe I should have posted that I tried the options listed at Trooubles @home, hence that is why I set everything manual. 

That didn't do the trick. On the dutch forum people seem to have the same issue.

Regards

Roger

---

### Post by squibT on 2006-10-29
How are you connecting to your ISP....modem and attached router? If you have a router that you can config you can set it up there...it will pass all dhcp info to your Ubuntu computer...I may be wrong but I dont think this is a client side issue (Ubuntu)
My Linksys + DD_WRT has settings for ISPs hostname

---

### Post by roger_s on 2006-10-29
I'm connecting directly to the internet, no router attached. When I use a router, it works fine, as the router accepts the hostname and thus receives an IP address from my ISP. I haven't recently tried a different distro, but I know it works fine with SuSE, wich was using dhcpd, not dhclient, but it has been a while (1 year or so)

---

### Post by squibT on 2006-10-29
You really should be using a router...they are cheap these days...you gotta be safe.

Synaptic Package Manager has the option to install dhcpd

---

### Post by roger_s on 2006-10-29
Don't get me wrong. I distributing Ubuntu with new PC's. @home is a commonly used ISP in the Netherlands. I cannot sell this to my customers. to install dhcp you need an internet connection

---

### Post by roberine on 2006-10-29
During setup you were asked a hostname.
Here's where you should have entered the cp* number.
To change it now edit the /etc/hostname
and change whatevery is in there to the cp* number and reboot.

You should now have internet access.

Herbert

---

### Post by roger_s on 2006-10-29
Hi Herbert,

I'm not new to linux. I can change the hostname in the gui as well. If it would have been that simple I would have had an internet connection by now.

---

### Post by trubblemaker on 2006-10-29
squibT, ignore posts, it's your right, your previous answering which amount to RTFM isn't helpful, stick to ignoring.  If you want to help then post, saying google it and go buy a router aren't helping his problem if you want to help, post an answer, if you want to bitch about him or his asking a question tell your mom she might care.

and google points here because once upon a time someone posted a question.  I've answered alot of posts that I've answered 5-6 times, because I ask questions and someones helped me, it's karma.

sorry roger_s no help for you in this post

---

### Post by roger_s on 2006-10-29
hi trubblemaker,

Thanks for understanding. As I said I'm not new to linux. And I'm not the only person having this issue in the Netherlands using @home as an ISP.

I need to fix this issue, as I'm distributing Ubuntu with my new PC's. If I tell my customers that, when they use @home the NEED to buy a router to use their PC with Ubuntu installed, the will swiftly install windows, as it works fine. For me this is no option.

Regards

Roger

---

### Post by trubblemaker on 2006-10-29
ok, if you know how to get an ip address that works, and you can figure out when your lease is up, (which you can by viewing the dhcp.lease file.) then you should be able to write a script that fixes the issue.  In other words, you create a script that is set to run when the lease is up 
gets a new address 
then  sets the address.
I know that this is an additional thing to setup on the pc's however it's only a file and not a package so it might work for you.  This is not a fix but a stop-gap measure until you can get a corrected fix.  Again the are connectivity packages that are worth looking into.  Some that are meant for wireless laptop connectivity might work out for wired machines.

script example

It would look something like, two scripts, one that checks your lease and sets the other script to run when it's time to renew your lease.

the other script gets an ip address and sets the address so the computer "seemlessly" has a new ip.  Then sets up the next call to the call to the lease script. downtime would be minimal especially if you set the "update" portion to a low use time of day.

---

### Post by roger_s on 2006-10-30
Hi Trubblemaker,

That would work for me as you said, but not for my customers. They are "not smart enough" to set this up themselves.

Regards

Roger

---

### Post by trubblemaker on 2006-10-30
Sorry I thought that you where installing for them.  You could always issue, an "internet connection disc" that they had to but into the disc drive and double click to get connected to the internet.  (then it would be a script that installed the script) But It seems that you are a little more removed from the customers.  Does your isp support Linux, can you call them for help or are they evil and not supporting linux.  Maybe they have a webpage setup page for linux?

---

### Post by roger_s on 2006-10-30
I'm installing for the (pre installed). But I do have customers who are just recently connecting to the internet, but have bought a pc a while ago.

The isp has limited support only, I will give them a call.

Thanks Roger

---

### Post by trubblemaker on 2006-10-30
checkout 'rocks' in synaptic, it looks like a candidate to help you

---

### Post by roger_s on 2006-10-30
What is rocks (currently on working on a Windows machine at work)

---

### Post by trubblemaker on 2006-10-30
From synaptic
```

Make network sockets reliable in a transparent way
Rocks protect sockets-based applications from network failures, particularly
failures common to mobile computing, including:

 - Link failures (e.g., unexpected modem disconnection);
 - IP address changes (e.g., laptop movement, DHCP lease expiry);
 - Extended periods of disconnection (e.g., laptop suspension).

Rock-enabled programs continue to run after any of these events; their broken
connections recover automatically, without loss of in-flight data, when
connectivity returns. Rocks work transparently with most applications,
including SSH clients, X window applications, and network service daemons.
```

---

### Post by roger_s on 2006-10-30
is it installed by default?

---

### Post by trubblemaker on 2006-10-30
nah you need to install it with synaptic or apt-get.  haven't tried it put it's worth a shot.

 also see [this page ]("http://ubuntuforums.org/showthread.php?t=264086&highlight=%40home+isp")for some more ideas on a similar problem, it's mostly point and click plus prewritten script for the connectivity, you'll have to change some of the functionality but it helps to have otherwise tested scripts

---

### Post by roger_s on 2006-10-30
My bad, I thought I had to uninstall it. I will read the docu and get back as soon as I know some more. Thanks for your help!

---

