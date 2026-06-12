---
title: "Ubuntu Firewall Configuration: Gufw"
date: 2009-05-29
forum: New to Ubuntu
---

### Post by Andy06 on 2009-05-29
Blocking all incoming or outgoing traffic via Gufw does not seem to have any effect on Firefox. I can still access any site I want. 

What am I doing wrong?

---

### Post by brian_p on 2009-05-29
> **Andy06 said:**
> 

Blocking all incoming or outgoing traffic via Gufw does not seem to have any effect on Firefox. I can still access any site I want. 

What am I doing wrong?

Please provide the iptables rules which you believe are doing this blocking.

```
sudo iptables -L
```

---

### Post by albinootje on 2009-05-29
> **Andy06 said:**
> Blocking all incoming or outgoing traffic via Gufw does not seem to have any effect on Firefox. I can still access any site I want. 


How did you block all outgoing traffic in gufw ? You need to import a rule for that afaik..
Please post the output of the following :
```

sudo iptables -L -n
sudo iptables -L -t nat

```

---

### Post by ibuclaw on 2009-05-29
> **Andy06 said:**
> Blocking all incoming or outgoing traffic via Gufw does not seem to have any effect on Firefox. I can still access any site I want. 

What am I doing wrong?

(g)ufw only handles **incoming** packets, and when set to "default deny", it only blocks incoming packets that don't have the ACK bit turned on (If the ACK bit is turned on, you requested the packet, ie: accessing a website through firefox).

If you want to block websites, try setting up the DNS Servers your computer uses to one that allows you to control what you can and can't have access to. ie: [http://www.opendns.com/](http://www.opendns.com/)

Or, if you just want to block specific sites, set deny rules in /etc/hosts

Regards
Iain

---

### Post by Andy06 on 2009-05-29
Ok that resolves it. I hadn't imported any rules.

In your recommendations, do you believe using gufw is necessary? And what rules should I be importing?

---

### Post by theDaveTheRave on 2009-06-01
Hi guys

I'm trying to determine what ports a peice of software I am using is sending outbound packets on.

The reason I ask is that the software I downloaded has information saying that I should use specified ports, but I get an error message stating that I need to open other ports on my system.

Before I run off and tell the supplier of the software that there is a problem I would like to be able to confirm the ports that the messages are sent to.

A quick firewalling question.... I guess that there are no blocks on outbound traffic, and firewalls only manipulate inbound trafic?

Am I correct, or am I way off ?

I know it is a silly question, and in my mind I expect to get the answer of "they only prevent inbound communication, who cares what goes out and on what port"

The question then is, how do I manipulate stuff that goes out on port 80 (for arguments sake) to actually send stuff out on port 81 (I'm guessing that I am talking about port forwarding, but again is this inbound only traffic?).

Thanks in advance for the help

David

edit 1.

Ok so I've been reading the stuff on the ubuntu wiki regarding [iptables]("https://help.ubuntu.com/community/IptablesHowTo"), and that cleared up that I can set rules for outbound and inbound ports (as there seem to be "chains" for input, forward and output)

I guess this is for if I use a personal DHCP / LDAP server, and want to restrict what people can "see", eg in my current location I only have access to ports 80 and 25 (or whichever is the "normal" port for ssh), and ports for ftp. Which in general is fine, except in this particular instance!

Again if you could clarify my understanding (as I may be miscomprehending the iptables howto).

Thanks again to everyone...

---

### Post by theDaveTheRave on 2009-06-03
Bump... I really need an answer to this to understand why this isn't working....

for more information...

it is from the [NCBI]("http://www.ncbi.nlm.nih.gov/") web site for [BLAST]("http://blast.ncbi.nlm.nih.gov/Blast.cgi") searches using their download available from [here]("http://blast.ncbi.nlm.nih.gov/Blast.cgi?CMD=Web&PAGE_TYPE=BlastDocs&DOC_TYPE=Download")

It should communicate on port 5860 but I get an error message saying there is a problem on port 4460... and I want to be sure if it is an incorrect error message (new software error messages not updated yet) or if the system really is attempting to communicate on port 4460.


David

---

### Post by albinootje on 2009-06-03
> **theDaveTheRave said:**
> 
I'm trying to determine what ports a peice of software I am using is sending outbound packets on.


Use something like wireshark, iptraf, or tcpdump for this.

---

### Post by theDaveTheRave on 2009-06-04
> **albinootje said:**
> Use something like wireshark, iptraf, or tcpdump for this.

Ah I had forgotten about wireshark... I removed it a long time ago!

I'm going to try something new, so I'll go for iptraf I think.

I've found a good site explaining how it works etc [here]("http://www.taedium.com/rrd-iptraf/")

thanks for that information.

David

---

