---
title: "move calendar to bottom where clock is"
date: 2010-10-08
forum: New to Ubuntu
---

### Post by Carus on 2010-10-08
so i tried playing with my panels a bit and i was wondering how to move the nice calendar preview things to the bottom just above the clock, kinda how it was close to the bar when it was at the top
picture attached showing my predicament.

---

### Post by e79 on 2010-10-08
It should have stick with the clock whether you 'moved' it down or you 'added' it to your bottom panel as shown on the picture. Try to delete and add the applet again to see if it solve the issue.

---

### Post by Carus on 2010-10-08
well it went halfway down...

---

### Post by e79 on 2010-10-08
Maybe next time it will go all the way down ?  :lolflag:  Seriously I don't know what to say since every time I tested it, it worked  :(

---

### Post by floborg on 2010-10-13
I have had this problem since upgrading from Lucid to Maverick.

---

### Post by arkadios on 2010-10-13
You tried *killall gnome-panel* from terminal right?

---

### Post by floborg on 2010-10-14
The same thing happens in the LiveCd environment when the panel is on the bottom.

I'd be curious if anyone has tried to see if this happens in any other Linux distro using Gnome 2.32.

---

### Post by garok89 on 2010-10-15
it has been happening to me for 2 months on maverick on 2 computer with several fresh installs....

anyone have any idea how to fix it?

---

### Post by dr_kabuto on 2010-10-15
I have this problem too, opening a bug report?

---

### Post by rinishak on 2010-10-15
Hey, guys. I have the same problem, too. The problem seems to be caused by Compiz or something related to Compiz. Turning off Compiz and clicking the applet placed at the bottom works perfectly - for me, at least. And it looks like it's been going on for a while: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/631664](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/631664)

There's a temporary workaround suggested by a user from the link above, but it uses the Compiz Place Windows plugin:
> Enough of that, here's a temporary workaround: Go to the "Place Windows" plugin of ccsm and under the tab "Fixed Window Placement" find the box "Windows with fixed positions" and click "new". Select the + icon and under "Type" choose "window title". click your calendar applet, then the "grab"-button and then click your open calendar. the resulting value should be something like "title=Calendar" or whatever it is in your language. Click add and under x and y positions choose the farthest settings to the right. Finally check "Keep in workarea" and you should be good to go.
-Either that or disable compiz and hope for another fix.

Do you guys have Compiz enabled?

Hopefully they'll fix it soon.

---

### Post by garok89 on 2010-10-16
confirmed....disabling compiz fixed it
thanks

---

### Post by mabtifro2 on 2010-10-16
had the same problem on fresh maverick install. disabled compiz and problem fixed... except now we cant have visual effects! thanks though!

---

### Post by Rytron on 2010-11-07
Same problem here. Setting Visual Effects to none fixes it alright. That is fine for lower end computers that don't use visual effects, however many people like to use Compiz. I saw this same problem in a Fedora forum. So it must be a GNOME issue. :confused:

---

### Post by shimoda on 2010-11-08
> **rinishak said:**
> Hey, guys. I have the same problem, too. The problem seems to be caused by Compiz or something related to Compiz. Turning off Compiz and clicking the applet placed at the bottom works perfectly - for me, at least. And it looks like it's been going on for a while: [https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/631664](https://bugs.launchpad.net/ubuntu/+source/gnome-panel/+bug/631664)

There's a temporary workaround suggested by a user from the link above, but it uses the Compiz Place Windows plugin:
Enough of that, here's a temporary workaround: Go to the "Place Windows" plugin of ccsm and under the tab "Fixed Window Placement" find the box "Windows with fixed positions" and click "new". Select the + icon and under "Type" choose "window title". click your calendar applet, then the "grab"-button and then click your open calendar. the resulting value should be something like "title=Calendar" or whatever it is in your language. Click add and under x and y positions choose the farthest settings to the right. Finally check "Keep in workarea" and you should be good to go.
-Either that or disable compiz and hope for another fix. 

Hopefully they'll fix it soon.
it really seems a Gnome bug...

thanks for the trick with this Compiz setting! Worked for me!:)

---

