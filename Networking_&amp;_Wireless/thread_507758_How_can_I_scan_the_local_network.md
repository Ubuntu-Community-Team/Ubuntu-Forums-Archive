---
title: "How can I scan the local network?"
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by derbaschti on 2007-07-23
Hi,

I have the following rather unusual problem:

We are a small research group in a University Institute. We are all running Ubuntu and are heaviliy dependent on Internet and local network bandwitdh. Since we are chemists, we don't administrate the network ourselves, but leave that to the IT-Center of the University.

Since a few days, we have only ridiculously small bandwith when connecting to the internet. Several calls to the IT-Center later, they came up with the explanation, that one of our computers is configured badly, and sending out rubbish packets eating up our bandwith. But they could't tell us, which IP or host the packets originate from, so I suspect that they actually have no clue and try to shove the problem back to us.

Can anybody suggest an approach toI can check their theory? If there actually is a computer malfunctioning,  it would also be great to find out which one...

All PCs in question are in the same IP-range (like 124.456.78.*). 

Thanks for any help,

Sebastian

---

### Post by jrusso2 on 2007-07-23
use some type of packet sniffer to find it.  Once such sniffer is wireshark or ethereal.  The IT dept should be able to do this.

---

### Post by t4thfavor on 2007-07-23
Use wireshark, or tcpdump to capture packets on the lan. The problem is that if you are on a switched network, you will not be able(ethically) to see all packets. You may be able to attach a regular hub to the uplink port on your switch, and then sniff that way. I would say you are better off calling your boss and having him/her light a fire under IT so they get on the problem.

---

### Post by derbaschti on 2007-07-23
> **jrusso2 said:**
> use some type of packet sniffer to find it.  Once such sniffer is wireshark or ethereal.  

Great, I will try that..

> **jrusso2 said:**
>  The IT dept should be able to do this.

That's exactly what I was telling my boss... However, since he is a bit over-cautious he would prefer some facts...

---

### Post by t4thfavor on 2007-07-23
First of all IT is the laziest group of people on the planet, If you do not keep on them it will never get done.  Your boss should call their boss and tell them you have a busted network and he needs to get it fixed. It is not your responsability to diagnose network trouble. It is however your job to use the network to do chemistry stuff. And the fact that the network is not working correctly means that you cannot effectively do your job. 

That should be enough to get the ball rolling on your issue.

---

### Post by Mr. C. on 2007-07-24
Most larger institutions have managed switches.  In this case, you will not be able to sniff the network as a whole, since you will only have access to your switchport's traffic.

Managed switches have the ability to generate bandwidth usage, errors, etc. per switchport.  Identifying the network and the exact switchport is not difficult, but will require the switch administrator privileges, ability to connect to its LAN interface, and the know how to do diagnose.  You will have to work with the IT department.

Start by providing them with some bandwidth usage charts during the problematic periods.

MrC

---

### Post by derbaschti on 2007-07-24
> **Mr. C. said:**
> 
Start by providing them with some bandwidth usage charts during the problematic periods.

MrC

Good idea! How can I generate these?

---

### Post by quinnten83 on 2007-07-24
> **t4thfavor said:**
> First of all IT is the laziest group of people on the planet, If you do not keep on them it will never get done.  Your boss should call their boss and tell them you have a busted network and he needs to get it fixed. It is not your responsability to diagnose network trouble. It is however your job to use the network to do chemistry stuff. And the fact that the network is not working correctly means that you cannot effectively do your job. 

That should be enough to get the ball rolling on your issue.

you know, As an It person I am insulted by this reply.
people tend to forget that an It department has layers of people with layers of knowledge and that IT is a ridicoulsy broad spectrum.
Since the computers being used are Ubuntu, maybe there just isn't a linux expert nearby, since most knowledge is of windows systems.
Perhaps the IT dept. doesn't even administer the actual physical network but outsources it. There are all sorts of things that make the IT jobs be delayed. It is not like we don't try, but the job is much more complex than those not in the know can even imagine or actually care to.
Having said that. I have no idea what causes the issues with the network. I suppose it is not possible to remove one computer at a atime to monitor the network. I would suggest asking the IT dept. or anybody who manages the physical network to send someone for a week to try and test this by leaving one computer of the network at  a time.

---

### Post by Mr. C. on 2007-07-24
I would just perform some period downloads of a known file size from a remote FTP server, say every 15 minutes, to get a running average of download speeds.  You can use wget or curl.  Alternatively, run a speed test from one of the many speed test applets available on the net (pick the closest one to your location).  Graph the results.

This is a crude estimate at best, and of course, uses the very bandwidth you and other's are competing for, but it is better than a poke with a stick, and may be sufficient to catch someone's attention more than a simple "our downloads are slow".

MrC

---

### Post by Mr. C. on 2007-07-24
> **quinnten83 said:**
> you know, As an It person I am insulted by this reply.

t4thfavor's response is troll-bait.  Just ignore it and drive through.

MrC

---

### Post by quinnten83 on 2007-07-24
> **Mr. C. said:**
> t4thfavor's response is troll-bait.  Just ignore it and drive through.

MrC

Yeah, I know.
I just keep getting the same crap at work (all the several companies I've been outsourced to) and this really got to me, since the Ubuntu forums have up to this point been a bastion of understanding and sympathy.
finding my zen, moving on..

---

### Post by derbaschti on 2007-07-24
Hey you all, thanks for all the answers. They were really encouraging...

Although I would say I am no noob and have a quite some experience with PCs, I still am somebody who just USES a computer for work... Sometimes you are really lost with all the complexity of network and hardware administration... 

So - as a short response to t4thfavor - there must be quite a lot of  IT-people who know their job, but obviously mine are a bit lazy...

By the way: The IT-Center of our University actively promotes the use of Linux, so for instance all client PCs in the library and so forth run SUSE. So I think there is enough Linux-Knowledge...

---

### Post by Mr. C. on 2007-07-24
> **quinnten83 said:**
> Yeah, I know.
I just keep getting the same crap at work (all the several companies I've been outsourced to) and this really got to me, since the Ubuntu forums have up to this point been a bastion of understanding and sympathy.
finding my zen, moving on..

It's the nature of being in the service industry: thanks are rare, problems always your fault.  You have to possess a constitution that thrives on serving others; any thanks and kudos are just bonuses.

Enjoy serving,
MrC

---

### Post by doodaa on 2007-07-24
Ask your IT folks the name or IP address of this alleged misconfigured computer so you can unplug it while it's fixed. If your bandwidth doesn't come back it wasn't that one. Start unplugging computers until you find the culprit - if there really is one.

---

