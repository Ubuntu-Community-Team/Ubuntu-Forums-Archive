---
title: "intel wireless 4965AGN..  Ndiswrapper --&gt; where's the guide I saw?"
date: 2007-06-10
forum: Networking &amp; Wireless
---

### Post by mikledet on 2007-06-10
I remember seeing a tutorial/guide how to install the Intel 4965AGN with Ndiswrapper, but I can't find it now (yes, I'm lazy :)  )  There are many guides, I just need that good one... grrrrrr..

---

### Post by RobotJox on 2007-06-11
this one: [http://ubuntuforums.org/showthread.php?t=464720&highlight=4965agn](http://ubuntuforums.org/showthread.php?t=464720&highlight=4965agn)  ?

It kinda worked for me, but my card drops out after a few seconds and then...nothing...

this sounds more promising: [http://intellinuxwireless.org/](http://intellinuxwireless.org/) , but I've had no luck :(

---

### Post by fflarex on 2007-06-11
That's the thread I started and it basically just tells you to make sure you install ndiswrapper from source, because the repository is outdated. Not that useful.

After you install it, see this link, which I used to get the actual driver working: [http://ubuntuforums.org/showpost.php?p=2514602&postcount=8](http://ubuntuforums.org/showpost.php?p=2514602&postcount=8)

I'm no expert, in fact I'm very far from it seeing as I've only been using linux for less than a week, but I managed to get it working and you can PM me if you don't understand the instructions. (I can't troubleshoot for you though, just lay it out in plain English if you don't understand it.)

> **RobotJox said:**
> this sounds more promising: [http://intellinuxwireless.org/](http://intellinuxwireless.org/) , but I've had no luck :(

Eventually there may be native linux drivers for the intel 4965agn (supposedly very soon too, but there have been no news updates on it whatsoever). As of right now, though, ndiswrapper is the only option.

---

