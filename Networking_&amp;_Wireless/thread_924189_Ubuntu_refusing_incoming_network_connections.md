---
title: "Ubuntu refusing incoming network connections"
date: 2008-09-19
forum: Networking &amp; Wireless
---

### Post by MatthewHSE on 2008-09-19
I had a Feisty installation, but managed to destroy it during an upgrade so I started fresh with Hardy.  I'm having difficulty getting it to work like I had the previous install working.

I want to use this computer as a LAN proxy using Dansguardian and TinyProxy.  The problem is that Hardy appears to be refusing all incoming network connections.  I can't ping it, connect to remote desktop, or use the proxy from other computers on the LAN.  These are all things that worked perfectly on my last installation.

I've trawled around the system settings, etc., but can't find anything obvious.  All I can think of at this point is a software firewall that needs to be configured differently, but I can't find any firewall on this installation.

At this point I'm out of ideas of what more to check.  What should I be looking for to resolve these issues?

Thanks in advance for any ideas,

Matthew

---

### Post by caljohnsmith on 2008-09-19
First, are you sure Dansguardian and Tinyproxy are running? Try something like this to find out:
```
ps axu | grep -ie dan -ie tiny
```
If it shows they are running, next try:
```
sudo netstat -tlpu 
```
That should show the open TCP/UDP ports on your computer. Do you know which TCP port you have set up in Dansguardian/Tinyproxy to receive proxy requests? 

That should give you some place to start; let me know how it goes.

---

### Post by MatthewHSE on 2008-09-19
Thanks for the quick reply!

I checked and Dansguardian and Tinyproxy are both running.  Netstat showed Tinyproxy listening on port 3128, which is correct. Dansguardian was listening on something called "webcache", but I have it configured to listen on port 8080. So that could potentially be a problem.

However, I think the problem is with something other than the Dansguardian/Tinyproxy setup. I can't ping this computer, connect to remote desktop, etc. Basically the rest of the network doesn't seem to know this computer exists (although I *can* ping other computers from this computer).  To me, that indicates a problem at a higher level than the proxy setup, such as a firewall. Or am I wrong on that?

---

### Post by caljohnsmith on 2008-09-19
If that netstat command shows your port 3128 is open, I'm pretty sure your port 3128 should actually be open and not blocked by a higher level firewall on your computer. But it sounds like there must be something else going on, since your other computers don't seem to see your Ubuntu computer. You said you could ping the other computers on your LAN from the Ubuntu computer, but can your Ubuntu computer access the internet OK? 

Here's another useful command that may tell us what is going on:
```
sudo iptables -L
```
That lists all your iptable rules, so that should show if a firewall is getting in the way.

---

### Post by MatthewHSE on 2008-09-20
> **caljohnsmith said:**
> You said you could ping the other computers on your LAN from the Ubuntu computer, but can your Ubuntu computer access the internet OK?Yes, I can get online from here using the same router the rest of the computers on our LAN use.  I can also ping the other computers on the network, and they can ping one another, but none of them can ping me or reach me in any way.

> **caljohnsmith said:**
> Here's another useful command that may tell us what is going on:
```
sudo iptables -L
```
That lists all your iptable rules, so that should show if a firewall is getting in the way.I ran that command but couldn't make head nor tails out of it. What am I looking for in there?

---

### Post by caljohnsmith on 2008-09-20
How about just posting the output of that iptables command so I can see what it looks like? Then it will be much easier to explain whatever you have.

---

### Post by MatthewHSE on 2008-09-20
> **caljohnsmith said:**
> How about just posting the output of that iptables command so I can see what it looks like? Then it will be much easier to explain whatever you have.

Good idea:

Chain INPUT (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
in_world   all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'IN-unknown:''
DROP       all  --  anywhere             anywhere

Chain FORWARD (policy DROP)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state RELATED
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'PASS-unknown:''
DROP       all  --  anywhere             anywhere

Chain OUTPUT (policy DROP)
target     prot opt source               destination
DROP       tcp  --  anywhere             localhost           tcp dpt:3128 ! OWNER UID match dansguardian
ACCEPT     all  --  anywhere             anywhere
out_world  all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'OUT-unknown:''
DROP       all  --  anywhere             anywhere

Chain in_world (1 references)
target     prot opt source               destination
DROP       all  --  anywhere             anywhere            state INVALID
pr_world_fragments  all  -f  anywhere             anywhere
pr_world_nosyn  tcp  --  anywhere             anywhere            state NEW tcp flags:!FIN,SYN,RST,ACK/SYN
pr_world_icmpflood  icmp --  anywhere             anywhere            icmp echo-request
pr_world_synflood  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,ACK/SYN
pr_world_malxmas  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,PSH,ACK,URG
pr_world_malnull  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/NONE
pr_world_malbad  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN/FIN,SYN
pr_world_malbad  tcp  --  anywhere             anywhere            tcp flags:SYN,RST/SYN,RST
pr_world_malbad  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,SYN,RST,ACK,URG
pr_world_malbad  tcp  --  anywhere             anywhere            tcp flags:FIN,SYN,RST,PSH,ACK,URG/FIN,PSH,URG
in_world_all_c1  all  --  anywhere             anywhere
in_world_irc_c2  all  --  anywhere             anywhere
in_world_ftp_c3  all  --  anywhere             anywhere
in_world_cups_s4  all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `''IN-world':''
DROP       all  --  anywhere             anywhere

Chain in_world_all_c1 (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state ESTABLISHED

Chain in_world_cups_s4 (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpt:ipp state NEW,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ipp dpt:ipp state NEW,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            udp spts:1024:65535 dpt:ipp state NEW,ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            udp spt:ipp dpt:ipp state NEW,ESTABLISHED

Chain in_world_ftp_c3 (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ftp dpts:32768:61000 state ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ftp-data dpts:32768:61000 state RELATED,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:1024:65535 dpts:32768:61000 state ESTABLISHED

Chain in_world_irc_c2 (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ircd dpts:32768:61000 state ESTABLISHED

Chain out_world (1 references)
target     prot opt source               destination
out_world_all_c1  all  --  anywhere             anywhere
out_world_irc_c2  all  --  anywhere             anywhere
out_world_ftp_c3  all  --  anywhere             anywhere
out_world_cups_s4  all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `''OUT-world':''
DROP       all  --  anywhere             anywhere

Chain out_world_all_c1 (1 references)
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere            state NEW,ESTABLISHED

Chain out_world_cups_s4 (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ipp dpts:1024:65535 state ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp spt:ipp dpt:ipp state ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            udp spt:ipp dpts:1024:65535 state ESTABLISHED
ACCEPT     udp  --  anywhere             anywhere            udp spt:ipp dpt:ipp state ESTABLISHED

Chain out_world_ftp_c3 (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:32768:61000 dpt:ftp state NEW,ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:32768:61000 dpt:ftp-data state ESTABLISHED
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:32768:61000 dpts:1024:65535 state RELATED,ESTABLISHED

Chain out_world_irc_c2 (1 references)
target     prot opt source               destination
ACCEPT     tcp  --  anywhere             anywhere            tcp spts:32768:61000 dpt:ircd state NEW,ESTABLISHED

Chain pr_world_fragments (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'PACKET FRAGMENTS:''
DROP       all  --  anywhere             anywhere

Chain pr_world_icmpflood (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere            limit: avg 100/sec burst 50
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'ICMP FLOOD:''
DROP       all  --  anywhere             anywhere

Chain pr_world_malbad (4 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'MALFORMED BAD:''
DROP       all  --  anywhere             anywhere

Chain pr_world_malnull (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'MALFORMED NULL:''
DROP       all  --  anywhere             anywhere

Chain pr_world_malxmas (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'MALFORMED XMAS:''
DROP       all  --  anywhere             anywhere

Chain pr_world_nosyn (1 references)
target     prot opt source               destination
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'NEW TCP w/o SYN:''
DROP       all  --  anywhere             anywhere

Chain pr_world_synflood (1 references)
target     prot opt source               destination
RETURN     all  --  anywhere             anywhere            limit: avg 100/sec burst 50
LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'SYN FLOOD:''
DROP       all  --  anywhere             anywhere

---

### Post by caljohnsmith on 2008-09-21
> **MatthewHSE said:**
> 
```
[COLOR="Red"]Chain INPUT (policy DROP)[/COLOR]
target     prot opt source               destination
ACCEPT     all  --  anywhere             anywhere
in_world   all  --  anywhere             anywhere
ACCEPT     all  --  anywhere             anywhere            state RELATED
[COLOR="Red"]LOG        all  --  anywhere             anywhere            limit: avg 1/sec burst 5 LOG level warning prefix `'IN-unknown:''
DROP       all  --  anywhere             anywhere[/COLOR]
```

One thing that is good about your iptables is that you have the "log" rule set, so all dropped incoming networking requests should be logged with "dmesg" if I'm not mistaken. I would try this: first go to one of your other computers and try (unsuccessfully) to use your Ubuntu proxy, and also ping your Ubuntu computer, and then on your Ubuntu computer do:
```
dmesg | less
```
And I think it will show messages about the dropped incoming networking requests from your other computers (i.e. proxy and ping requests). 

The other thing I'm concerned about is the line above:
```
DROP       all  --  anywhere             anywhere
```
According to the iptables manual, the rules in your iptables are used in order, so the first rule you have:
```
ACCEPT     all  --  anywhere             anywhere
```
Should mean that all incoming requests are accepted, and thus it supersedes the later "drop" rule you have (at least I think so, as I'm not an iptables expert). Also above your "INPUT" policy is set to defualt to "policy DROP" it looks like, and again, I don't use iptables much so I'm not sure if that then supersedes the "ACCEPT" rule that is first in that list. 

But bottom line is you have a quite complicated iptables at this point, which has to be due to some firewall software that is installed. Do you maybe have "firestarter" installed? Finding which firewall software is creating all those rules is the issue here I think.

---

### Post by MatthewHSE on 2008-09-21
> **caljohnsmith said:**
> But bottom line is you have a quite complicated iptables at this point, which has to be due to some firewall software that is installed. Do you maybe have "firestarter" installed? Finding which firewall software is creating all those rules is the issue here I think.

I didn't know it, but it turns out that I had Firehol installed. Looks like its configuration file is the trouble:

```
iptables -t filter -I OUTPUT -d 127.0.0.1 -p tcp --dport 3128 -m owner ! --uid-owner dansguardian -j DROP

transparent_squid 8080 "root root"

interface any world
policy drop
protection strong
client all accept
server cups accept
#server webcache accept
#
# $Id: client-all.conf,v 1.2 2002/12/31 15:44:34 ktsaou Exp $
#
# This configuration file will allow all requests originating from the
# local machine to be send through all network interfaces.
#
# No requests are allowed to come from the network. The host will be
# completely stealthed! It will not respond to anything, and it will
# not be pingable, although it will be able to originate anything
# (even pings to other hosts).
#

version 5

# Accept all client traffic on any interface
	#client all accept
```

That section of comments in the middle is pretty explicit about not allowing incoming connections.  So it looks like this file has the key, although I'm not sure yet what I need to change.

---

### Post by caljohnsmith on 2008-09-21
OK, looks like you found the root of the problem then since you have Firehol installed. :) I really have no experience with Firehol, so I don't think I can be of much help, although its configuration file doesn't look too complicated. Have you tried "man firehol" to see what its man page says? That's probably a good place to start, or maybe there's a help guide on the internet for it.

Personally though, I would simply uninstall Firehol. You mentioned you are on a LAN, meaning you must be using some sort of router, is that true? If it is, your router is your firewall, because your router uses network address translation (NAT) to share the single internet connection with your LAN; NAT by its very nature acts like a firewall. Let me know how it goes or what you decide to do.

---

### Post by MatthewHSE on 2008-09-22
Yes, I'm behind a NAT router and a hardware firewall, so you're right, the software firewall shouldn't be necessary. I uninstalled Firehol and everything is working well now, except that I can't get Ubuntu to remember my nameservers. But, that's another topic for [another thread](http://ubuntuforums.org/showthread.php?t=926766)! ;)

Sorry for giving you the royal runaround on this.  I could have fixed it myself if I'd realized Firehol was installed.  I really do know computers and networking fairly well, but I still don't know much about Linux.  Probably Firehol was bundled with something else and I didn't realize it. Anyway, thanks again for all your help, at least I learned some useful commands through this! :)

---

### Post by caljohnsmith on 2008-09-22
> **MatthewHSE said:**
> 
Sorry for giving you the royal runaround on this.  I could have fixed it myself if I'd realized Firehol was installed.  I really do know computers and networking fairly well, but I still don't know much about Linux.  Probably Firehol was bundled with something else and I didn't realize it. Anyway, thanks again for all your help, at least I learned some useful commands through this! :)
You're welcome, and believe me, compared to some of the responses I get when I sincerely try and help, you hardly gave me the "royal runaround". 

And yes, Linux has a steep learning curve I think because you really do have to learn a lot of commands to accomplish some things, since not everything can be done with a GUI. If you haven't done so, I might suggest keeping your own Linux command "cheat sheet"; whenever I come across a useful command, that's where I put it. For instance, I knew I had a netstat command to show the open ports on the computer, but I certainly haven't committed to memory all the necessary options for that command (-tlpu) to make it happen. :)

Anyway, hope you get your other DNS issue resolved. Cheers and have fun. :)

---

