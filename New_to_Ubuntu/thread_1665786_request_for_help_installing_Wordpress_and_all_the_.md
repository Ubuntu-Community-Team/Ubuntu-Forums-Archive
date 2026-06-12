---
title: "request for help installing Wordpress and all the things it needs to work"
date: 2011-01-12
forum: New to Ubuntu
---

### Post by Old Jimma on 2011-01-12
Hi Ubuntu Community:

I've been struggling with installing Wordpress. Seems like I've tried everything. 

Tried the 5 minute install. Didn't work. :neutral:

Tried following directions on a bunch of you tube guides. Didn't work. :(

Tried the Ubuntu Community Documentation: [https://help.ubuntu.com/community/WordPress]("https://help.ubuntu.com/community/WordPress") ... couldn't understand it... too complex for an old guy.

:confused:

Bought the Wordpress for Dummies book.... huh?? Didn't help. :-k

[COLOR="Blue"]**What I want is: to install everything that Wordpress needs to start tinkering with WP _on my own machine_... **[/COLOR] (I haven't rented server space, yet.)

Would someone kindly give me a hand with this? [-o<

Many thanks,
Phil Smith
Duluth, GA

---

### Post by SuaSwe on 2011-01-12
Hi Phil!

I had some troubles installing WordPress on my self-hosted domain recently, and chronicled the lot here:

[http://www.suaserve.com/theBlog/?p=9](http://www.suaserve.com/theBlog/?p=9)

Any questions please ask. :)

---

### Post by SuaSwe on 2011-01-12
Just had a read through my post there and it does dive into it sort of in the middle. Look from the point of:

"Anyhow &#8211; here&#8217;s where the fun starts. Time to totally wipe all this stuff off the server and start afresh, and this time doing it right!"

---

### Post by Old Jimma on 2011-01-13
Hi SwaSwe:

I followed the advice from your blog.

Now, synaptic doesn't work and sound doesn't work.

I wondered whether this happened to you, also, and how you recovered.

Thanks,
Phil

---

### Post by Hippytaff on 2011-01-13
Does
```

sudo apt-get update && sudo apt-get upgrade

```work?

If so you might just need to reinstall synaptic, but I don't know why installing wordpress would cause these anomolies, though Swaswe is the expert on this.

---

### Post by Old Jimma on 2011-01-13
I reinstalled 10.04 and things work more nicely now.

I'll look at those suggestions again. I don' know what happened there.

P

---

### Post by mastablasta on 2011-01-14
If i am not mistaking you will need to set up a LAMP server first.
 
if you just want to tinker with wordpress i suggest you use one of free hosting sites available (might get slow at times). for example one of them is: 000web$$$host.com
 
[enter address without $$$ as forums won't let me post the original address]
 
you register, get a subdomain and then just go for fantastico installer (ok you might need to create one MySQL database first). a few clicks later you will have wordpress set up and ready for tinkering.
 
i am doing somethign similar at the moment with opencart.

---

