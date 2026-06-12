---
title: "Firewall rules?"
date: 2009-08-22
forum: New to Ubuntu
---

### Post by GeordieJedi on 2009-08-22
Hi all, hope your all doing well.

I use my box, like most people. I surf the web, send emails and IM.
Watch films and play music and a play a few games.

Ok, I have a couple of quick questions, if thats ok?

1. Firewalls

I use 2 firewalls on Ubuntu (as I'm the paranoid type). I use both 
Gucfw and firestarter.

Now my main question is this = Do I just start the firewall apps and then forget about them?

I get the occasional hit (thats why I also use firestarter as it shows me who's being attacking my box).
I do realize  that I can apply rules and add/block certain IP addresses.
But (at the moment Im not using bit torrent of doing any major downloading. which will change over time).


2. A bit daft but.....
How do I make my thread post appear in bold on the main page?
I've looked everywhere to no avial. It just makes people looking at posts ignore it more easily.

Thanks in advance for any help and advice.

---

### Post by Bradtek on 2009-08-22
Doesn't answer your question, but

You are only using 1 firewall (iptables)
and 2 Frontends to iptables
Which isn't paranoid it's pointless isn't

Someone pls correct me if I am wrong.

> I get the occasional hit (thats why I also use firestarter as it shows me who's being attacking my box).

What makes you think you are being attacked (as opposed to just being scanned like everyone else in your IP range) ?

---

### Post by philinux on 2009-08-22
You dont have two FW's. Only two gui's to control the firewall which is iptables.
Yuo dont need to start either gui at bootup only if you wish to change iptables.
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

If you use one you also have a firewall in your router.

---

### Post by sasho_zl on 2009-08-22
> **Bradtek said:**
> Doesn't answer your question, but

You are only using 1 firewall (iptables)
and 2 Frontends to iptables
Which isn't paranoid it's pointless isn't

Someone pls correct me if I am wrong.



What makes you think you are being attacked (as opposed to just being scanned like everyone else in your IP range) ?

Actually iptables is also a configuration tool for the real kernel firewall - the GNU/Linux Netfilter...
Maybe the most easy to use and supported solution is the Gufw. Use it and remove firestarter which is more a security breach then a firewall in fact. And if you are really interested in your PC security install Host and Network intrusion detection systems.

---

### Post by 3rdalbum on 2009-08-22
> **GeordieJedi said:**
> Hi all, hope your all doing well.

I use my box, like most people. I surf the web, send emails and IM.
Watch films and play music and a play a few games.

Ok, I have a couple of quick questions, if thats ok?

1. Firewalls

I use 2 firewalls on Ubuntu (as I'm the paranoid type). I use both 
Gucfw and firestarter.

You surf the web, send e-mail and IM. You watch films, play music and play a few games.

None of those things that you've listed will open *any* incoming ports on your computer. At least, as far as I know. So your computer won't respond to any incoming connection requests anyway, regardless of whether or not you've got a firewall.

I don't think you actually know what a firewall does. A firewall does just two things, essentially:

1. Passes packets through, if they are coming in on a port that you have allowed.
2. "Drops" packets (doesn't allow them through) if they are coming in on a port that you haven't allowed.

It doesn't look at the packets to see if they correspond to a known attack, or look to see if they match the pattern of a virus. It just drops any packets that you haven't said are allowed.

So, setting up two firewalls doesn't make sense, even for the paranoid type. If the packet is dropped by one firewall, then it doesn't make it to the second firewall. If your two firewalls have the same set of rules, then there will NEVER be times when a packet will go through the "first" firewall and be blocked by the "second". If the two firewalls have different rules, then what's the point?

In addition, whenever you want to open or close a port, that makes more work for you, for ZERO security gain.

Two anti-viruses makes more sense, because some anti-virus programs will know about viruses that the other program doesn't know. Firewalls, on the other hand, don't know what's bad and what's good, all they know is what you've told them to block and what you've not told them to block.

And as the other posters have told you, you're only running one personal firewall anyway. gUFW and Firestarter are frontends for the same firewall running in-kernel. I'd highly recommend removing Firestarter anyway - it's a confusing program to use even when you're only applying one set of rules to Iptables, and it gives newbs a heart attack when they see that other computers are trying and failing to connect - they think that they're being attacked by the Russians. It's normal to have the occasional incoming connection on the Internet, and it poses no threat as long as nothing on your computer is listening to that port.

One firewall running at your internet gateway, and one running on your personal computer, makes more sense - have one firewall protecting your network-facing services from being accessed through the Internet, and the other firewall protects your personal computer's services from being accessed by other computers on your network.

Sorry if this seems like a long sound-off, but now that you know what a firewall does and doesn't do, you'll hopefully have a better and less paranoid computing experience.

---

### Post by GeordieJedi on 2009-08-22
Thanks to everyone who's responded so far.

Ok. I should clarify a few things. (should have mentioned this before, but as you
all know, hindsight is the clearest of all).

1. I understand that I'm not under constant attack (although I did have a strange
episode a few months back).

I use two firewalls, (not for the paranoia reasons) but beacause I get different things
from each one. I use Gufw because its very easy to set up and I just leave it alone and
let it do its thing.
I use Firestarter as it gives me a good breakdown of the hits and thier originating IP
addresses.

Q1. = (Which firewall takes priority? I start Gufw 1st (Its set to start on boot). And
firestarter which is started manually next).


2. I don't yet, do a lot of downloading, eg: bit torrent, ftp Linux .iso's (this will
change in the future though). Which is one of the reasons I was wondering about my
set-up.

3. Is there a pre-set set of rules that I can download that I could import into my
firewall, that would help keep me safe? Or is it just a case of setting up each
individual rule/service as I go on?

4. I use a router to access the net, and I know that it has a built in firewall.
which helps.

I dual boot with windows and I know that I can forget most of the crud that comes with
using that system. (But I really think that a "Healthy" does of paranoia does everyone
the world of good :-))

I use Kaspersky Internet suite on Win and I like it a great deal.
I'd like something with the ability to be configurable, but mostly something that I can
startup and then forget about, knowing that I'm protected.


Thanks for all of your reply's and help so far. Its much appreciated!

---

### Post by sasho_zl on 2009-08-22
You don't need Firestarter to monitor your connections. As I've wrote before it is a security risk because it has root privileges. The best way to monitor your system is through the system logs. The blocked connections as well as a lot more info then the one provided by firestarter can be seen in /var/log/messages. List of active connections through those commands:```
 lsof -i -n -P
```
```
lsof | grep TCP
```
```
tail -f /var/log/messages | grep eth0
```

---

### Post by cariboo on 2009-08-22
For more info on setting up security on your computer have a look at this [sticky]("http://ubuntuforums.org/showthread.php?t=510812")

---

### Post by markharding557 on 2009-08-22
have a look at guarddog this about the best gui i have found

---

