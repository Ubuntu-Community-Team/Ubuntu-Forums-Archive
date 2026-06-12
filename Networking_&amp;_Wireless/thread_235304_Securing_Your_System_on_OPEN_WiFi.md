---
title: "Securing Your System on OPEN WiFi"
date: 2006-08-12
forum: Networking &amp; Wireless
---

### Post by Bezmotivnik on 2006-08-12
Well, the good news is that I get free DSL from my generous neighbor's wireless system.  The bad news is that it's an open (unencrypted) access point.  That's not going to change, either.

I know that there are lots of people whose only net access is on public systems like this.  My previous home DSL wireless system was as secure as modern technology and common sense could possibly make it.  

I feel positively *naked* like this! :oops:

What steps can people in this situation take to secure their systems?

Thanks for any advice.

---

### Post by NetworkGuy on 2006-08-12
Since you are running Ubuntu (I'm assuming that) and if you haven't installed anything like Samba or any other type of server software, then you are secure.  I have read that by default the only thing people can see on a new Ubuntu installation is echo replies (pings).  All other ports are closed since nothing is loaded that would be listening on them.  

If you did install some sort of server software on your PC, I recommend configuring IPTables to be a firewall.  Something like firestarter may be where you want to start there.

Hope this helps.

BTW.  It only takes a couple of minutes to crack a WEP key anymore and I believe WPA from a home router can be broken within a few hours.  802.11a/b/g is not secure.

---

### Post by RedBoot on 2006-08-12
As a test you can go to grc.com and run Shields Up. It has a few steps and ends up showing you what ports you have open, closed and 'stealthed'. 
FWIW, when in internet cafes and such, I try to run as many sites as I can using https: instead of http:  For example, google's gmail allows you to simply add the "s" and it then runs all your email encrypted.

---

### Post by Bezmotivnik on 2006-08-13
> **NetworkGuy said:**
> Since you are running Ubuntu (I'm assuming that) 

Well, no, not yet.  I can't get Ubuntu to get fully connected, even with a working, supported wireless device accessing an open system.  Sad, huh? :-|  Can't acquire a network address, apparently.

Eventually, though! :-k 

> I have read that by default the only thing people can see on a new Ubuntu installation is echo replies (pings).  All other ports are closed since nothing is loaded that would be listening on them.  

Yes, "closed by default" firewalling, but I am not 100% sure that's true.  It it were, I think I should have had to manually open some ports by now, and I haven't.  Perhaps Ubuntu somehow does that automagically.

> BTW.  It only takes a couple of minutes to crack a WEP key anymore and I believe WPA from a home router can be broken within a few hours.  802.11a/b/g is not secure.

WPA2/AES with 63-character ASCII PSKs are pretty secure.  I have never heard of them being broken (and I try to stay current with this) but WEP is indeed a total joke.

I would have been very surprised if anyone this side of the NSA could have cracked my previous system, which used the maximum security features and configuration available, plus had the random 63-character ASCII PSK changed every couple of days, plus was shielded against signal leakage outside of the desired indoor area of coverage, plus was turned off when not in use. ;)

You can imagine how weird using an open system after that seems!

I was considering having my desktop machines ethernet cabled into my former wireless router and configuring the router to be in client mode (essentially making it a wireless card for two units), then using the Linux firewall in the router to protect the desktop boxes.  I haven't been able to figure out how to get the network addresses worked out for this so far, though. :-k

I'm beginning to think that there's something to configuring fixed IPs in the net that might help some of this, I dunno, as acquiring network addresses through the host system is almost always a hassle, even under the best circumstances.

---

