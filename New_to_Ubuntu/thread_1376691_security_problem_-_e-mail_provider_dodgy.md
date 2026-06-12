---
title: "security problem - e-mail provider dodgy?"
date: 2010-01-09
forum: New to Ubuntu
---

### Post by lila on 2010-01-09
Hello,

I know e-mail providers can and do scan e-mails to customise advertising.  Ours definitely does that, since we have a Baby (a few months), we get practically only baby-related advertising on the log-in page and around our mails.  

but now I've noticed that I get specific object adds for things I've looked for on google the previous days - including, all of a sudden, something non-baby related: a particular rare kind of door hinge!  I have definitely never talked about that in an e-mail.  So, if they can scan my google searches, what else?  

The e-mail provider in question is laposte.net, the e-mail service of the French postal service, a non-privatised entity.  

Specification: I do not use the search function on their page, but the firefox toolbar.

Can you tell me what's going on, how serious it is and how to stop it?

Thanks,
Lila

---

### Post by dzon65 on 2010-01-09
Plenty of blockers available.You could start securing with:[http://noscript.net/](http://noscript.net/)

---

### Post by tom.swartz07 on 2010-01-09
> **lila said:**
> Hello,

I know e-mail providers can and do scan e-mails to customise advertising.  Ours definitely does that, since we have a Baby (a few months), we get practically only baby-related advertising on the log-in page and around our mails.  

but now I've noticed that I get specific object adds for things I've looked for on google the previous days - including, all of a sudden, something non-baby related: a particular rare kind of door hinge!  I have definitely never talked about that in an e-mail.  So, if they can scan my google searches, what else?  

The e-mail provider in question is laposte.net, the e-mail service of the French postal service, a non-privatised entity.  

Specification: I do not use the search function on their page, but the firefox toolbar.

Can you tell me what's going on, how serious it is and how to stop it?

Thanks,
Lila

Hi Lila,

There could be a few causes for this...

Your ISP, LaPoste, might actually be tracking your searches and stuff; in which case I would suggest using a VPN to 'hide' what you are doing. Theres a free website [www.itshidden.com](www.itshidden.com) that fools all of the internet trackers and anyone snooping on your internet traffic into thinking your computer is in the Netherlands.

Another possible cause is browser cookies. Perhaps google and your ISP landing page are looking at your cookies to see where you were? Thats just a matter of going into your options and deleting your cookies. Private Browsing is also an option- most browsers have this option.

Those are the only two causes that I could think of..

Hope this helps!

---

### Post by J V on 2010-01-09
Hows this for an idea, google is looking at your searches for both babies and rare door hinges and is using this in its advertising?

Woulden't put it past them...

---

### Post by lila on 2010-01-09
Thanks - meanwhile, I have discovered that there is a dedicated security forum for ubuntu - being a not-very-technological-person I never venture beyond the absolute beginners normally.  Have found lots of step-by step guides there!  Should have looked before, of course...

Will try to secure my computer better.  
Here I was, proud of myself for installing firestarter...

Lila;)

---

### Post by running_rabbit07 on 2010-01-09
> **lila said:**
> Thanks - meanwhile, I have discovered that there is a dedicated security forum for ubuntu - being a not-very-technological-person I never venture beyond the absolute beginners normally.  Have found lots of step-by step guides there!  Should have looked before, of course...

Will try to secure my computer better.  
Here I was, proud of myself for installing firestarter...

Lila;)

Yes, there is lots of great stuff in the security sub-forum. Read the stickies by Bodhi, they are great.

---

### Post by J V on 2010-01-09
hehe, well if you did install firestarter, its a starter, only a starter, actually leaving it running only adds another potential hole for an interuder to come in by (and as it runs sudo they have full access so don't do it!)

---

### Post by warfacegod on 2010-01-09
Instead of Google, I use [http://www.ixquick.com/uk/]("http://www.ixquick.com/uk/")

---

### Post by lila on 2010-01-09
> **J V said:**
> hehe, well if you did install firestarter, its a starter, only a starter, actually leaving it running only adds another potential hole for an interuder to come in by (and as it runs sudo they have full access so don't do it!)

Serious?:shock:

So, why is it recommended?

Good job we keep nothing sensitive on our computer!  Our motto: if you don't REALLY understand a machine, don't give it anything sensitive.
Hence, our customer database, for example, is on index cardsin a shoebox.  Try and hack that...:D

---

### Post by J V on 2010-01-09
Well its good for configuring the firewall, but thats another program alltogether...

It runs as root therefore if its open and someone cracks it your entire system is exposed...

All it really does while its open is monitor the network traffic, just configure it and leave it be...

---

### Post by lila on 2010-01-09
> **J V said:**
> Well its good for configuring the firewall, but thats another program alltogether...

It runs as root therefore if its open and someone cracks it your entire system is exposed...

All it really does while its open is monitor the network traffic, just configure it and leave it be...

!!!  Shouldn't that be written in the instructions, somewhere obvious?

---

### Post by J V on 2010-01-09
yes, but it isn't, like all things linux, it expects you to know what you're doing :)

But yeah, no point in installing it at all if all you want is a firewall, thats built in...

---

### Post by warfacegod on 2010-01-09
> !!! Shouldn't that be written in the instructions, somewhere obvious?

Programmers think everything is already obvious.

---

### Post by running_rabbit07 on 2010-01-09
Instead of Firestarter, use Ubuntu FireWall aka ufw. ```
sudo ufw enable
``` Is all you have to do to get a running firewall that runs all the time and starts automatically when you start the system.

---

### Post by lila on 2010-01-09
> **running_rabbit07 said:**
> Instead of Firestarter, use Ubuntu FireWall aka ufw. ```
sudo ufw enable
``` Is all you have to do to get a running firewall that runs all the time and starts automatically when you start the system.

Thanks!
Done that.  Also got rid of google et al. out of my toolbar and put various language versions of ixquick instead.
Will now go cookie hunting, and maybe run a virus check while I'm at it.:)
See you later!

---

### Post by J V on 2010-01-09
Oh please! Firestarter ufw (uncomplicated firewall btw) are all frontends to iptables, its all the same firewall, and its on your system by default...

---

