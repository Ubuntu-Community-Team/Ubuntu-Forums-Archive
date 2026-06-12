---
title: "my broadcom 4306 wireless does random disconnects"
date: 2007-02-07
forum: Networking &amp; Wireless
---

### Post by nekofelin on 2007-02-07
hi i'm new to linux (Ubuntu Edgy 6.10) and thought i'd give it a shot for my laptop.  well installed fine and all but it seems that the wireless went shoddy.  so i use the [how to boradcom]("http://www.ubuntuforums.org/showthread.php?t=185174&highlight=wireless+broadcom+bcm43xx") and well it works because my wireless connects but the problem seems to be that it will disconnect from the public router in my university after a while or when i close my laptop lid for too long.  i tired the enable re-enable to try to reconnect but that won't let it reconnect to the wireless.  so i have to reluctantly restart my computer to the wireless going.  is there a way to reconnect without a restart?  also is it important to know that my wireless card is labeled as eth1?  does that have to do with anything?  hope for responses soon!

---

### Post by BjarneJ on 2007-02-08
I have the same problem, also with the Broadcom 4306 driver. Wish I could say I had a solution for it, but I haven't found anything yet. I can, however, restart my connection thus:

$ sudo ifdown eth1

and then:

$ sudo ifup eth1



I don't think it has anything to do with it be called eth1.

---

### Post by nekofelin on 2007-02-08
sweet thanks for that now i'll keep it at hand :D i hope for a permanent solution though

---

### Post by ppvanzella on 2007-02-09
Mine does the same thing, except that I can't ifup it again, it just doesn't find any network...
Any idea?

---

### Post by nekofelin on 2007-02-09
hmmm no idea really...so new to ubuntu :D well tried to install beryl and my X screwed up so have to re-format (but that's another story)  hopefully this time the wireless will work flawlessly :D will post result when done

---

### Post by nekofelin on 2007-02-09
curses beryl won't work after 4-5 times of reformat anyways redid the process of setting up but good news is now i don't seem to have an unstable linux wireless anymore anymore.  even the wireless bars show up which previously didn't which is weird.  dunnno what happened but now it works.

---

### Post by BjarneJ on 2007-02-10
#4 

Maybe you should try instead:

sudo /etc/init.d/networking restart

---

