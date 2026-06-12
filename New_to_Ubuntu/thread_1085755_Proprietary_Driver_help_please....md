---
title: "Proprietary Driver help please..."
date: 2009-03-03
forum: New to Ubuntu
---

### Post by Jingle on 2009-03-03
Hi all,

I've been playing with Ubuntu for a couple of weeks now and really like it, however I've installed and removed various things in the course of experimenting.  Now I'd like to re-install (changing partitions etc) but I have a problem:

When I first install/run from the live cd I can't get internet access due to the fact that I have a belkin (broadcom) wifi card and no wired access.  That's fine I understand about the copyright issues etc.

What I would like to do is make my own install/live CD with these drivers integrated so I don't physically have to dismantle my PC drag it across the house and find a wired network connection.  

Is this possible, if so can someone help me out with some "how to" steps please.  

If I can't change the original installation disc due to copyright that's fine, I would quite happily settle for a second CD with these drivers on (I would then like to add things like the medibuntu extras and stuff so I don't have to keep downloading it all).  If so, how can I a) extract the drivers from my existing setup and b) point ubuntu to the CD to look for them when I'm installing?

Thanks in advance
Frazer

*just incase it's relevant, when I did get a wired connection the update manager installed the proprietary drivers for me, I didn't have to do any messing about with ndiswrapper or firmwarecutter or anything (which was a relief)*

---

### Post by Jingle on 2009-03-04
bump...

Ok I've given up on the idea of embedding the drivers into a live CD :(  but I'd like to create a CD with these drivers on so I can do an offline installation, that must be possible?

I've looked at remastersys but it specifically states on the website that it won't include proprietary drivers.

---

### Post by OffAxis on 2009-03-04
what about apt on cd?
aptoncd.sourceforge.net

It's in the repos
```

sudo apt-get install aptoncd
```

---

