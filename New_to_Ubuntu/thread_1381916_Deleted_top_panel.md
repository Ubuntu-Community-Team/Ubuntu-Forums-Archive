---
title: "Deleted top panel"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by vnpifhf on 2010-01-15
i think ive deleted the toolbar at the top but im not sure,,, i cant access it and its not there!!
it had me network status, and everything O_O

if i press me start button my pc it does nothing?!?!

i cant get me settings time or anything!!
please help me and tell me how to get it back!!


ull be my :KS !

---

### Post by vnpifhf on 2010-01-15
also can someone tell me how to install wine?

---

### Post by Cam42 on 2010-01-15
Is the bottom panel still there?
If yes, right click>Add new panel. Drag this new panel to the top if it isn't there.
Right click on the new panel, select add to panel, and you're going to want to add either menu or custom menu, (can't remember which, and that probably isn't the right name.), notification area, user switcher, shut down, clock, and whatever cool things you want there.

```
 sudo apt-get install wine
```

---

### Post by vnpifhf on 2010-01-15
i cant get it to look like the one i had before!!
HELP i really liked the other one and i dont have a clue how to get it back

:(

---

### Post by Cam42 on 2010-01-15
> **jahangir99 said:**
> i cant get it to look like the one i had before!!
HELP i really liked the other one and i dont have a clue how to get it back

:(

Well I really have no way of knowing what changes you made to it. My Ubuntu machine is down for the count at the moment, else I'd create a new user account and tell you the default panel settings, but I really can't right now.

---

### Post by MelDJ on 2010-01-15
how was it before ? and what is missing?

---

### Post by vnpifhf on 2010-01-15
it was the default one , with the drop down start bar on the left and shut down sleep hibernate drop down on the right, time/date, network manager E>T>C

i dont remember lol

please help me i have tried but cant get the default one :(


and how do u put the command prompt for wine if u dont have  start bar?

---

### Post by ThePantryMaster on 2010-01-15
alt f2
gnome panel

does that work?

---

### Post by d3v1150m471c on 2010-01-15
if you deleted it you'll have to readd everything to it that you lost. rightclick the bottom panel and select add new panel. put all the stuff back on it you lost with the panel. If you aren't worried about resetting your desktop back to it's original settings you can always do this, too:

open your home folder and press ctrl + H. delete gconf,gconfd,gnome,gnome2 (gnome might not be in there which is no biggy) Delete them... do not worry, when you log back in it will recreate these configuration files as they would be on a fresh installation. No, you will not lose any programs or saved data (except the stuff altered in those files).

**If you cannot get to these then use alt+F2 and run nautilus.**

P.S. : whatever you're trying to run in wine may run better with wine1.2. You can install this with apt-get or, i suggest, the synaptic package manager. Wine-doors is back up again last i checked and it works in wine (original version) and can help certain stuff in wine run a lot better.

---

### Post by ThePantryMaster on 2010-01-15
if that doesn't work
terminal
```

gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel


```

---

### Post by dzon65 on 2010-01-15
Something else.Someone mentioned it to you in your other thread.When it's solved,please mark it as such.
Kind regards,J.

---

### Post by vnpifhf on 2010-01-15
sorry this thing didnt work and i cant get me bar like how it used to be and im really angry :@

this dosent happen with windows!!
u cant delete the taskbar by acident!
i need 2 get it back
help!
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

above dosent work lmao!

---

### Post by mlentink on 2010-01-15
You have installed Ubuntu for the first time not two hours ago. You do not know it, are only just now trying it out. And now you're angry?

Might i suggest this: [http://www.ubuntupocketguide.com/](http://www.ubuntupocketguide.com/)
And perusal of the excellent pages on the ubuntu website, starting with: [https://help.ubuntu.com/9.10/](https://help.ubuntu.com/9.10/)

---

### Post by vnpifhf on 2010-01-15
lol i like ubuntu better :P but sometimes it frustrates me!

just needs to know how to reset bar back to normal :)

---

### Post by dzon65 on 2010-01-15
Like mentioned before,rightclick on the existing panel.New panel,place it whereever you like.Second,rightclick the new panel,add to panel.A small window pops open where you can choose whatever you want on that new panel.You can change the background,transparency......Hey couldn't do that in windows éy!Now,once you added all the goodies you wanted,move the applets to their right place,rightclick the applets to change their icon (if you want to do that)and fix them to the panel.(so you can't accidentally delete them);)

---

### Post by mlentink on 2010-01-15
I sincerely doubt whether anyone would be able to say they liked an operating system better after less than two hours of use.  But go on trying it out, as long as you keep an open mind. Ubuntu has its faults, just like any other OS.

As to your panels, you might want to read this, where you could have gotten in two clicks with the link I gave you: [http://library.gnome.org/users/user-guide/stable/panels.html](http://library.gnome.org/users/user-guide/stable/panels.html)

---

### Post by warfacegod on 2010-01-15
Right click your top "bar" called a panel and select New Panel. When that panel appears, grab it and drag it to the bottom of your screen. Then right click again and select Add to Panel. You'll probably want:

Highlight each thing in the menu you want and click add.

Show Desktop

Window List

Workspace Switcher

And whatever else you care to put on there. You can move each icon around by right clicking it and selecting Move, you may have to unlock it first.

---

### Post by d3v1150m471c on 2010-01-15
> **jahangir99 said:**
> sorry this thing didnt work and i cant get me bar like how it used to be and im really angry :@

this dosent happen with windows!!
u cant delete the taskbar by acident!
i need 2 get it back
help!
gconftool-2 --shutdown
rm -rf ~/.gconf/apps/panel
pkill gnome-panel

above dosent work lmao!

did you try what I posted somewhere in this thread? It's worked for me on issues like this numerous times...

---

### Post by d3v1150m471c on 2010-01-15
you're right. windows prettymuch decides what the user can and cannot do...part of the reason why i hate it.

---

### Post by dzon65 on 2010-01-15
> **warfacegod said:**
> Right click your top "bar" called a panel and select New Panel. When that panel appears, grab it and drag it to the bottom of your screen. Then right click again and select Add to Panel. You'll probably want:

Highlight each thing in the menu you want and click add.

Show Desktop

Window List

Workspace Switcher

And whatever else you care to put on there. You can move each icon around by right clicking it and selecting Move, you may have to unlock it first.
  Aaand.......if you have some space left,you can even add starters or web-shortcuts.

---

### Post by warfacegod on 2010-01-15
I like having a System Monitor myself.

---

### Post by dzon65 on 2010-01-15
The eyezzz,THE EYEZZZZZ !!!!!!

---

### Post by warfacegod on 2010-01-15
No matter where you stand, they're looking right at you! Creepy.

---

### Post by d3v1150m471c on 2010-01-15
lmao... those eyeball things are pretty cool

---

### Post by doublewitt on 2010-01-18
> **jahangir99 said:**
> lol i like ubuntu better :P but sometimes it frustrates me!

just needs to know how to reset bar back to normal :)

[-X  No need to be frustrated! - just relax - you can make your new toolbar look exactly like the other one. It's so simple. Just like the others said - create a new panel at the top. Right-click on it and ADD everything you need. All links that you had when you installed Ubuntu are available in the list - just add what you need, it's all there. This way, you will know how to build the top panel exactly the same way as before (default). A few minutes of your time... that's all...
enjoy...!

---

