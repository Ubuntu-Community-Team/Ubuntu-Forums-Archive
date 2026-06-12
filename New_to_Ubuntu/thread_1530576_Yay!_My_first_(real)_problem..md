---
title: "Yay! My first (real) problem."
date: 2010-07-13
forum: New to Ubuntu
---

### Post by Planetes on 2010-07-13
I just installed some updates that were sitting in my update manager and then unfortunately on my next login, not my next boot, my theme was a bit screwy. This only seems to happen every other time, in between "breakouts" everything looks normal as far as i can tell. 

So is there a way to see my last updates and then undo them?

---

### Post by rolleander on 2010-07-13
I have not found a way to undo and update - (unless you know exactly which update - uninstall the program in question and manually install an older version - sometimes google can come up with an older .deb package - but only do that if you know what you're doing -


But something important in reference to this matter that might help you in the future - go to System , Administration, software sources, and click the tab that says 'updates'
uncheck Pre-release updates (xxxxx-proposed)

where xxxxx is your version (in my case (lucid-proposed)

Some of the pre-released (proposed) can cause crashes and all kinds of weirdness and I'd only recommend having that checked if you are willing to test and send feedback with a computer that you don't use for work or productivity and can afford to have to wipe and re-install, etc...

---

### Post by rolleander on 2010-07-13
> **Planetes said:**
> my theme was a bit screwy.


by the way - how was your theme screwy - describe it a bit more - maybe I could tell you something a bit more helpful then...

---

### Post by Planetes on 2010-07-13
yeah i got a little trigger happy with my new wireless mouse so i didn't get a chance to actually look at the updates before i sent them into action. 

But good tip i'll get it done, thanks.

---

### Post by rolleander on 2010-07-13
no prob

---

### Post by Planetes on 2010-07-13
well i had a custom theme installed, which takes effect every other time i log on/restart. When its problematic it real ugly. very utilitarian. It doesn't look like any of the default themes on the system. My upper and lower task bars which are normally only partially transparent due to the applets and launchers on them are now completely transparent to the point where i can't read the words Applications/ Places/ System. and can barely see my icons.

Turns out i already had pre-released updates unchecked. 
Any more ideas out there?

---

### Post by rolleander on 2010-07-13
weird - I'm baffled - I'm not sure if this would help or not, but have you tried changing the theme, rebooting and then changing it back and rebooting?

---

### Post by Planetes on 2010-07-13
I'm not sure either. But hey I'll give it a try.

---

### Post by rolleander on 2010-07-13
Oh! Have you upgraded from an earlier version of ubuntu to the newest (ie 9.10 to 10.04)

---

### Post by Planetes on 2010-07-13
Nope. No luck there, I installed 10.04 LTS about two or three months ago.


Ah! My theme is overglossed, it finally says that again instead of just "Custom".

---

### Post by rolleander on 2010-07-13
Are your visual effects on or off?

---

### Post by Planetes on 2010-07-13
Off, I have compiz installed.

---

### Post by rolleander on 2010-07-13
try disabling compiz temporarily and see if that makes a difference

---

### Post by rolleander on 2010-07-13
you'd have to actually uninstall compiz from synaptic - if that doesn't fix it - I'm exhausted of ideas - trying to do a google search on this issue too though so if I find anything... I'll let you know

---

### Post by Planetes on 2010-07-13
Alrighty I'll fully uninstall compiz to see if it helps. As of now i cannot reproduce my problems after disabling compiz. but who knows given time they may show up.

I also did a google search and a forum search before posting, always do, but thanks for the extra effort.

---

### Post by rolleander on 2010-07-13
No problem! Actually I think that may be a compiz conflict - I know it's not as pretty, but you may be better off without it - also I found this:

[http://ohioloco.ubuntuforums.org/showthread.php?t=525934&goto=nextnewest](http://ohioloco.ubuntuforums.org/showthread.php?t=525934&goto=nextnewest)

(but it is from 3 years ago...)

---

### Post by Planetes on 2010-07-13
I don't think that that post was describing my same problem but like you said its three years old. My task bars are there, they're just overly transparent.

I still cannot reproduce the problem after having uninstalled compiz so you may be on to something.

---

### Post by rolleander on 2010-07-13
Sweet! I guess if you really want to be sure, you could re-install compiz and see if it comes back again...

Maybe there's a way to configure compiz to get the problem to go away and still use compiz.

I don't know how important compiz is to you... I'm kind of a minimalist when it comes to my desktop, personally...

but there is a compiz configuration editor called Compiz Fusion Icon that can be installed through the software center.

The program will be under Applications , System Tools - when you click it - it'll look like nothing happened, but in the upper right of screen (system tray) will be a blue-box icon with a white pointer on it

If you right-click it, there will be options

-Reload window manager

-select window manager (compiz, metacity, kwin)

-compiz options (loose binding , indirect rendering)

-select window decorator (mine just says gtk-window decorator)

Now if I had a guess - the indirect rendering or loose binding may be a place to start...

Oh and good rule of thumb
When testing and troubleshooting - only change one option at a time, then test and see - that way if something changes, you know which option changed it :-)

---

### Post by Planetes on 2010-07-13
Well i've re-installed compiz and again have not come across any problems. I don't know what it was but i would have never jump to compiz on my own. 

Thanks for the advice.

---

### Post by rolleander on 2010-07-13
Your welcome and good luck!

---

