---
title: "Really slow internet"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by Spacedementia87 on 2007-12-17
I am connected wirelessly to my router which apparently has:

DownStream Connection Speed  	3808 kbps
UpStream Connection Speed 	448 kbps

however when in linux the internet is really really slow.  If I am in windows on the same machine it is fast.

What could be the problem?

My machine doesn't appear on my attached devices list either but i can ping every other computer in the network fine.

---

### Post by r4ik on 2007-12-17
This is a partial solution:

In firefox, type:
about:config

filter; ipv

find this:
network.dns.disableIPv6

and change its value to "true"

Good luck !

---

### Post by Spacedementia87 on 2007-12-17
Nope afraid not :(

Thing is, it isn't just firefox.  Everything is slow.  Azureus, thunderbird, package manager.

---

### Post by Spacedementia87 on 2007-12-19
Grrr, AOL's tech support are the worst ever!

I e-amil them asking about why it might be having problems.  They ask me to check my firewall is allowing the AOL software and download thier spyware searcher thing.

I tell them that I am running Ubuntu Linux and so don't have the AOL software or any spyware/viruses.

They then reply saying that they know I might like using the malware on my computer but reccomend I download their spyware scanner and use it anyway.  So I told again that I was running linux and so the best I could do to defend my system with their spyware software would be to write it to disc and throw it at people who come near my PC.

Waiting to see what they say to that.

---

