---
title: "RhythmBox Crashes"
date: 2011-05-12
forum: New to Ubuntu
---

### Post by alexis44 on 2011-05-12
I only use it for the internet radio function.  As soon as I select a station, it crashes most of the time. Anything that I can change, or maybe another program that is compatible with Ubuntu?  :)

---

### Post by astex on 2011-05-12
I would suggest banshee.

---

### Post by hackb0y294 on 2011-05-12
You can try disabling various plugins in Rhythmbox (Edit > Plugins), and see if that works for you. The Portable Players - iPod plugin in particular is known for causing crashes.

---

### Post by alexis44 on 2011-05-12
I disabled some of the plugins and it didn't change anything.  I looked for Banshee, but all it had was a tarball, and I don't know how to use that.

---

### Post by ajgreeny on 2011-05-12
Banshee is in the repositories!  No need for tarballs.

Did you also install rhythmbox with a tarball?  If so, it could be the reason for the crashes.  Rhytyhmbox is also in the repos, and until natty was the default music player for ubuntu, so I presume that repository version is the one you are using.

---

### Post by astex on 2011-05-12
Open a terminal.

```
$ sudo apt-get install banshee
```

Type your password.  Run banshee.

---

### Post by alexis44 on 2011-05-12
> **ajgreeny said:**
> Banshee is in the repositories!  No need for tarballs.

Did you also install rhythmbox with a tarball?  If so, it could be the reason for the crashes.  Rhytyhmbox is also in the repos, and until natty was the default music player for ubuntu, so I presume that repository version is the one you are using.

I didn't know that Banshee was in the repositories.  I didn't see an option for internet radio there.  Do I need a plugin?  Rythymbox just came with my installation.

---

### Post by NoNameWill on 2011-05-12
Yes you need the live radio plugin. If you do it through terminal then the package is called banshee-extension-liveradio

This one will give you just about every plugin banshee-community-extensions

---

### Post by alexis44 on 2011-05-12
> **NoNameWill said:**
> Yes you need the live radio plugin. If you do it through terminal then the package is called banshee-extension-liveradio

This one will give you just about every plugin banshee-community-extensions

I tried the command and it didn't work.  Unless I'm looking in the wrong place, it wasn't added.

---

### Post by NoNameWill on 2011-05-12
sorry I should of had you do this :D

```
sudo apt-get install banshee-extension-liveradio
```or

```
sudo apt-get install banshee-community-extensions
```Now try it. Or you can install these through synaptic package manager.

---

### Post by NoNameWill on 2011-05-12
I re-read what you posted. It you installed those through terminal and can't find them in Banshee you have to active them by opening banshee<Edit<Preferences<Extensions

Now tick the extensions. You might have to restart banshee to get them to show up. Then start banshee click on liveradio. From there you will have to configure the plugins for each station block ie icecast/xiph, 365live, Realradio. I can't get Magnatunes to work though the live radio plugin but there is a magnatune plugin. If you installed all the community extensions then it will show up.

---

