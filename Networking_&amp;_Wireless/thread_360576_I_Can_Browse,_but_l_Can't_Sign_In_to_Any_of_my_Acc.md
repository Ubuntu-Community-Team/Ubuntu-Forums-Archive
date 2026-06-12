---
title: "I Can Browse, but l Can't Sign In to Any of my Accounts."
date: 2007-02-13
forum: Networking &amp; Wireless
---

### Post by SendDerek on 2007-02-13
[RESOLVED]

Hello!

I have a wired connection only on this one.  It's my wife's computer and for some odd reason, it will let us browse the Internet just fine, but once we try to login somewhere like google.com/ig or hotmail.com (just to name a couple) it goes to a page cannot be displayed message. 

I have tested in both Opera and Firefox, but both do the exact same thing.  My other computer will do everything just fine and it's connected to the same router.  So, I'm thinking that the router settings are alright.  

I wanted to see if it made a difference to use Network Manager instead since I've always had good luck with it, but it the only message I get out of it is "No network device could be found."  

I even tried to ping google.com (as well as 72.14.207.99) and redhat.com, but I can't ping them from either computer.  It may be because of the limitations on the network we have here on campus.

The two computers can talk with each other.  My wife's computer can get updates from synaptic and download things from there as well.  We just can't sign into anything.  Would it be that we can't get to any https sites?  That's about the only thing I can think of.

Also, on the computer that works, I copied down the DNS server from resolve.conf, and copied it to the non-working computer's resolve.conf and restarted with no resolve.

What could be happening?

Thanks for any help in advance...

-Derek

---

### Post by SendDerek on 2007-02-13
Oh, GRRR.... the one thing I didn't check was the one thing that was making all this a problem.

Firestarter.

I ran it and disabled it and now everything is fine.  Is there a way to allow https access to firestarter?

EDIT:  Nevermind... I've figured this one out as well!  lol.  I just need to stop assuming the worst.  I just added a policy for HTTPS in there for everyone to allow.

---

