---
title: "Any way to LIMIT samba transfer speed?"
date: 2007-03-21
forum: Networking &amp; Wireless
---

### Post by hikaricore on 2007-03-21
This is probably an odd request, but I've looked everywhere here, and most search engines.

I found hundreds of posts and howtos on speeding up Samba transfers, the one thing I didn't 
find was a way to limit samba transfers to a slower speed.

Let me explain:

I mix various music electronic tracks, samples, and the such every so often.  Then I like to transfer
them over to my girl's windows desktop either while I'm at work, or while she's playing a game or
doing something else so it's a suprise when she's done.  :)

The problem is, when transfering with Samba it maxes the entirety of our crap network cards
and router, and the internet drops (mostly) or she gets heavy lag in her web browsing/gaming.
It doesn't matter while I'm at work because she's either not here or asleep, but as long as she's
here I like to keep it hush work to make her ask: "when the hell did you do that??".

The only solution I've been able to come up with is to link the folder where i keep the files
in my apache server directory, then mount her desktop via command line, and use:

```
wget --limit-rate=500000 filename.whatever
```

Thus forcing the transfer through apache at 500k/sec.

All done in like 6 steps, which I'd love to avoid.

So, short of writing a gtk frontend for wget to accomplish my task, I'd like to find some way of
limiting the max data transfer of samba as not to hose our network.

Any help is greatly appreciated.

--Aaron

---

### Post by Mr. C. on 2007-03-21
Three things quickly come to mind:

1) renice the smbd process (so it runs when nothing is is running)
2) configure iptables' hashlimit to throttle packets destined to smb ports
3) if your firewall allows it, or you can configure it on your server, you can use outbound traffic shaping

MrC

---

### Post by hikaricore on 2007-03-21
> **Mr. C. said:**
> Three things quickly come to mind:

1) renice the smbd process (so it runs when nothing is is running)
2) configure iptables' hashlimit to throttle packets destined to smb ports
3) if your firewall allows it, or you can configure it on your server, you can use outbound traffic shaping

MrC


1. I don't think this will actually accomplish what I'm looking for, but it may have other uses, I'll remember that one.

2. This sounds like the best bet at this point, I'll look more into iptables as I'm a little rusty.

3. Not really using anything but the router and obviously the default iptables along with hosts.deny / hosts.allow, so I'm pretty limited on this one.


Thanks for the tips.  :)

--Aaron

---

### Post by Mr. C. on 2007-03-21
You're welcome.  Let us know how it goes.

Best of luck,
MrC

---

### Post by Mr. C. on 2007-03-21
It occurs to me that if you can use certain smb.conf TCP parameters to optimize speed, one can reduce speed in the converse manner.

Have a look at : [http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html](http://us4.samba.org/samba/docs/man/Samba-HOWTO-Collection/speed.html)

MrC

---

