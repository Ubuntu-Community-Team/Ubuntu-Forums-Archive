---
title: "How to kill gnome-panel?"
date: 2009-09-20
forum: New to Ubuntu
---

### Post by harisund on 2009-09-20
Does anyone know how to kill gnome-panel? 

I tried killall gnome-panel and kill -9 <gnome-panel pid> and they both only restart the gnome-panel? 

Is this a gnome thing or a Ubuntu thing?

---

### Post by Tclarkie on 2009-09-20
why r u killing it

---

### Post by Tclarkie on 2009-09-20
right click
delete panel

---

### Post by Joeb454 on 2009-09-20
> **Tclarkie said:**
> right click
delete panel

That doesn't kill the process though, merely deletes the panel.

I'm surprised something like ```
killall -9 gnome-panel
``` didn't work though

---

### Post by Paqman on 2009-09-20
> **harisund said:**
> they both only restart the gnome-panel? 


Indeed, as they're supposed to. Gnome does require you to have at least one panel IIRC.

---

### Post by wojox on 2009-09-20
Open a terminal type:

```
ps aux
```

Look for gnome-panel and find it's pid.

Then:

```
kill <pid>
```

---

### Post by harisund on 2009-09-20
> **Tclarkie said:**
> why r u killing it

I am sorry, I didn't realize I was posting in the Apple forums! 

> **Paqman said:**
> Indeed, as they're supposed to. Gnome does require you to have at least one panel IIRC.

So Gnome is becoming like Apple after all, they decide what's best for the user. 

No, but seriously, I just wanted to have the Gnome panel removed to see how much memory it took and if I could reduce the memory footprint. 

And please don't suggested on installing some other desktop environment or some random LowMemoryBuntu. I just want to see how much low memory I could get with a default Ubuntu install and still retain the convenience. I am trying to get rid of various applets to save on memory (replacing it with a Conky window, for example), killing background processes etc. But Gnome is like Windows, with its own registry to edit 

The fact that Gnome decides you can't remove its panel is just wrong man :(

---

### Post by Paqman on 2009-09-20
> **harisund said:**
> 
The fact that Gnome decides you can't remove its panel is just wrong man :(

Not really. A desktop without any panels would be pretty unusable. Making sure the user doesn't accidentally remove their last panel is a nice feature.

Killing a panel is different from removing it, btw. Kill a panel and it'll respawn. That's very useful, if your panel ever misbehaves you just kill it and it comes back fresh as a daisy.

If you want to see how much memory a process is using, go to System > Admin > System Monitor.

Btw, I happen to know exactly how lightweight Gnome can be from my own experiments. Getting it down to about 80MB at idle is eminently doable. Although it's far easier to achieve this by adding packages to a minimal install than it is by stripping back the default install.

---

### Post by harisund on 2009-09-20
> **Paqman said:**
>  A desktop without any panels would be pretty unusable
That's something the user should decide, not Gnome. 

> Making sure the user doesn't accidentally remove their last panel is a nice feature.
What about deliberately? 

> If you want to see how much memory a process is using, go to System > Admin > System Monitor.
I prefer top. System Monitor is probably the biggest memory or CPU hog I have seen, except Firefox of course. 


> Btw, I happen to know exactly how lightweight Gnome can be from my own experiments. Getting it down to about 80MB at idle is eminently doable. Although it's far easier to achieve this by adding packages to a minimal install than it is by stripping back the default install.
Finally, some useful information in this thread :) 80MB? Do you have some documentation of how you achieved that? I would love to read it. 

Thanks man, please don't take this personally, but I am not really angry with you, just Gnome. Maybe I should just dump Gnome and go back to hanging out more with the command line.

---

### Post by Paqman on 2009-09-20
> **harisund said:**
> That's something the user should decide, not Gnome. 


I disagree. I think it's important for a DE to make sensible usability decisions. Flexibility and ease of customisation is a feature, but so is usability. The designers have to weigh all these things against each other, and it's their job to decide where one gets sacrificed for the other, because you can't have everything.

If you're hacking up the DE to the point where you're removing all the panels, i'd say you're stepping well outside the design parameters of the DE. You can't really blame the designers for not taking your special case into account.

Besides, there may well be a good technical reason why removing all the panels isn't a good idea. Who knows?

> 
80MB? Do you have some documentation of how you achieved that? I would love to read it. 


It's actually pretty easy. You just [build up from the minimal image]("http://andyduffell.com/techblog/?p=361"), using the metapackages in the repos. I used a Virtualbox environment to keep things nice and simple.

---

### Post by mcduck on 2009-09-21
As long as the Gnome-Panel is defined as desktop component in gconf Gnome will automatically spwan it back wen killed.

So, if you want to remove the Gnome-panel from your desktop you need to start gconf-editor and then remove "panel" from the list in desktop/gnome/session/required_components list (and perhaps also unset the desktop/gnome/session/required_components/panel -key).

But if you are planning to just run some other panel or dock instead it would make sense the leave the panel in the session components, and then just set the desktop/gnome/session/required_components/panel to use whatever program you are planning to run. This would automatically start that app for you and also autospawn it back if it crashes or is killed.

(and no, removing the last panel doesn't work. Actually that's impossible, Gnome-panel's developers were sensible enough to prevent doing that since you'd end with gnome-panel still running but with no actual panels and thus no way to interact with the program any more to add back the panels..)

Also note that if you disable Gnome-panel you will loose the Alt-F2 Run dialog as well, so make sure you have some other way to start applications that the Run dialog and panel menus.. ;)

---

### Post by nothingspecial on 2009-09-21
> **Paqman said:**
> Indeed, as they're supposed to. Gnome does require you to have at least one panel IIRC.

I don`t have any panels.

Just move gnome-panel out of /usr/bin
```

sudo mv /usr/bin/gnome-panel ~/.panel
```

You can always move it back later.

---

### Post by madchine on 2010-08-17
What a load of male cow dung...

1) If you cannot help answer the OP's question in the spirit intended, please-o-please, just butt out. 

2) Misinformation is worse than no information. There are no 'requirements as to what processes constitute a GNOME session'. You can disable gnome-panel and run xfce4-panel instead. And kill that and have no panels. Or something else - the choice is yours. Some software may require a notifciation area/systray but that's another story.

3) I don't have a perfect solution but running 
```
gnome-panel --replace
killall gnome-panel
```seems to do the trick. 

[ASSUMPTIONS] The first line probabvly replaces the 'session gnome-panel process' with a user-run process and while the first respawns, the latter does not and is therefore... killable! [/ASSUMPTIONS]

---

### Post by nothingspecial on 2010-08-17
> **madchine said:**
> What a load of male cow dung...

Sorry, but which bit of my answer was "male cow dung"?

---

### Post by madchine on 2010-08-18
@nothingpsecial: Why are you assuming, that I was referring to your reply? My comment was on the general quality of replies to the OP, tclarkie and paqman in particular, who didn't try to help but contest the OP.

---

### Post by nothingspecial on 2010-08-18
> **madchine said:**
> @nothingpsecial: Why are you assuming, that I was referring to your reply? My comment was on the general quality of replies to the OP, tclarkie and paqman in particular, who didn't try to help but contest the OP.

Just that my reply was the last reply

That`s all :D

---

### Post by nothingspecial on 2010-08-18
> **madchine said:**
> @nothingpsecial: Why are you assuming, that I was referring to your reply? My comment was on the general quality of replies to the OP, tclarkie and paqman in particular, who didn't try to help but contest the OP.

The answer from tclarkie is was it is.

Never, ever, disregard posts from paqman.

{S}He knows what {S}He`s talking about

Trust me :D

---

