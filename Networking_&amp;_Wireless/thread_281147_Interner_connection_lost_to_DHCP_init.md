---
title: "Interner connection lost to DHCP init"
date: 2006-10-20
forum: Networking &amp; Wireless
---

### Post by paddy_ on 2006-10-20
Hello,

I'm a 4-days-old linux beginner trying to migrate to kubuntu 6.06.

All was going right until this morning, when I realized that I wasn't able to connect on internet.

After some investigation, I believe it happened because the DHCP server in my modem/router has been initialized. Thus I got a new adress : 192.168.1.10 (instead of 192.168.1.13 when installing kubuntu).

It seems kubuntu doesn't manage this situation. I am currently using the livecd which is working well.

How can I tell kubuntu to use the new dhcp IP. I changed value in "network parameters" with no result. I rebooted the computer with no more results.

Some help would be really appreciated...

Regards

Paddy

---

### Post by Iowan on 2006-10-20
There are a few threads around on DHCP resetting DNS servers.  I'll see if I can locate one for you.
[http://www.ubuntuforums.org/showthread.php?t=279339]("http://www.ubuntuforums.org/showthread.php?t=279339")
Check **handy's** post#3.  
Not intending to dump/run - if that doesn't work, or if you need more advice/instructions, please ask.  I don't want to drown you with details, but don't want to suggest "this is all you need - if it ain't enough... tough".

---

### Post by paddy_ on 2006-10-20
Dear iowan

A big thank for your quick answer.

I am going to check the post you indicated. I will come back to say if it works or not.

Regards

Paddy

---

### Post by paddy_ on 2006-10-20
Hello,

I followed the instruction in the indicated post.

In the /etc/dhcp3/dhclient.conf file, I inserted a prepend line with the IP of my router (192.168.1.1)

Now, in the "network parameters" the good IP for my PC is indicated (192.168.1.10 chosen by the router)

when typing in the konsole

```
sudo ifup eth0
```

I got this kind of result :

> DHCPOFFER from 192.168.1.1
DHCPACK from 192.168.1.1
bound to 192.168.1.10  - renewal in xxxxx seconds

This is in progress but unfortunately within konqueror I always get the same message :

> [www.xxxxx](www.xxxxx) unknown host

Tell me if you need more info.

Regards

Paddy

---

### Post by lloyd_b on 2006-10-20
It sounds like you are connecting to the network fine, but there's a problem with DNS.  Simply put, the web browser is failing because it can't look up the name you're giving it to find it's IP address.

Could you post a copy of "/etc/resolv.conf"?  This is where nameservers are defined.

Lloyd B.

---

### Post by paddy_ on 2006-10-21
here it is !

/etc/resolv.conf :> 
nameserver 192.168.1.1
nameserver 192.168.1.1
nameserver 0.0.0.0

Thanks for your support everybody.

This forum is really reactive and as a beginner it makes me feel secure.

Regards

paddy

---

### Post by paddy_ on 2006-10-21
Ok, I removed the 2 last lines of my /etc/resolv.conf file and I restarted my kubuntu.

I have allways the same error message when trying to acces to internet with konqueror :

[www.google.com](www.google.com) : unknown host (for google and any other site...)

](*,)

Any help will be welcome

Regards

Paddy

---

### Post by handy on 2006-10-21
Hi Paddy, you need to find your ISP's DNS IP addresses to use with the following argument in **/etc/dhcp3/dhclient.conf** :

**prepend domain-name-servers ***.***.***.***, ***.***.***.***;**

Your router's address is NOT the right one to use.

If you put your router's address into the address field in firefox (or whatever browser you use), you should be able to access it's firmware setup pages & see your ISP's DNS addresses.  If you can't you will have to get the addresses from your ISP's web site, or contact them directly.  Unless you allready have the info' of course... :)

---

### Post by handy on 2006-10-21
Paddy, I have to go to bed now, it after 2am here.

I can see the problem that you have, If it's not me then someone else will have you sorted out pretty quickly, it's NOT a big problem, it's just like everything else, easy when you know how.  :)

Hang in there, it gets easier, after you have been using Ubuntu for a month it will feel much more like home. :cool:

---

### Post by paddy_ on 2006-10-21
Handy, I don't have a lot of time this week-end, so I will try what you said tomorrow or monday.

Unix is an old friend. I was working on Sun workstations in 1988-1993. I don't remember a lot, but I am rediscovering smoothly the logic of unix systems that I liked really. 

Unfortunately internet wasn't a reality for me at this time and I am a real beginner on this subject.

I am really grateful for your help and for everybody's help. Thanks a lot. Now is coming the time for me to live an old dream.

Regards

Paddy

---

### Post by paddy_ on 2006-10-21
:-k mmmmhh!!

I got my ISP's DNS adresses from my router and changed the prepend line in the **/etc/dhcp3/dhclient.conf** file.

Not much progress anyway, always the same error message "www.google.com : unknown host".

I always need your help... (sorry ;) )

---

### Post by handy on 2006-10-21
Do the **ipv6** thing in firefox too Paddy, it is quick & easy & often absolutely necessary.  It follows directly after the DNS stuff in **Post 3** of  **[that thread.]("http://www.ubuntuforums.org/showthread.php?t=279339")** :)

By the way, did you restart the network or reboot after doing the **prepend** thing?

---

### Post by paddy_ on 2006-10-23
Handy : thanks for your support!

Effectively, after each change I made I used to reboot my PC. This is an old habit with computers... ;)

About firefox, I am not using it anyway. In fact I took it off my kubuntu because it didn't launch, saying something like  "Another instance of firefox is already running". But there was no other firefox in the proc table... So I just get konqueror which is really nice.

I am afraid something (ie a program, but which one ?) has messed up some configuration files, may be too many to get a simple solution. I don't understand very well the link with the DHCP server init and I'am considering getting the same trouble at each new init... :( 

I am thinking about installing kubuntu again. May be I will get the same trouble with DHCP server reset, or may be not...

Is there a way to preserve the modifications I made (nvidia drivers, scanner drivers, etc) or do I need to restart from scratch ? (may be I should post this to another forum...)

What's worrying me is that I would like to fix the pb, just to avoid system installation each time there is a mess...

Your feeling is welcome (with any idea for solving this pb ;))

Paddy

---

### Post by handy on 2006-10-23
The best solution for making it as quick & loss free as possible that I know of is this:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

After having done the /home partition thing, life really is so much easier with linux.

I used the info' from that link to create a separate /home partition.

I have installed Edgy RC1, & it was so quick I don't know why people would want to do upgrades instead of a clean install?

Something that I use at each setup of a Ubuntu machine is [_**Automatix**_]("http://www.getautomatix.com/").  I can not recommend it highly enough, (from my experience).

It will set up your nVidia drivers & about  40 other options if you call them on!?

So check it out & don't listen to those that bad mouth it, saying that it stops you from learning stuff that you need to know!

When we need to know it, we will learn it!

I Say! :)

---

### Post by paddy_ on 2006-10-23
Handy : thanks for your advice. Your links are really interesting.

I'm going to re-install kubuntu, hoping trouble will not come back.

I'm grateful for all the support I got in this thread. Thanks to all and see you soon... :D 

Paddy

---

