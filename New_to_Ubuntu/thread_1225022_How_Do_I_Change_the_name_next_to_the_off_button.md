---
title: "How Do I Change the name next to the off button?"
date: 2009-07-28
forum: New to Ubuntu
---

### Post by hypnonebula on 2009-07-28
Hi all, 

I tried this,

system > administration > users and groups

i changed the name but then the name next to the off button remains...

the next time I logged into my computer, the old name remains unchanged...

I really need to change it, because the name has a bad spelling... :P

---

### Post by Hobgoblin on 2009-07-28
Right click the button, select preferences, change it to not show the name. :KS

OK, not quite what you wanted but I'm guessing it's the actual username that is showing, not the real name.  Changing the username is more difficult.

I assume you have the system log you on automatically as well?

---

### Post by kostkon on 2009-07-28
Try changing it in *System &#8594; Preferences &#8594; About Me*.

---

### Post by MelDJ on 2009-07-28
try reading this: [http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/](http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/) (first result i found on google:P)

---

### Post by hypnonebula on 2009-07-28
> **Hobgoblin said:**
> Right click the button, select preferences, change it to not show the name. :KS

OK, not quite what you wanted but I'm guessing it's the actual username that is showing, not the real name.  Changing the username is more difficult.

I assume you have the system log you on automatically as well?

thanks,

wow that was fast... (the response)

actually the one shown is the real name, and no, I still need to put in my username and password before logging on...

---

### Post by hypnonebula on 2009-07-28
> **MelDJ said:**
> try reading this: [http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/](http://www.tech-recipes.com/rx/2732/ubuntu_how_to_change_computer_name/) (first result i found on google:P)

honestly, I tried that...

but since i'm a completely useless noob, I freaked out so I didn't try...

I was hoping there is another easier way...

thanks anyway... this time I'll give it a try...

---

### Post by hypnonebula on 2009-07-28
> **kostkon said:**
> Try changing it in *System &#8594; Preferences &#8594; About Me*.

yeah it is shown there, next to the profile picture, but how do i change the real name?

---

### Post by hypnonebula on 2009-07-28
> **hypnonebula said:**
> honestly, I tried that...

but since i'm a completely useless noob, I freaked out so I didn't try...

I was hoping there is another easier way...

thanks anyway... this time I'll give it a try...

ok, an update, i tried that but it actually a command to change the username... it didn't change the name next to the off button...

---

### Post by MelDJ on 2009-07-28
i got it. Try this. Go to Administration. then go to network. Click on general. then change the host name to YoURNAME-desktop. yourname being the name you want. then log out and see if it works:KS

---

### Post by hypnonebula on 2009-07-28
> **MelDJ said:**
> i got it. Try this. Go to Administration. then go to network. Click on general. then change the host name to YoURNAME-desktop. yourname being the name you want. then log out and see if it works:KS

sorry but I tried that one too...

But the thing is, actually I don't have 'network' per se under administration... what I actually have is 'network tools'...

i clicked on it anyway but I couldn't find the 'general' tab

thanks again!

---

### Post by MelDJ on 2009-07-28
that might be because i am using hardy :P.. maybe its hidden too. try looking for it in preferences- main menu..

---

### Post by MelDJ on 2009-07-28
[http://ubuntuforums.org/showthread.php?t=927699](http://ubuntuforums.org/showthread.php?t=927699) try this thread. it explains the command sudo gedit /etc/hostname. Hope it helps:popcorn:

---

### Post by hypnonebula on 2009-07-28
> **MelDJ said:**
> [http://ubuntuforums.org/showthread.php?t=927699](http://ubuntuforums.org/showthread.php?t=927699) try this thread. it explains the command sudo gedit /etc/hostname. Hope it helps:popcorn:

thanks a lot...

I still don't understand terminal (at least i'm getting there now)...

But now problem's solved, thanks to everyone...
:KS

---

### Post by MelDJ on 2009-07-28
glad to hear you solved it :D. 
to learn more on terminal commands go here: [http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/](http://fosswire.com/post/2007/08/unixlinux-command-cheat-sheet/)
its easy once u get the hang of it!:popcorn:

---

