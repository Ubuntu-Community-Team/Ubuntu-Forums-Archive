---
title: "Centralized Users?"
date: 2008-02-27
forum: Networking &amp; Wireless
---

### Post by JoeyH on 2008-02-27
I am building a small network of ubuntu computers for the school. There are seven computers and one server, and there's seven students that will be using these computer. The teacher in charge of the class wants to play "musical computers", so people will sit at different computers at different times.

I want to set up something like roaming profiles, so you can log on to any computer, and all your documents are automatically loaded off the server.

I've already considered LTSP, The problem is, we had to build the network with dated technology. The server only has 512mb of ram, and a 2.8ghz processor. So running LTSP is kinda out of the question for us.

One thing I can think of - I have two spare server systems (exact same specs) just sitting under the desk. Is it possible to run LTSP on a cluster group or something? If so, how do I set that up?

If that isn't possible (or is too complex), what other ways are available to set up roaming profiles?

---

### Post by The Cog on 2008-02-27
If nobody else has any better ideas, I would suggest using NFS to have a common /home partition which is physically on the server and mount it on all the other machines. 

You will also have to propogate the user authentication somehow - there must be standard ways to do this but I don't know how.

---

### Post by Eiríkr on 2008-02-27
I'm not 100% sure, but it looks like [thread=437487]this thread[/thread] talks about just what you need.  

Good luck,

Eiríkr

---

