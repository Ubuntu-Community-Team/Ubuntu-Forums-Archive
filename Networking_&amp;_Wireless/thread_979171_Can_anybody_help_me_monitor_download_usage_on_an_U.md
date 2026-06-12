---
title: "Can anybody help me monitor download usage on an Ubuntu Router"
date: 2008-11-11
forum: Networking &amp; Wireless
---

### Post by destructogus on 2008-11-11
Does anybody know of a good program that will monitor the volume of traffic passing through my Ubuntu Router?  One (or more) of my housemates is hogging our download quota, and we're getting shaped  earlier and earlier each month.

my network topology looks like this.

```

Internet
    |
Adsl modem/router
    |192.168.0.x
 PC Router
    |192.168.1.x
  Switch
    |
  -----------------------
  |                      |
Wired Computers     Wireless Access Point 

PC Router: 
 - Ubuntu 8.04 Server 
 - eth0 is internet facing
 - eth1 is home network facing
 - PC is set up to just forward everything
 - Followed _[this guide]("http://ge.ubuntuforums.com/showthread.php?t=926001")_

```
So, ideally, what I want is some way to monitor how much each person in the Wired/Wiress network is downloading from the internet.

Does anybody know of a program that can give me download statistics (current rate of transfer, total downloaded by day/month etc) of traffic going through eth0 on a PER USER basis? Either by IP, MAC or ideally by resolved hostname.  Information can be terminal based, but it'd be nice to have pretty graphs and what not.

Thanks,
Sam

---

### Post by cariboo on 2008-11-11
There a lot of tools listed here:

[http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html](http://www.ubuntugeek.com/bandwidth-monitoring-tools-for-linux.html)

I know the one time I tried bandwidth monitoring with Webmin, it created huge log files.

Jim

---

### Post by maxhax on 2008-11-11
Alright destructogus, I have some ideas for you.  I've had roommates before, so I feel your pain...they don't know how to be mindful of a NAT'd connection so you basically need to locate the usage and throttle it or just them in general.  So here are my ideas for you.

I looked at the tutorial you followed, and I'd just say it'd be easier to learn IPtables.  There used to be a great RedHat press book about IPtables based firewalls.  It's out of print now, but you can still find it...I doubt someone telling you to learn IPtables is hardly what you wanted to hear, but what you will find is that you can identify the traffic the hog generates and throttle it back.  It would take some time to learn their traffic patterns, but you could easily shell a tcpdump session that grabs just their SYN packets out to a file...that would be a lot better than look at ACKs for a week. So I haven't provided any code here because I have gotten away from IPtables all together; which leads me to my next point.

You don't have to justify it to me, so this is a rhetorical question...is there a specific reason to be running Ubuntu here?  I noticed that you were running the server version, so I know you're not using it as a desktop unless you are running a headless virtual server, and RDP'ing up to it. 

The only reason I ask is because about 4 years ago I moved away from IPtables.  The first time I used them I thought they were the best thing since base 2, but I found there are other options that are much better and can definitely solve your problem without a tool or script.  

The OS is OpenBSD and the firewall is PacketFilter.  I know this is an Ubuntu forum, and I wouldn't normally steer anyone away from Ubuntu, but in this case, I'm not sure it's the best tool.  In just a few lines [/etc/pf.conf] you can have everything setup to nat and label all traffic coming from the hog, without needing some other tool.  It's just a suggestion if your Ubuntu server is just pushing packets. PF can do the throttling for you too.  One other thing that made me a believer is the syntax of the pf.conf script.  You can write out one line that expands to many lines.  In IPtables you used to have to do this one by one, which was a pain.  

So if Ubuntu has to stay and you have the resources, consider this.  Virtualbox has host based interfaces aka bridging.  You might be able to leave Ubuntu as is, setup Virtualbox with an oBSD guest, do the host based interface thing and roll out a virtual machine firewall.  I've never done this before so I don't fully know if it would work, but I have a hunch it could be made to work.  Virtualbox will do up to 4 virtual interfaces which is enough for your setup.  The internal bridge would need to take on a static IP with the actual interface taking on something off dhcp, and on the outside bridge an IP  off your modem/router via dhcp.  This is just an idea, and might be a sinker if you're just looking to get something running.  

I will say that I wrote a script for PF to log my total interface traffic.  Since Comcast implemented a 250G per month limit, I wanted to know how much I've been using.  In a few lines I had it done and logging every day at midnight to a file.  Well, read over this and think about it.  Let us know if you need any help.  

-maxhax-

---

### Post by iponeverything on 2008-11-11
on "PC Router"

```
iptables -N users
iptables -A INPUT -s 0/0 -j users
iptables -A INPUT -d 0/0 -j users
```


add all the IP address with:
```
iptables -A users -s <ipaddress> ; iptables -A users -d <ipaddress>

```
then check usage with:
```
iptable -L -v
```

---

### Post by destructogus on 2008-11-12
Wow.. a lot of replies so quickly :D

Thanks for your help.

To clarify, what I was after wasn't so much a *bandwidth monitor*, but rather a *traffic counter*.  Sorry about the confusion, I only figured that out after trawling through more forums.

cariboo907: Thanks for the list of bandwidth monitor stuffs, was a good spring board for more googling. 

maxhax: ...wow..  Yeah, I kinda wanted an out-of-the-box solution, because i'm pretty sure that this is not an uncommon problem.  IPTables might be interesting (maybe fun?) to learn later, but it's probably a bit too involved for what i want to do.  Oh, and I chose Ubuntu probably because it's marketed as the easy/accessible flavor of linux?

Anyway, I ended up using Bandwidthd and Ntop.  They seemed to install fine.. so we'll see how we go.  I'll run a few tests tonight to see if everything is working as expected.

Thanks for your help agian

---

