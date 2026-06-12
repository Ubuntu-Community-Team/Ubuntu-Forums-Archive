---
title: "Recurring crashes soon after start up"
date: 2009-01-27
forum: New to Ubuntu
---

### Post by jtsc on 2009-01-27
So I've had ubuntu functioning well on a laptop for almost a week. In the past hour it has frozen six times... the first few times about ten minutes after startup, but now just about two to four minutes after.

The only thing that works are the power button and the cd drive. The caps lock light, for whatever reason, starts flashing at the moment the screen freezes; if any sound was playing it repeats like a skipping cd.

At first I thought it was songbird, which I installed this morning, but the past several times songbird wasn't running when the computer crashed. The last two or three times the only thing I had done was enter my username and password and begin to use firefox.

Suggestions? How do I even figure out what the problem is, much less fix it?

---

### Post by Crafty Kisses on 2009-01-27
How about we start with your system specs?

---

### Post by jtsc on 2009-01-27
The computer is a Lenovo Thinkpad z61t with 80GB, 1.83GHz Intel Core Duo, either 1 or 2 GB of RAM (sorry to be so vague, I'm reconstructing this from the shipping report since the computer isn't working so well now...). Any other computer specs that might indicate a problem?

The operating system is Ubuntu 8.10, running with Gnome.

What other information could help?

---

### Post by jtsc on 2009-01-27
Can anyone at least give me some ideas about where to start?

(Apologies if bumping my request isn't allowed.)

---

### Post by jtsc on 2009-01-28
So following the advice in [this]("http://ubuntuforums.org/showthread.php?t=1052559") thread I'm looking at messages, syslog, and kern.log... but it's kind of opaque, I'm not sure which lines are the events that caused the panic, and then I don't know what to fix. Help?

---

### Post by jimrz on 2009-01-28
Sounds like the problem in [[COLOR="Sienna"]**_this_**[/COLOR]]("http://ubuntuforums.org/showthread.php?t=968792&highlight=4965") thread also experienced by several people with x6x series Thinkpads. These all seem to be caused by Intel wifi card and the thread also details the cure. Hope it helps.

---

### Post by jtsc on 2009-01-28
dear jimrz - thank you! That sounds like my problem exactly, down to the detail that it happened as soon as I went on to my main university campus. I've installed linux-backports-modules-intrepid, I'll try it out tomorrow.

---

### Post by jimrz on 2009-01-28
:) ... post back with how it goes

---

