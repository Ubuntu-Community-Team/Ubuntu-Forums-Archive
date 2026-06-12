---
title: "Request help with Update Manager"
date: 2009-07-10
forum: New to Ubuntu
---

### Post by m9ke on 2009-07-10
Update Manager is popping up daily.  Sometimes it has updates I need, and I am glad to get them.
Other times it only has updates for software I have uninstalled (gstreamer) or software I don't need (a driver for a printer I don't own).

I looked at the Update Manger prefs and searched this forum but did not see this problem.

Is there a way to tell Update Manager, "I don't want that update, and please stop suggesting it"?

---

### Post by Western Digital on 2009-07-10
I don't believe it's possible to ignore updates. There seems to have been bugs opened against most Ubuntu flavors. I would definitely like this feature.

---

### Post by nothingspecial on 2009-07-10
Alt + F2

Type ```
gconf-editor
```

Go apps > update notifier >

Uncheck auto_launch

---

### Post by earthpigg on 2009-07-10
> **m9ke said:**
> 
Is there a way to tell Update Manager, "I don't want that update, and please stop suggesting it"?

uninstalling the packages you dont want is one option. many will be part of a metapackage. you can remove that metapackage. *this is not something people commonly do*, but it *is* an option if downloading stuff you dont want/need is bothering you.

many of them will likely be a part of a big metapackage, and removing that _**can**_ be scary. a metapackage is a package that is nothing but a big list of 'dependencies'. 

meaning if you have the ubuntu-desktop package (it is a metapackage), it will make you keep what the ubuntu developers consider to be essential to the standard ubuntu desktop installed - including printer stuff that you may not want/need. you are in disagreement with the ubuntu developers, in other words.

if you have the ubuntu-desktop metapackage installed, then you will have suchandsuch installed.

removing ubuntu-desktop doesn't remove anything in itself, but it will give you the freedom to remove other stuff. it just axes the giant 'must-have' list that contains things that _**you**_ dont think you 'must-have'.

_be cautious_, however, as it will also give you the freedom to break your system.

to remove ubuntu-desktop:

```
sudo apt-get remove ubuntu-desktop
```

then, open up synaptic and start uninstalling things you think you dont need.

if things start going awry, and you want ubuntu-desktop back (including all the stuff you got rid of that you previously could not):

```
sudo apt-get install ubuntu-desktop
```

keep in mind, if you remove a package that was not part of the ubuntu-desktop metapackage by mistake.... installing ubuntu-desktop again will not bring that back.

does all of that make sense?



many people, however, find it easier to start thin and build up than to start with the fat full ubuntu-desktop and do a liposuction procedure. that is where ubuntu minimal comes in -- your install will come with nothing but a command line and networking.

---

### Post by m9ke on 2009-07-10
nothingspecial, thanks!

It looks like the fix you suggested will globally prevent Update Manager from launching unless I launch it. 

Is that correct?

---

### Post by nothingspecial on 2009-07-10
Yep

However updates are important and now you will not be prompted.

It is a good idea to run

```
sudo apt-get update
```

```
sudo apt-get upgrade
```

about once a week.

---

### Post by earthpigg on 2009-07-10
ooooooo, thats what you wanted!

i thought you wanted to not be bothered by _**specific**_ updates for stuff you dont want/need lol

yes, what nothingspecial said will do that :D

---

### Post by m9ke on 2009-07-10
earthpig, thanks!

I am looking for a way to individually say 'no thanks, don't ask again' to *individual* items.  For example, Update Manager always asks if I want a driver for a printer I don't own.

Maybe the gstreamer stuff is more complex, but for the case of the printer driver I am hoping there is a simple way to nix it that I have over looked.

---

### Post by nothingspecial on 2009-07-10
If you really want to stop updates of this kind then you can look at [[COLOR="Magenta"]pinning[/COLOR]]("https://help.ubuntu.com/community/PinningHowto") but in all honesty I wouldn`t worry about it.

---

### Post by earthpigg on 2009-07-10
> **m9ke said:**
> 
I am looking for a way to individually say 'no thanks, don't ask again' to *individual* items.  For example, Update Manager always asks if I want a driver for a printer I don't own.

Maybe the gstreamer stuff is more complex, but for the case of the printer driver I am hoping there is a simple way to nix it that I have over looked.


ok, ya.... uninstall ubuntu-desktop and start uninstalling packages (like the printer package you dont want).

if a package is installed, it will seek updates for it - that is part of having that package installed.


if you can uninstall what you dont want *without* removing ubuntu-desktop, then that would probably be preferred.... but ubuntu-desktop includes everything and the kitchen sink, so that is probably not the case.

---

### Post by nothingspecial on 2009-07-10
Do not uninstall ubuntu-desktop unless you know what you are doing.

---

