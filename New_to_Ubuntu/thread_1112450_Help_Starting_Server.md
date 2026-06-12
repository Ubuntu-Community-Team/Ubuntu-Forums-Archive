---
title: "Help Starting Server?"
date: 2009-03-31
forum: New to Ubuntu
---

### Post by dmaxel on 2009-03-31
Hi there! My family is trying to start a server by using Ubuntu 8.10 Server. We are currently planning on making it a file server for all computers (which includes mostly Windows machines), as well as possibly a TeamSpeak 2 Server. I would like to know how to do this, manage it, and whatnot, as whenever we start the server we see the OS loading, and then when its done a terminal prompt starts (which I suppose is normal). However, we do not know where to go from there.

Thanks for the help in advance!

---

### Post by kanikilu on 2009-03-31
Check out the Ubuntu Server Guide:

[https://help.ubuntu.com/8.04/serverguide/C/index.html](https://help.ubuntu.com/8.04/serverguide/C/index.html)

There's a section on running a file server.

If you have more specific questions, just ask (also remember that there is a sub-forum for server related threads).

---

### Post by jamesrfla on 2009-03-31
If you are not familiar with the terminal prompt I suggest just installing the desktop edition. Then you can use a GUI to configure you file server.

---

### Post by mlentink on 2009-03-31
[http://www.ubuntu.com/products/whatIsubuntu/serveredition](http://www.ubuntu.com/products/whatIsubuntu/serveredition)

---

### Post by kanikilu on 2009-03-31
> **jamesrfla said:**
> If you are not familiar with the terminal prompt I suggest just installing the desktop edition. Then you can use a GUI to configure you file server.+1. Some people frown upon adding a GUI to a server, but I say, for a home server, if you have some system resources to spare and don't know the command line well, it's probably worth it.

To install the desktop, just login at the command prompt and then run:```
sudo apt-get update && sudo apt-get install ubuntu-desktop
```It will take some time, it's not a small download...

---

### Post by hyper_ch on 2009-03-31
> **kanikilu said:**
> +1. Some people frown upon adding a GUI to a server, but I say, for a home server, if you have some system resources to spare and don't know the command line well, it's probably worth it.

And when something won't load you are totally clueless... besides it's an overhead that's not needed and there's not much you need to know about command line. Just how to navigate yourself around, how to edit files, how to install/remove stuff and how to start/stop daemons. Very simple actually.. the big issue is editing the config files. A Gui won't help you there because you still have to *edit* the config files ;)

---

### Post by dmaxel on 2009-03-31
Thank you for the many replies. We have actually tried to put the desktop version on the system at first, but somehow the hardware was not what Ubuntu liked (at least something that made the graphics low), so we tried it with the server edition.

Another question though, what about, lets say I want to start a TeamSpeak 2 Server on there, where i would have to download (or move since I have one running somewhere else), and then start/stop and possibly configure. How would I manage that, as I can't go to Firefox and download something?

---

### Post by mlentink on 2009-03-31
So....

What what is you wanted to actually ***do*** with your server? Tell us and we might be able to give you more specific help

---

### Post by kanikilu on 2009-03-31
> **hyper_ch said:**
> And when something won't load you are totally clueless... Well, it seems like he's totally clueless now (no offense), so instead of ripping into other people's suggestion, how about giving him some pointers that might help beyond "it's not that hard"...

> besides it's an overhead that's not needed and there's not much you need to know about command line.That's really more your opinion, though, isn't it? Only the user can determine if something is "not needed". And for someone coming from Windows with no prior DOS or other CLI knowledge (I'm assuming here), there is a *hell* of a lot to learn at first. Just figuring out how to simply navigate (ls, cd) can be daunting for a new-comer.

> Just how to navigate yourself around, how to edit files, how to install/remove stuff and how to start/stop daemons. Very simple actually.. Once you know how to do it, it's not particularly hard, but you first have to know what a **daemon** is, LOL :D

> the big issue is editing the config files. A Gui won't help you there because you still have to *edit* the config files ;) Ever heard of webmin?

Hey, don't get me wrong, I think the vast majority of tasks can be accomplished easier from the command line, but for someone setting up a home server, I don't think you particularly even need the server kernel, much less go headless without a GUI (unless that's what he wants)...

---

### Post by mlentink on 2009-03-31
> **kanikilu said:**
> 
 ever heard of webmin?

+1!

---

### Post by hyper_ch on 2009-03-31
> **kanikilu said:**
> Well, it seems like he's totally clueless now (no offense), so instead of ripping into other people's suggestion
Did I hurt you? And because he is totally clueless now you think he really, really must have a GUI? Hmmm, there was a time I was totally clueless also but a tiny bit of effort helps a great deal.
[/QUOTE]

> **kanikilu said:**
> That's really more your opinion, though, isn't it?
Not really...

> **kanikilu said:**
> Only the user can determine if something is "not needed".
Not necessarily. If one doesn't know all the options then one can't judge what's needed ;)

> **kanikilu said:**
> And for someone coming from Windows with no prior DOS or other CLI knowledge (I'm assuming here), there is a *hell* of a lot to learn at first. Just figuring out how to simply navigate (ls, cd) can be daunting for a new-comer.
You credit new users too little.
Let's say, navigation around the system: ls, cd
Manipulating files: nano, cp, mv, rm
Manipulating daemons: sudo /etc/init.d/XXX start/restart/stop

Hmmm, it's not much. I think those few commands (especially with a cheat sheet) aren't hard to figure out.

The hard part is still to make right configuation files and that's independant of cli or gui ;)

> **kanikilu said:**
> Once you know how to do it, it's not particularly hard, but you first have to know what a **daemon** is, LOL :D
That's what google and wikipedia is for and that's why I even mentioned it ;)

> **kanikilu said:**
> Ever heard of webmin?
I'm sure you can tell me.

> **kanikilu said:**
> but for someone setting up a home server, I don't think you particularly even need the server kernel, much less go headless without a GUI (unless that's what he wants)...
As shown above, a GUI won't make it simpler to setup a server... and one should not be afraid of the cli. It's one of your best friends on the computer.

But well, you can continue to consider new users as too stupid to handle the cli. I however think they can manage once they see it's not really difficult. Why not doing things right from the beginning?

---

### Post by dmaxel on 2009-03-31
Ahh, sorry for the heated discussions. Yes, I basically am coming from a Windows-mindset, and have somewhat broken through that working with Ubuntu desktop the past week just doing simple tasks. I do understand now that I do need to learn a lot more before I can tackle anything with the command prompt as my only tool, so we are currently trying to get back to the desktop version and then installing the file server program. It'll make it easier on us as it's somewhat familiar (as I've been working with it the past week), and easier to manage (being able to click instead of typing cd /home/user...etc. Thank you for your contributions, as I will probably bookmark the suggested links for learning material and future use in case we want to go just server.

EDIT: I do understand your position as well, hyper_ch, but I do believe I have some catching up to do before I can move to to the server edition. Everything takes its time for me, but I'll eventually manage it. ;)

---

### Post by mlentink on 2009-03-31
> **hyper_ch said:**
> As shown above, a GUI won't make it simpler to setup a server... and one should not be afraid of the cli. It's one of your best friends on the computer.

But well, you can continue to consider new users as too stupid to handle the cli. I however think they can manage once they see it's not really difficult. Why not doing things right from the beginning?

And, as many times before. i think Hyperschwyz is right.
Guys, let&#347; face it. I have just witnessed a Windows Server 200whatever migration to a complete virtualized environment. If the guy that's doing it doesn't know what he's doing....
No matter how much GUI he has to guide him/her/it.

Better tell us what needs to be achieved. so we can tell how to do it.

Afterthought: the re-emergence of the cli in Windows Server 2008....

---

### Post by hyper_ch on 2009-03-31
> **dmaxel said:**
> I do understand now that I do need to learn a lot more before I can tackle anything with the command prompt as my only tool, so we are currently trying to get back to the desktop version and then installing the file server program.
Not really.... I've given you already the basic commands. In addition two cheat sheets here:

[http://files.fosswire.com/2007/08/fwunixref.pdf](http://files.fosswire.com/2007/08/fwunixref.pdf)
[http://files.fosswire.com/2008/04/ubunturef.pdf](http://files.fosswire.com/2008/04/ubunturef.pdf)

That's all you need to know more or less. Also you can find a great many tutorials on servers here: [http://www.howtoforge.com](http://www.howtoforge.com)

The cli isn't as complicated as you think it is. Most config files are well documented, the howtos are usually cli only...

---

