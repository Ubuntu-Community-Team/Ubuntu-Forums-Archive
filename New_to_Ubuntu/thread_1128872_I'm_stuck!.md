---
title: "I'm stuck!"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by balbecdaze on 2009-04-18
After messing about with various things ...

now when I startup, a terminal window opens up - not a problem really, I can close it, but my question is - how can I find out what is making my computer do this? What's the troubleshooting thing to do? (tried google but I'm not very knowledgable about this stuff...)

---

### Post by Peter09 on 2009-04-18
If everything else is working ok then you have most probably just included it in your session configuration.

Goto System->Preferences->Sessions (its now called startup applications in Jaunty)

Look through there for an application called xterm and untick the box.

---

### Post by balbecdaze on 2009-04-18
Wow! fast reply - unfortunately no xterm in my startup!

---

### Post by Peter09 on 2009-04-18
Is there anything else in your session information that could trigger a terminal to come up?

---

### Post by pbpersson on 2009-04-18
Is there anything in your startup list that looks strange or out of place?

When the terminal session opens, does it have a title or any content that would provide any clues?  

Does it appear exactly as a standard terminal session?

---

### Post by balbecdaze on 2009-04-18
Does anyone know if there's some kind of way I can see what my computer's doing when it loads ubuntu? I reckon this'll pin down the reason why I get an open terminal on startup.

---

### Post by uxen on 2009-04-18
I'm not sure but probably you shutted down the computer while you were doing something on terminal. And probably again as you had chosen "Automically Remember Running Applications When Logging Out", when you start the computer, automically starts the terminal. You can check this option and try. It's in Prefences / Session Prefences / Options.
I hope this will solve this problem.

---

### Post by balbecdaze on 2009-04-18
pbpersson - one odd thing - prob'ly irrelevant, the terminal window doesn't have naximise, minimise boxes on the top right - to close it I need to go File Close. And er, most of the startup things look wierd, I'll look again.

---

### Post by Peter09 on 2009-04-18
You can see what is going on at startup by altering the boot parameters, but this is not your problem because this is happening within your session, not at boot time. At a guess something is running within your startup parameters which triggers this.

Is there anything you have been doing of late that could give a further clue?

---

### Post by balbecdaze on 2009-04-18
uxen - maybe, I did tick that box at one point then untick it later. Shutdown and started up again loads since - I don't seem to have a "session" anything under preferences?

---

### Post by balbecdaze on 2009-04-18
Peter09 - it started (I think) when I was trying to delay conky (which I've now unticked from startup) from starting by writing a sleep xx && conky command (in bash ??).

---

### Post by Peter09 on 2009-04-18
What flavor of Ubuntu are you running, the term 'Session' has been replaced by 'Startup Applications' in jaunty.

---

### Post by balbecdaze on 2009-04-18
Jaunty - by the way, what does session information mean and what is the way to discover it?

---

### Post by Peter09 on 2009-04-18
Your conky command could be it ... it is most probably using the console to output error/text messages and because its not completing the 'console' is left open. (Its a good theory anyway ...:D)

---

### Post by pbpersson on 2009-04-18
> **balbecdaze said:**
> pbpersson - one odd thing - prob'ly irrelevant, the terminal window doesn't have naximise, minimise boxes on the top right - to close it I need to go File Close. And er, most of the startup things look wierd, I'll look again.

Nothing is irrelevant - this is not a "standard" terminal session - my instinct tells me it is being spawned by another process during startup.

For instance, perhaps some startup script was told to open a shell script and the script was empty - that sort of thing.

By using the Dependencies view of System Monitor you can see all the current processes and who their parents are - I don't know if that would help.  I just looked at it and it confused the heck out of me ;)

---

### Post by Peter09 on 2009-04-18
'Session' was the old menu item which has been replaced by 'startup applications'

A session is 'what is running + configurations etc' when you log in. On a multiuser system (which Linux is) each user has his own 'Session'.

---

### Post by balbecdaze on 2009-04-18
Just restarted to remind myself - not a massive problem as I've said, but ... does anyone know how I can see the steps ubuntu jaunty is taking on startup? Surely that would give me the reason for this seemingly randomly opened terminal? (or are there a billion thing Ubuntu does to start and I could never keep up ...)

---

### Post by balbecdaze on 2009-04-18
Pbpersson - ah, cool idea - I could look at system monitor with the terminal window open and with it shut and see the difference - I'll try that!

---

### Post by Peter09 on 2009-04-18
type
```
dmesg
```
in a terminal will show you the startup log - but don't hold your breath for a solution from there.

You may get something from syslog.

System->admin->log file viewer

---

### Post by balbecdaze on 2009-04-18
Just did that and there is a process called bash that disappears when I shut my annoying and persistent terminal window. Still stuck though.

---

### Post by balbecdaze on 2009-04-18
Peter09 - see what you mean!

---

### Post by Peter09 on 2009-04-18
Bash is the script that is running that is keeping your terminal open. (its not the name of the script, it the interface that runs the script.) I think you need to look hard at your conky set-up.

---

### Post by balbecdaze on 2009-04-18
Anyway Guys, thanks for the help - this is the most open and useful forum ever - but don't waste your brains anymore 'cos I'm going to bed.  It'll all be fine in the morning - oh, it is morning - oops!

---

### Post by hovzio on 2009-04-18
Can you post the output of this command, this may help clear things up:

```

 cat ~/.config/autostart/* | grep 'Exec'
```


These are "user defined" startup files for gnome, we'll try these first before we check your systemwide settings located in /etc/xdg/autostart. Who knows maybe somehow an entry was made there, although this can not happen on its own..

---

