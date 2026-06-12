---
title: "Firestarter doesn't start automatically"
date: 2007-06-20
forum: Networking &amp; Wireless
---

### Post by cocotte on 2007-06-20
Hello,

Firestarter doesn't start at boot time : 

root@snoopy:~# /etc/init.d/firestarter status
 * Firestarter is stopped

GNOME sets up the connection when I log in. I have checked all startup ootions in Firestarter

Any idea ?

---

### Post by dreadlord_chris on 2007-06-20
> **cocotte said:**
> Hello,

Firestarter doesn't start at boot time : 

root@snoopy:~# /etc/init.d/firestarter status
 * Firestarter is stopped

GNOME sets up the connection when I log in. I have checked all startup ootions in Firestarter

Any idea ?
If you haven't already, I think you should remove that entry you made to the **sodoers** file earlier....

**EDIT**
Actually, I think there's something you are not quite understanding - and it's a common misconception. Firestarter is **not** your firewall - it is mearly the configuration interface to your firewall. Your firewall, a function of **iptables** by the way, is part of your kernel - and is running by default in Ubuntu. Configuring iptables by hand can be a daunting task - even for seasoned Linux users - hence the various *front-ends* (firestarter/guarddog/etc).
Now, there are basically 2 parts to **firestarter**: there's the *init* script that gets run at boot - what it does is initialize **iptables** (your firewall, remember?) with the rules and policies that are configured thru the second part - the GUI (the part everybody mistakes for their firewall). The boot script does not actually run firestarter (the GUI), it just loads your firewall rules into iptables.

---

### Post by cocotte on 2007-06-21
> **dreadlord_chris said:**
> If you haven't already, I think you should remove that entry you made to the **sodoers** file earlier....

I had done it but as you said, I don't really understand how the firewall works. How can I be sure that iptables has been utpdated ? I think that it should exist a log file somewhere ?

---

### Post by cocotte on 2007-06-21
I think iptables isn't set at boot time because my ports should be filtered and not closed :

benoit@snoopy:~$ nmap snoopy

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-06-21 10:03 CEST
All 1697 scanned ports on snoopy (127.0.1.1) are closed

Nmap finished: 1 IP address (1 host up) scanned in 0.158 seconds

---

### Post by dreadlord_chris on 2007-06-21
> **cocotte said:**
> I think iptables isn't set at boot time because my ports should be filtered and not closed :

benoit@snoopy:~$ nmap snoopy

Starting Nmap 4.20 ( [http://insecure.org](http://insecure.org) ) at 2007-06-21 10:03 CEST
All 1697 scanned ports on snoopy (127.0.1.1) are closed

Nmap finished: 1 IP address (1 host up) scanned in 0.158 seconds

looks to me like it is.... Why do you think your ports should be filtered and not closed?

if you want to see the contents of your firewall:
```

sudo iptables -L

```
but, unless you've actually defined some rules - it's likely to be empty

I would suggest you do some reading up on iptables: [http://blog.2blocksaway.com/2007/01/03/iptables-explained-get-started-with-iptables-and-tame-the-monster-of-all-firewalls/]("http://blog.2blocksaway.com/2007/01/03/iptables-explained-get-started-with-iptables-and-tame-the-monster-of-all-firewalls/")

---

### Post by cocotte on 2007-06-21
It's in the man page of nmap. Ports controlled by a firewall should be filtred.

If a port is closed, there is no service behind but the system responds to request. If a port is filtred the system doesn't respond to request on this port therefore the port is invisible.

---

### Post by dmizer on 2007-06-21
here's your bug with a workaround posted:

google search returned this result on "firestarter does not load on boot"

[https://bugs.launchpad.net/debian/+source/firestarter/+bug/42759](https://bugs.launchpad.net/debian/+source/firestarter/+bug/42759)

---

### Post by dreadlord_chris on 2007-06-21
> **cocotte said:**
> It's in the man page of nmap. Ports controlled by a firewall should be filtred.

If a port is closed, there is no service behind but the system responds to request. If a port is filtred the system doesn't respond to request on this port therefore the port is invisible.

first off - not all firewalls filter ports. IPtables can be configured to filter - but it takes a bit of setting up.
Also, not all firewalls filter in the same way - some will simply **drop** the packet (true stealth -the sender receives no reply) - others firewalls will send a **tcp-reset** (which is *supposed* to mean the address is invalid).

Either of these methods works great - as long as it's the only port that is scanned or attacked. The purpose behind stealthing/filtering your ports is to make your computer *appear* invisible - the problem lies in the fact that a networked computer **must** have at least some ports open. So, even if all the other ports are filtered, the presence of one open port blows your cover. The thing is - if there isn't a service listening on some port (ie it's closed), it doesn't matter how hard an attacker hammers that port - it will have no effect on you.

---

### Post by B-Con on 2007-06-21
> **dreadlord_chris said:**
> The purpose behind stealthing/filtering your ports is to make your computer *appear* invisible - the problem lies in the fact that a networked computer **must** have at least some ports open. So, even if all the other ports are filtered, the presence of one open port blows your cover.

Depends on how you define "open". Technically speaking, "open" means that a port will reply to an SYN with a SYN|ACK. A closed port will respond to an SYN with a RST.  Yes you need to let traffic in on some ports, but you don't need to send RST packets out when you get unexpected SYNs. 

If you never expect to get any connections to your computer, ie your not running any services that'll expect connections, you can just do a simple DROP for all SYN packets in your iptables. This is effective to setting your ports to "filtered", for SYN purposes.
```
$ iptables -A INPUT -m state --state NEW -j DROP
```

---

### Post by dreadlord_chris on 2007-06-24
> **B-Con said:**
> Depends on how you define "open". Technically speaking, "open" means that a port will reply to an SYN with a SYN|ACK. A closed port will respond to an SYN with a RST.  Yes you need to let traffic in on some ports, but you don't need to send RST packets out when you get unexpected SYNs. 

If you never expect to get any connections to your computer, ie your not running any services that'll expect connections, you can just do a simple DROP for all SYN packets in your iptables. This is effective to setting your ports to "filtered", for SYN purposes.
```
$ iptables -A INPUT -m state --state NEW -j DROP
```

This, while not being RFC compliant, is true - and has the added benefit of protecting against SYN flood attacks. I do wonder though, how many typical users have ever been victim of a SYN flood (or any other networked DoS attack). 

How many layers of tinfoil do our hats need this week? :-k

---

### Post by B-Con on 2007-06-24
Heh. The only SYN floods I've ever seen were on IRC channels against script kiddies with dail-up modems. :-P

The main advantage to that is that it allows the user to run in "stealth" mode*. Ie, an attacker cannot determine if a host exists at that address simply by attempting to elicit a reply. This isn't really a *huge* deal, but when it comes to your own security, RFC takes second seat. (A lot of attacks or data elicitation techniques used by hackers rely on technical points of RFC.) And I think the advantage of being "invisible" to an attacker is a bonus. Again, not a huge deal, but really, why not?


* Of course, if the attacker has the ability to sniff the network you're on you won't remain invisible and "stealth" mode is somewhat useless.

I think about three layers is safe, but go with four if you want to be conservative. ;-)

[qutoe]The symbol is not the thing[/quote]
I like that. I wrote a rant/article against flag-worshipers because of that concept a while ago and will stick it on my site somewhat soon. People who don't get that fact drive me nuts.

---

### Post by dreadlord_chris on 2007-06-25
> **B-Con said:**
> Heh. The only SYN floods I've ever seen were on IRC channels against script kiddies with dail-up modems. :-P

The main advantage to that is that it allows the user to run in "stealth" mode*. Ie, an attacker cannot determine if a host exists at that address simply by attempting to elicit a reply. This isn't really a *huge* deal, but when it comes to your own security, RFC takes second seat. (A lot of attacks or data elicitation techniques used by hackers rely on technical points of RFC.) And I think the advantage of being "invisible" to an attacker is a bonus. Again, not a huge deal, but really, why not?


* Of course, if the attacker has the ability to sniff the network you're on you won't remain invisible and "stealth" mode is somewhat useless.

I think about three layers is safe, but go with four if you want to be conservative. ;-)

> The symbol is not the thing
I like that. I wrote a rant/article against flag-worshipers because of that concept a while ago and will stick it on my site somewhat soon. People who don't get that fact drive me nuts.

Unfortunately, one open port pretty much negates the effectivness of *stealth mode*. It doesn't really matter how many of the 65,535 ports silently drop packets during a scan - all it takes is a reply from one open port to reveal their computer's presence. So, *feeling* safe with their shiny new SuperStealthFirewall(tm), they fire up their everyday apps - IM, bittorrent, eMule, etc - never realizing they now have sparkling holes in their NinjaWall. Now, in reality, they are *probably* just as safe - but the false sense of security that *stealth mode* promotes, I've found, tends to preclude them even looking any further.

---

### Post by DarkN00b on 2007-06-25
To reply to the OP:

As long as you have used Firestarter to configure IPtables then it is not necessary to run Firestarter at boot time. Firestarter is _not_ a firewall. All it does is configure IPtables. IPtables is really just a sophisticated packet filter (firewall).

---

### Post by B-Con on 2007-06-25
> **dreadlord_chris said:**
> Unfortunately, one open port pretty much negates the effectivness of *stealth mode*. It doesn't really matter how many of the 65,535 ports silently drop packets during a scan - all it takes is a reply from one open port to reveal their computer's presence. So, *feeling* safe with their shiny new SuperStealthFirewall(tm), they fire up their everyday apps - IM, bittorrent, eMule, etc - never realizing they now have sparkling holes in their NinjaWall. Now, in reality, they are *probably* just as safe - but the false sense of security that *stealth mode* promotes, I've found, tends to preclude them even looking any further.
Yes, of course, which is why I recommended the iptables rule I did. If you have to leave port 6881 open then you basically lose all the benefit of being stealthed. A lot of users don't need to, though. And you can sometimes get away with running bittorrent without open ports.

Although, if you have to leave a port open, you can make it an off-beat one, like 36826. Most port scans, for speed's sake, only scan a default list of several hundered common ports and are unlikely to include such a weird port number. If the attacker is simply looking for a host -- any host -- via a clunky port scan, you may pass by undetected, if you're lucky.

---

### Post by dreadlord_chris on 2007-06-25
> **B-Con said:**
> Yes, of course, which is why I recommended the iptables rule I did. If you have to leave port 6881 open then you basically lose all the benefit of being stealthed. A lot of users don't need to, though. And you can sometimes get away with running bittorrent without open ports.

Although, if you have to leave a port open, you can make it an off-beat one, like 36826. Most port scans, for speed's sake, only scan a default list of several hundered common ports and are unlikely to include such a weird port number. If the attacker is simply looking for a host -- any host -- via a clunky port scan, you may pass by undetected, if you're lucky.

Don't get me wrong, I understand the value of dropping packets to unused ports - if nothing else, less resources are used. Moving services to uncommon ports is also very useful - you won't find ssh at port 22 on my box ;)

but...
there's always a but, isn't there? :p

I'm pretty fanatical about scanning my firewall logs, and I've been noticing a trend over the last few years - an increase in the frequency of *distributed probes*. For a while it was hard to find the pattern in all the noise. I am seeing **alot** of IPs that, instead of scanning well-known ports, seemed to be scanning groups of random ports all over the range. Taken individually, there seemed to be no rhyme or reason to the scans. Until I noticed that other IPs, scanning random (seeming) ports, during the same time periods - almost never seemed to scan the same *random* ports as each other. When taken together I started noticing that these seemingly unrelated IP where scanning the majority, if not all, of the port space.

Just imagine.... you control a bot-net of a thousand compromised computers. You randomize & parcel out 70 ports for each bot to scan - sure, you'll have some overlap, but this actually makes the nature of the scan harder to detect. Suddenly, what was time-consuming and hard to do without being noticed, becomes very easy & increasingly tricky to spot. How many computers do you think that bot-net could thoroughly scan in 24 hours? Thousands....

Now, just imagine that were true.... oh wait #-o

---

### Post by B-Con on 2007-06-25
Heh. We live in the age of the bot net. :-P

Yeah, a perfectly valid scenario. If you get targeted by the bot net and you have any open ports, you're going to get discovered eventually. You're only hope is to not open any ports, or take good care of the ports you do open.

---

