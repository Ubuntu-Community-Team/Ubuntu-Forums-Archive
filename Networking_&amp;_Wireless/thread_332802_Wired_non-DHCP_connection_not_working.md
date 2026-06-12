---
title: "Wired non-DHCP connection not working"
date: 2007-01-06
forum: Networking &amp; Wireless
---

### Post by MindDriver on 2007-01-06
Hello, I just installed Ubuntu 6.10 with the help of a friend. We had some trouble though - turned out that 6.10 can be installed only on an ext3 formatted partition ); Our original intention was to install on reiserfs, because, as he told me, it's faster than ext3.
Anyway, I reformatted the partition of choice to ext3 and managed to install succesfully.

So far, so good.
The first thing I wanted to do is set up my internet connection, because there's pretty much nothing I can do without it.
I enabled my built-in LAN card, clicked properties, entered my static IP address, my subnet mask, my gateway and clicked OK.
Then i went to DNS and entered my preferred and alternate DNS server addresses.

I hit OK and closed the networking window.
Then, with the thought that I've done it, I opened Firefox.
And since I had just finished installing and therefore had no bookmarks, I simply clicked on "Getting Started".
And guess what happened?
The message "Server not found" immedeately appeared on screen, as if I hadn't even connected my internet cable. I checked it and checked the settings (I am sure they're correct, because right now I am using them here in WindowsXP and I obviously have internet. And I even used a printed screenshot to enter them in Ubuntu e.g. no way I have made a mistake here.). I restarted into Win - active net connection, I restarted again - this time to Ubuntu - no net connection.

And right now I'm sitting here, thinking "What the hell!?". ](*,) 
This is the only thing that's stopping me to finally move to Ubuntu. :( 

Any help is appreciated. :-|

---

### Post by xiaoxin on 2007-01-06
i dont have a real idea what the problem with the network might be, but i can tell you that if you use the alternate install cd you can choose which fs the partitions get formatted as in your case reiserfs, maybe by installing using this cd the network will also work because network configuration is done during the installation

---

### Post by MindDriver on 2007-01-06
I didn't do any network configuration during installation, I can tell you that.

---

### Post by xiaoxin on 2007-01-06
i meant that you can set the network when installing if you use the "alternate cd"

---

### Post by MindDriver on 2007-01-06
What do you mean by "alternate cd" ? :-k

---

### Post by xiaoxin on 2007-01-06
there are 3 types of install cd's you can download
1. livecd/install
2. server cd
3. alternate cd

i assume you have the first one.

the alternate cd gives you a real installation process 

[http://ubuntu.ipacct.com/releases/edgy/ubuntu-6.10-alternate-i386.iso]("http://ubuntu.ipacct.com/releases/edgy/ubuntu-6.10-alternate-i386.iso")

---

### Post by MindDriver on 2007-01-06
Hm, will try it. Thanks. :)

P.S.: Thanks again, for giving me a local link.

---

### Post by xiaoxin on 2007-01-06
No problem :)

---

### Post by MindDriver on 2007-01-06
What the hell!? According to the installation process, the gateway that I'm using right now /in WinXP/ is unaccesable!? :confused:

---

### Post by xiaoxin on 2007-01-06
what is the gateway you are using? a router?

---

### Post by MindDriver on 2007-01-06
Well, according to the installation the gateway is a router, which ISPs use for connections outside their network i.e. the Internet. That's all I know about it. :-|

---

### Post by xiaoxin on 2007-01-06
so this info you got from your isp? you have a static address from you isp?

---

### Post by MindDriver on 2007-01-06
Yes, I do. Why?

---

### Post by xiaoxin on 2007-01-06
so in windows there is no problem connecting but in ubuntu you can't connect.
strange, did you install some software from your isp in windows?
maybe they use some kind of authentication or something

---

### Post by MindDriver on 2007-01-06
No, I haven't installed any software from my ISP. :-|

---

### Post by xiaoxin on 2007-01-06
:-k 
i'm running out of ideas here

---

