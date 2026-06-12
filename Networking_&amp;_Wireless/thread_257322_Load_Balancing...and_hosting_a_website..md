---
title: "Load Balancing...and hosting a website."
date: 2006-09-14
forum: Networking &amp; Wireless
---

### Post by hellmet on 2006-09-14
Well, 
I attended an interview today..and this was the assignment I was
given..I need to complete this by Monday..to get myself the job..
But I find this quite difficult..

this is the assignment

There are two ISPs..each with one static IP assigned to the computer.
and each with their own Gateway..
I want a Linux (Ubuntu) box to run as the Router between the ISPs
and the internal LAN...with 3 NICs

Two for the ISPs and one for the LAN..
I want the network to Load-balance on its own..

Also one of the cmoputers on the LAN hosts a website..
Suppose there are ppl accessing the website and there is a
failure in one of the ISPs..I still want the users to remain
connected...thru the other ISP..

Is this possible??

PLEASEEE help...as this cud decide my career...
I was able to answer most of the other questions..
but this one was..quite tuff

---

### Post by hellmet on 2006-09-14
hmm....here is a visual image of the same..:(

---

### Post by tbonius on 2006-09-14
I had to re-read that 10 times.. even with your network diagram.

> There are two ISPs..each with one static IP assigned to the computer.

What computer?  Some computer that will exist as a router between two ISPs?
> 
and each with their own Gateway..

Ok

> I want a Linux (Ubuntu) box to run as the Router between the ISPs
and the internal LAN...with 3 NICs
Two for the ISPs and one for the LAN..


What LAN?

> I want the network to Load-balance on its own..

What network?  Load Balance what traffic?  On its own as in with Elf Magic?

> Also one of the cmoputers on the LAN hosts a website..


So now we are adding another computer on a LAN that hosts a website. Um.. ok


> Suppose there are ppl accessing the website and there is a
failure in one of the ISPs..I still want the users to remain
connected...thru the other ISP..

SO the LAN is actually a DMZ for both ISPs?  Users are accessing the website through the ISPs networks to the "LAN"?  This sounds like more of a job for border router configuration than an internal router that is supposed to perform some sort of j00kie failover routing between two ISPs.  Or maybe I am just being naive.

T

---

### Post by kidders on 2006-09-14
What you're describing doesn't seem possible, because of the simple fact that each ISP will be providing your LAN with a different IP. Without an external third party controlling the load balancing, there would be no way to inform clients of the change, should one provider go down.

Even if an external load balancer *was* running, your website example would only work because HTTP is stateless ... almost no other common protocol would be able to handle the switch-over smoothly.

---

### Post by hellmet on 2006-09-15
I am sorry if the explanation was crude...
Dear kidders...ok..putting the website thingy..aside..
will I be able to use the Linux box to load balance..without BGP??
that is the million dollar question..

---

### Post by kidders on 2006-09-15
You're explanation wasn't crude ... don't worry :-)

Here's the way I see it, but I'd really welcome any comments tbonius might have about it.

I know you said to ignore this bit, but say you *did* have a website you wanted to load balance. Furthermore, say you wanted to do it geographically. You have two ISPs, one for India and one for Ireland (lol!).

**ISP 1**
IP: 1.1.1.1
DNS: in.mycoolwebsite.com

**ISP 2**
IP: 2.2.2.2
DNS: ie.mycoolwebsite.com

So, visitors to **www**.mycoolwebsite.com should be quietly redirected to the appropriate subdomain (and hence their local ISP), based on where they happen to be (or any other criteria you wanted). Also, should the Irish ISP crap out on you (suprise suprise!), you want Irish visitors to switch silently to the Indian ISP without noticing.

Now, your diagram tells me that, in reality, in.mycoolwebsite.com and ie.mycoolwebsite.com are really the same server ... it's just being accessed via a different network in each case.

I hope this is an accurate paraphrasal of what you were asked!!

You have two big problems:

**1.** - You model mentioned nothing about the third party ([www.mycoolwebsite.com)](www.mycoolwebsite.com)), that is controlling the load balancing. Large-scale load balancing models require this concept to work successfully. The third party would do nothing but monitor the load/connectivity status of your various ISPs and do nothing but hand out "HTTP/1.1 301 Moved" directives all day.

**2.** - Specific to HTTP-based protocols, silent failover would cause headaches, because web browsers that suddenly found themselves talking to in.mycoolwebsite.com (after spending 10 minutes on ie.mycoolwebsite.com) might stop sending cookies, resulting in a loss of state for affected visitors. There are, of course, ways around that ... but let's ignore it for our purposes. Many other protocols would simply die altogether during the changeover though. :-(

Anyhow, the short answer, as it appears to *me*, is "no". For the kind of load balancing you describe to work, the model is missing one critical piece.

Btw, what's BGP? (I realise this may well be a dumb question!!)

Your diagram itself is trivial, really, in that there is nothing "special" about the Linux-based 3-NIC router, etc. Of course, even if there *were*, you could not effectively load balance activity external to the LAN from within it, by somehow making the network smarter. (Doing so for LAN-originated traffic is a different story though.)

Feel free to tell me all this is a bucket of crap by the way! I like to think I learned *something* about load balancing in college, but my understanding may be flawed somehow.

---

### Post by hellmet on 2006-09-16
thanks for that patient answer dude..
wen I posted the same on linuxquestions.org..i got 
a fu** off kinda answer..
You guys are really nice..

Yea..I seem to have run into a dead end here..
even I am not very very clear at it..bcoz its
something entirely new to me..i.e load balancing

BGP afaik is a contract btw ISPs made by the webhost so
that the failover takes place automatically ..i don't know
more than this tho

---

### Post by kidders on 2006-09-16
> i got a fu** off kinda answer
Yeah, that'll happen ... most members of forums like this will react pretty badly to "Can you please help me with my homework" style questions. Hehe. (It's not really what they're here for.)

---

### Post by socceroos on 2008-07-14
look up pfSense. It does WAN failover.

---

