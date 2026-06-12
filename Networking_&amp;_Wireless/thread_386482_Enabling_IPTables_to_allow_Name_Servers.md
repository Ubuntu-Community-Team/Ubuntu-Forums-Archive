---
title: "Enabling IPTables to allow Name Servers"
date: 2007-03-17
forum: Networking &amp; Wireless
---

### Post by mikestefff on 2007-03-17
I am configuring iptables for my vps server. Everything is working fine except nameservers. I cannot ping dns's or send mail out. I have the default incoming action set to drop, and all of my other services are configured properly. Initially I just added my names servers from /etc/resolv.conf into the tables and accepted all traffic, but for some reason that no longer works.

I also added udp source/dest port 53 to accept but that doesnt work..

What should I do??

Thanks

---

### Post by mikestefff on 2007-03-17
This doesn't make much sense to me. I also tried to log all incoming packets, and was told they goto /var/log/messages, but they aren't. Would webmin cause them to go else where because I use that to configure the tables?

Any ideas why this isn't working?

Thanks

---

### Post by koenn on 2007-03-17
Explain how your network is layed out. 
eg, iptables distinguishes between rules to and from the machine wher iptables runs (INPUT, OUTPUT rules), and rules for traffic passing through that machine (FORWARD)
so it's important to show what your network looks like, and indicate clearly which machine is doing what.

Also, you may have to post (at least part of) your iptables script, such as the default policies for each CHAIN, the blocking rules, and the rules concerning dns.

---

### Post by mikestefff on 2007-03-17
I have only edited incoming traffic rules. I have done nothing to forwarding or outgoing traffic.

The default policy for incoming is drop. I allow all traffic for web, smtp, 2 admin panels, and my IP for SSH. 

At first I allowed incoming traffic for the nameservers in resolv.conf but they would eventually change and even if they didnt, for some reason it stopped working. 

I tried opening udp/tcp source/dest for 53 - just to try everything..doesn't work either.

When i try to ping a domain (ping yahoo.com) nothing works - it just sits there..

When i tri to send outgoing mail, mail.log says "Name lookup failed"..something like that..

---

### Post by Mr. C. on 2007-03-17
Although your resolver will initiate outbound traffic to resolve queries, the traffic is UDP, and you won't see a TCP connection generally.

Your resolver's queries will be to port 53 of the name server (ie. dest port).  But that nameserver will not send packets back to your port 53!  It will be some random high numbered port.

Its probably time for you to start using tcpdump to learn to capture incoming and outgoing packets, so that you can setup your firewalls properly.

Once captured, you can quickly use a tool like wireshark to see the transactions more easily.

MrC

---

### Post by koenn on 2007-03-17
OK, so it looks like a DNS problem, and possibly has something to do with iptables.
**again : **
> Explain how your network is layed out. It's important to show what your network looks like, and indicate clearly which machine is doing what.
Is this one computer ? two ? if it's more than 1, which one is running the iptables ? are you behind a router ? how do you connect to the internet ?

---

### Post by Mr. C. on 2007-03-17
koenn,

mikestifff is attempting to configure his iptables.  They are mis-configured, and are blocking the incoming response from the resolver's queries.

MrC

---

### Post by koenn on 2007-03-17
> **Mr. C. said:**
> koenn,

mikestifff is attempting to configure his iptables.  They are mis-configured, and are blocking the incoming response from the resolver's queries.

MrC
Yeah, I know. I just find it hard to troubleshoot iptables without seeing the actual ruleset, and reviewing a ruleset for possible errors is also next to impossible without any knowledge of the network layout.

---

### Post by mikestefff on 2007-03-17
I am sorry I misunderstood your question at first..

It is for my VPS server..

Why wouldn't allowing all incoming traffic for the names in resolv.conf just work?

edit: i tried adding a rule on top of the tables to log the traffic so I can see whats coming in when I attempt to ping or something but I cannot find the logs. I thought /var/log/messages was where it should be..

---

### Post by Mr. C. on 2007-03-17
Last I checked, IP tables supports IP addresses, not host names.

The destination of iptables log messages depends upon how syslog is configure (via /etc/syslog.conf).

Here's an explanation:

[http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html](http://www.cyberciti.biz/tips/force-iptables-to-log-messages-to-a-different-log-file.html)

I certainly wouldn't setup a firewall to allow ALL incoming packets from some name server I don't manage!

You can allow incoming UPD port 53 responses to high-numbered ports.

See: [http://oceanpark.com/notes/firewall_example.html](http://oceanpark.com/notes/firewall_example.html) , search for  "DNS queries"

MrC

---

### Post by mikestefff on 2007-03-17
I am beginning to read this article, but need to quickly ask why if I allowed ALL traffic from the dns server, it still wouldn't work?

I am not saying I will leave it that way, but all udp/tcp ports on all ranges are open to it..so how would changing anything make it work?

---

### Post by mikestefff on 2007-03-17
one more thing that I just noticed which is really weird..

i tried this just to test...i added a rule in iptables just to allow ALL udp incoming traffic. didnt work. i removed that and allowed ALL tcp traffic..doesnt work. but if I make the default policy to accept it works..

?

---

### Post by Mr. C. on 2007-03-18
Its difficult to know exactly what the problems are with layers of translation between you, your computer, these forums ,and us out here in helper-land.  Often when we're confused by something, we overlook the obvious, and that translates to those helping as "i tried it... it doesn't work".  I just had a long back and forth with another poster who insisted he/she changed only X.  I accepted the user's interpretation, and overlooked the obvious because of that.  Once I insisted on the data, the problem and solution were plain as day.

So, without seeing your iptables, seeing the transcript of your DNS queries and results, and/or seeing a tcpdump, I have no idea why things are not working as you expect.

MrC

---

### Post by mikestefff on 2007-03-18
this is using tcpdump udp port 53  : (while pinging yahoo.com)

FIREWALL ON:

listening on venet0, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
23:43:50.941044 IP MY_IP_ADDRESS.43406 > resolver2.opendns.com.domain:  44166+ A? yahoo.com. (27)
23:43:50.941700 IP MY_IP_ADDRESS.43410 > resolver2.opendns.com.domain:  43309+ PTR? 220.220.67.208.in-addr.arpa. (45)
23:43:50.988279 IP resolver2.opendns.com.domain > MY_IP_ADDRESS.43406:  44166 2/0/0 A w2.rc.vip.scd.yahoo.com, (59)
23:43:50.988663 IP resolver2.opendns.com.domain > MY_IP_ADDRESS.43410:  43309 1/0/0 (80)
23:43:50.988867 IP MY_IP_ADDRESS.43413 > resolver2.opendns.com.domain:  33127+ PTR? 40.86.126.75.in-addr.arpa. (43)
23:43:51.038633 IP resolver2.opendns.com.domain > MY_IP_ADDRESS.43413:  33127 1/0/0 (98)
23:43:51.038920 IP MY_IP_ADDRESS.43413 > resolver2.opendns.com.domain:  4608+ PTR? 13.234.94.66.in-addr.arpa. (43)
23:43:51.085730 IP resolver2.opendns.com.domain > MY_IP_ADDRESS.43413:  4608 1/0/0 (80)


=======
FIREWALL OFF AND ACCEPTING ALL:


listening on venet0, link-type LINUX_SLL (Linux cooked), capture size 96 bytes
23:46:19.017209 IP MY_IP_ADDRESS.43669 > resolver2.opendns.com.domain:  57881+ A? yahoo.com. (27)
23:46:19.017943 IP MY_IP_ADDRESS.43672 > resolver2.opendns.com.domain:  57792+ PTR? 220.220.67.208.in-addr.arpa. (45)
23:46:19.063882 IP resolver2.opendns.com.domain > MY_IP_ADDRESS.43669:  57881 2/0/0 A w2.rc.vip.scd.yahoo.com, (59)
23:46:19.065009 IP resolver2.opendns.com.domain > MY_IP_ADDRESS.43672:  57792 1/0/0 (80)
23:46:19.065227 IP MY_IP_ADDRESS.43674 > resolver2.opendns.com.domain:  16524+ PTR? 40.86.126.75.in-addr.arpa. (43)
23:46:19.115230 IP resolver2.opendns.com.domain > MY_IP_ADDRESS.43674:  16524 1/0/0 (98)
23:46:19.115523 IP MY_IP_ADDRESS.43674 > resolver2.opendns.com.domain:  9773+ PTR? 13.234.94.66.in-addr.arpa. (43)
23:46:19.141459 IP MY_IP_ADDRESS.43676 > resolver2.opendns.com.domain:  15362+ PTR? 13.234.94.66.in-addr.arpa. (43)
23:46:19.162327 IP resolver2.opendns.com.domain > MY_IP_ADDRESS.43674:  9773 1/0/0 (80)
23:46:19.189563 IP resolver2.opendns.com.domain > MY_IP_ADDRESS.43676:  15362 1/0/0 (80)
23:46:20.144265 IP MY_IP_ADDRESS.43679 > resolver2.opendns.com.domain:  28504+ PTR? 13.234.94.66.in-addr.arpa. (43)
23:46:20.191141 IP resolver2.opendns.com.domain > MY_IP_ADDRESS.43679:  28504 1/0/0 (80)


while the firewall was on my first line for incoming traffic was to accept ALL udp traffic..still doesnt work tho..?

---

### Post by mikestefff on 2007-03-18
i opened up all allowed for imcp protocol and it seems to work finally...

i used wireshark locally and saw it being used for ping request and replies..

why didnt the 15 articles, 2 forums, and irc mention that?

---

### Post by koenn on 2007-03-18
> **mikestefff said:**
> i opened up all allowed for imcp protocol and it seems to work finally...
i used wireshark locally and saw it being used for ping request and replies..


As you found out : "ping" uses imcp protocol, which is neither tcp nor udp, so "drop all + allow tcp and udp" would still block your pings.

> 
why didnt the 15 articles, 2 forums, and irc mention that
sometimes you have to ask the right question to get a useful answer. And articles usually cover 1 aspect of networking and assume the reader will know (or find out) the rest elsewhere. If I were to write something about DNS and iptables, I doubt that I'd mention IMCP if it wasn't relevant in the context of the article.

---

### Post by koenn on 2007-03-18
I'm still having trouble understanding your setup. 
this vps is a virtual private server, right ? 
After reading all the posts again, I now _assume_ it's hosted elsewhere, not something you're tinkering with at home ? 
I also _assume_ the problems you're describing are** on** that vps, and not on some other computer trying to connect to it ? And that the iptables is also running **on** the vps. 

I have no experience with tcpdump, but to me it looks as if you* do *get replies to your dns queries, both in the  : 
```
23:43:50.941044 IP MY_IP_ADDRESS.43406 > resolver2.opendns.com.domain: 44166+ A? yahoo.com. (27)
23:43:50.988279 IP resolver2.opendns.com.domain > MY_IP_ADDRESS.43406: 44166 2/0/0 A w2.rc.vip.scd.yahoo.com, (59)

23:43:50.941700 IP MY_IP_ADDRESS.43410 > resolver2.opendns.com.domain: 43309+ PTR? 220.220.67.208.in-addr.arpa. (45)
23:43:50.988663 IP resolver2.opendns.com.domain > MY_IP_ADDRESS.43410: 43309 1/0/0 (80
```

run this, it's a dns lookup - and post the output so we can see what's happening
```
dig www.google.com
```

---

### Post by mikestefff on 2007-03-18
> If I were to write something about DNS and iptables, I doubt that I'd mention IMCP if it wasn't relevant in the context of the article.

How would it not be relevant if its what it needed to work? I couldn't send or receive mail either until I did this...

Yes it is on a VPS, not in my home, hosted by a company.

Yes, I noticed I was receiving some responses from tcpdump even when the pings werent working. Thought it was weird so I used wireshark on my local machine. 

And I don't know how i left anything out in this post. I asked what is needed in IPtables to get ping and dns lookups to work. On top of udp 53 i needed imcp open as well.

---

### Post by koenn on 2007-03-18
> **mikestefff said:**
> How would it not be relevant if its what it needed to work? I couldn't send or receive mail either until I did this...

dns and email don't require ICMP. 
(and if your server does require icmp to send/receive mail or do dns lookups, there is something very peculiar about that server that is not obvious from the info you've given so far)

In that respect : 
> **Mr. C. said:**
> Its difficult to know exactly what the problems are with layers of translation between you, your computer, these forums ,and us out here in helper-land.   ...  Once I insisted on the data, the problem and solution were plain as day. 

I'm not in the mood to argue about this. (That's what [http://ubuntuforums.org/showthread.php?t=378855](http://ubuntuforums.org/showthread.php?t=378855) is for). 
I happen to be one of those people that require concrete data in order to diagnose a problem, so maybe I'm not the right person to be offering help in this particular thread.

---

### Post by Mr. C. on 2007-03-18
Mikestiff,

I entirely agree with koenn; there is some level of basic knowledge and understanding that must be assumed.  Networking is complex, and in my opinion, requires having a solid grasp of the fundamentals before moving to more complex tasks.  I would assume anyone trying to build a firewall via iptables understands the basics of icmp, arp, high-numbered ports, etc.  Too many people are looking for a "cookbook", and this approach is inevitably doomed.

Koenn - I'm confused by your previous post.  It sounds to me like we both require data, not users' interpretations.  What is there to argue about?

MrC

---

### Post by koenn on 2007-03-18
> **Mr. C. said:**
> 
Koenn - I'm confused by your previous post.  It sounds to me like we both require data, not users' interpretations.  What is there to argue about?


No worries, Mr. C; 
We both require data, and i quoted you to indicate I wasn't the only one asking for them. So the quote is related to the lack of info, not to the "I'm not in the mood to argue about this" part. The latter was just to tell the OP I wasn't about to argue about whether or not he should provide more info. If he does, I'll look at it, and if I can help to diagnose or troubleshoot, I will. If I he doesn't, well, it's his loss. 

Hope that clarifies it.

---

### Post by Mr. C. on 2007-03-18
Indeed.  Thanks for taking the time to clarify.

Cheers,
MrC

---

### Post by mikestefff on 2007-03-18
I understand what you guys are saying..no one is arguing..I was just trying to understand something. I appreciate your guys help more than anything. Your all great..

Thank you..

---

### Post by Mr. C. on 2007-03-18
It sounds like we're all on the same page.

Mikestiff - you seem to be very interested in learning all about networking, server administration, etc.  Can I recommend a good TCP/IP book ?  "Internetworking with TCP/IP" by Comer.  It will give you a solid foundation for understanding some of the tasks you are trying to accomplish.  Iptables will be a breeze after that.

MrC

---

