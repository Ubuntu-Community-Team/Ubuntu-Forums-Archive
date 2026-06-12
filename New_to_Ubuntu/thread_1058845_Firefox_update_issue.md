---
title: "Firefox update issue"
date: 2009-02-03
forum: New to Ubuntu
---

### Post by Andy06 on 2009-02-03
So I was tweaking with my firefox update settings in Edit>Preferences>Advanced>Update

and when I unchecked "firefox" option, it greyed out and also greyed out thhe options for "when firefox updates are found". Now I cannot recheck them. Never happened in windows and seems like a bug maybe? I tried resetting the about:config entries for app.update.auto and app.update.enable but no luck. Shouldnt these entries revert the behaviour to default. 

Is this something to do with ubuntu updating firefox through the central updating system and hence it over rides firefox?

---

### Post by OrangeCrate on 2009-02-03
Yes, that's correct. Firefox updates come through the repositories.

---

### Post by Andy06 on 2009-02-03
Ok, but why then does it first give us the option to play with settings and then grey them out and thereby, lock us out of them.

I created a new profile to see what the default is and it again come up with everything available, then as soon as cleared the firefox update or auto download boxes, it greyed out and locked me out again. Tweaking the relevant about:config entries also doesn't do any good. I know I'm tweaking the right settings and to the right values because the same thing works on windows and if you keep your about:config page open while tweaking something in the preferences through GUI, it will immediately highlight and let you know what you changed in the about:config page.

IMO, it should either stay greyed out to begin with or not lock me out at all. What it does now seems buggy. Combined with the flickering bug and the random right click option selection bug, it gives a very poor impression since linux is firefox's "native" home isn't it. 

FF works perfectly on windows, never a hiccup...........

Whats worse is there aren't really too many alternative browsers on linux. No safari or [SIZE="1"]chrome or IE[/SIZE]:)
Opera isn't as great on ubuntu as it is on windows.

---

### Post by Temposs on 2009-02-04
Andy, there are plenty of alternative browsers to try out there, to be sure. Just search the repositories. Seamonkey, Konqueror, Epiphany, Galeon, Kazehakase, Arora, Netsurf, Dillo

I've never experienced the flickering bug you speak of, so I think it may be limited to certain hardware.

The thing with certain Firefox options being greyed out is to presumably give more tight integration with how Ubuntu works, with its update system. There is a particular package that enforces these changes. And you of course are able to remove it. I believe it is firefox-gnome-support. If you remove that, or maybe look at disabling the add-on called "Ubuntu Firefox Modifications", then you may get all the options available again. This is *not* a bug.

---

### Post by mikewhatever on 2009-02-04
You seem to have done a lot of tweaking to you Firefox on Ubuntu, so how is anyone supposed to know what's going on there. I mean, tweak as much as you like, but then don't complain that it's buggy. One more thing to note here, you seem to expect the tweaks you apply from Windows to work in Ubuntu, probably not quite realizing that Ubuntu is not Windows.

---

### Post by Andy06 on 2009-02-04
> Andy, there are plenty of alternative browsers to try out there, to be sure. Just search the repositories. Seamonkey, Konqueror, Epiphany, Galeon, Kazehakase, Arora, Netsurf, Dillo

Yeah I know, I tried seamonkey, Konqueror, Epiphany and Galeon before but to me they aren't Firefox or Opera competitors. I need the FF features:), it's just not nice to come to FF's native OS and find it works not as well as it does on non native ones.

> The thing with certain Firefox options being greyed out is to presumably give more tight integration with how Ubuntu works, with its update system. There is a particular package that enforces these changes. And you of course are able to remove it. I believe it is firefox-gnome-support. If you remove that, or maybe look at disabling the add-on called "Ubuntu Firefox Modifications", then you may get all the options available again. This is *not* a bug.

Tried that earlier before my post, dint work. Thing is once an option is changed, it changes its about:config entry, resetting the entry then does not undo the change, that would be a bug? Also the random right click selection is a documented bug and easily re-created, driving me insane hehe.

> You seem to have done a lot of tweaking to you Firefox on Ubuntu, so how is anyone supposed to know what's going on there. I mean, tweak as much as you like, but then don't complain that it's buggy. One more thing to note here, you seem to expect the tweaks you apply from Windows to work in Ubuntu, probably not quite realizing that Ubuntu is not Windows.

Nope, I created a new profile to test the theory, but it happens every single time. I dint say Ubuntu is windows but this doesnt have much to do with OS. Its the same app with the same about:config entries being changed, it should behave the same way.

---

### Post by OrangeCrate on 2009-02-04
If you haven't already done this, you could uninstall "ubufox" from Synaptic, and see if that makes a difference:

Package description...

> 
Ubuntu Firefox specific configuration defaults and apt support

Extension package for Firefox provides ubuntu specific configuration defaults
as well as apt support for firefox plugins/extensions.

[B]You can uninstall this package if you prefer to use a pristine firefox
install.[/B]


---

