---
title: "Port Fowarding without access to router (BSD router)"
date: 2008-09-22
forum: Networking &amp; Wireless
---

### Post by benander on 2008-09-22
Hi,

I am wondering if anyone could point me in the right direction for this question. Please don't answer it completely. It's for a class, not an assignment but I would rather figure it out on my own.

We have a lab behind a NAT (BSD router) with the only open port being 80.  We were asked if we could figure out how to have computers outside the NAT communicate with computers inside the NAT using SSH.  The tricky part is that we don't have access to the BSD router but we do have root privileges on computers inside the network.

I'm pretty lost on what to search for so articles containing information would be great.

---

### Post by Iowan on 2008-09-22
> **benander said:**
>  Please don't answer it completely. Shouldn't be a problem - since I don't know the answer...
What other information do you have?  Are you to set up the inside computers first, or assume an existing network, and "break in" (not exactly "breaking" via SSH)?
[VPN]("https://help.ubuntu.com/community/SSH_VPN") *might* be a possibility if you can decipher what the router will permit.

---

### Post by benander on 2008-09-22
Ok sorry for not including enough info.

Basically we have a BSD router acting as our gateway to the DNS servers at our school.  We can not access the router in any way directly, but have set up computers behind the BSD server that use it as a gateway.  I can SSH out to other servers at the school, but nothing can SSH in. We are not allowed to change anything on the gateway to get the SSH to forward through port 80 (which is the task at hand).

That's pretty much all I know, unless I missed something when it was explained to me.

I'll read up on VPN in the meantime.

---

### Post by gali98 on 2008-09-22
Don't know much about this kind of stuff, but couldn't you just set up the computers on the inside to accept ssh through port 80?
Also what about UDP port punching....
Like I said, don't know much about this. If you do find the answer, would you post it? This is interesting. Staying tuned.
Kory

---

### Post by benander on 2008-09-22
So I just started reading about SSH Tunneling.  This seems to be what my teacher was talking about. I'll have to do some research into the subject but I found a few decent tutorials. I'll post again about my findings.

---

### Post by Iowan on 2008-09-23
I, too, will look forward to your results...

---

