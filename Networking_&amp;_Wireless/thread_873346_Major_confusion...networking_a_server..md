---
title: "Major confusion...networking a server."
date: 2008-07-28
forum: Networking &amp; Wireless
---

### Post by meesekiller on 2008-07-28
So I've searched around to figure out how to do this...but for the most part, I don't have any idea how to start, so if you could please read below and either a) point me in the right direction or b) explain how this works, I'd be appreciative.

Long story:

So I'm trying to get into using Ubuntu 8.04.1 server. Needless to say I am installing Ubuntu 8.04.1 server edition on an older computer I have just lying around the house.

Right off the bat I have a problem (while installing). I would like to access the internet by linking through my laptop which is running Ubuntu 8.04.1 desktop edition (the two computers are connected via ethernet). I need the internet for obvious reasons, mostly so I can update and install packages via the internet to the server edition. Apparently the server installation can't see anywhere to connect to the internet (I don't blame it my laptop is wirelessly connected to the internet, so I can't just plug in the laptop, the server, or a switch to a dedicated wired internet source). So my options are to allow the internet to run somehow through a network (which I don't understand how to set up in linux or how to ping from the server) or to make the desktop version a repository that I update and then the server looks through to update or obtain files.

Now I'm assuming the first option is easier, but like I said, I really don't know what I'm doing. So if anyone can help me or point me in the right direction for help, that would be great.

Thanks in advance.

---

### Post by knightcoder on 2008-07-28
Are you connecting the server machine to the laptop directly ?? Is there a router/switch in between ??

I believe you need a cross-cable if you're connecting them directly.

---

### Post by meesekiller on 2008-07-28
> **knightcoder said:**
> Are you connecting the server machine to the laptop directly ?? Is there a router/switch in between ??

I believe you need a cross-cable if you're connecting them directly.

There is simply an eithernet cable connecting the laptop to the other machine and I have not the slightest clue what a "cross-cable" is. Googling.

Edit: Huh, I never knew there were different types of ethernet cables. So, in theory, if I connect these two computers using a cross-cable, will the immediately see each other?

---

### Post by knightcoder on 2008-07-28
Yeah. I don't think it would work if you connect two computers directly through a normal ethernet cable. You need a switch/router in between them or a crossover cable.

---

### Post by superprash2003 on 2008-07-29
well there is a cross over cable and a cat5 cable.. cross over is normally used to connect two pcs.. you would need to enable ICS In your laptop for internet to work [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

---

### Post by songshu on 2008-07-29
> **superprash2003 said:**
> well there is a cross over cable and a cat5 cable.. cross over is normally used to connect two pcs.. you would need to enable ICS In your laptop for internet to work [http://ubuntuforums.org/showthread.php?t=91370](http://ubuntuforums.org/showthread.php?t=91370)

basically it is the same cable, just a difference in the scheme for the coloured wires.
You can easily make them yourself if you have the right equipment to squeeze the cables.

---

