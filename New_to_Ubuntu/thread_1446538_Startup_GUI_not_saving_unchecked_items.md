---
title: "Startup GUI not saving unchecked items"
date: 2010-04-04
forum: New to Ubuntu
---

### Post by wannabegeek on 2010-04-04
hello,

When I un-check an item in System>Pref>Startup   the change doesn't hold. If i open it again, the check box is marked....?

Also, I'd like to add Compiz there, because for some reason it is not my default manager...

I have looked for the directory where startup items are kept and cannot find it...

thanks,
wbg

---

### Post by wannabegeek on 2010-04-04
not the best solution, I wrote a script to kill the processes and put in my  .profile

I'd still like to be able to edit the startup GUI  it's a cool featue, if it worked ...

wbg

---

### Post by demosthene1 on 2010-04-04
I have Jaunty and Startup works fine. What version do you have?

---

### Post by warfacegod on 2010-04-04
In Startup Applications, under the Options tab, have you enabled "Remember Applications blah, blah"? If so, that could be the problem.

Another way that might work is to right click your menu and select Edit Menu. Highlight Preferences> right click Startup Applications> select properties> add gksudo to the beginning of the command.

```
gksudo gnome-session-properties
```

I have no idea how "safe" this is nor if it will even let Startup... well, start up (it should). Do this may just make changes to the root account and not yours. If it doesn't work, then set the command back to it's default.

---

### Post by warfacegod on 2010-04-04
What exactly do you mean by setting Compiz as the default manager?

---

### Post by wannabegeek on 2010-04-04
hi again and thanks for replies...

> What exactly do you mean by setting Compiz as the default manager? This is my way of trying to not mis-name something, that I don't know how to say....

I had just the standard effects from the System > Appearance > Desktop Effects

Then I installed CCSM, I was able to get the other effects to work and the effects were available every time I logged in.

As well, my keyboard shortcuts from the System menu, started behaving strange and I use what hot keys work and 
use compiz shortcuts to make up the difference. All the googling I've done points out that this keyboard shortcut thing is a common problem.

Using the menu, I went back to appearances > desktop effects and set to none, which was my attempt to turn off the 'compiz' effects.
Then, I turned them back on by running "compiz" from F2....but it doesn't load for every login....

wbg

---

### Post by warfacegod on 2010-04-04
Turning effects to none, as you did, does indeed turn Compiz "off". So you think that CompizConfig messe up your keyboard shortcuts?

Give Ubuntu Tweak a try. It has a Startup section that should work for you. Compiz won't be in there though. Not will it be in the regular Startup Applications in your Main menu.

---

### Post by wannabegeek on 2010-04-05
@ warfacegod...

Hey it worked !   I put gksudo before the command and the startup changes hold.

I looked and could not find the gnome-session-properties directory anywhere...I even tried 
'find' from root...

 ahh...one major caveat...System Monitor shows that the processes I unchecked in Startup Applications
are still running...

For now I will kill them with my script...

wbg

---

### Post by warfacegod on 2010-04-05
gnome-system-properties should be somewhere in the Configuration Editor (System Tools).

---

