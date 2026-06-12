---
title: "e17 help"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by PatrickMoore on 2009-04-26
im trying to install e17 as an alternate desktop enviroment. following ruis pais instructions im stuck here

```
patrick@patrick-laptop:~$ sudo apt-get install e17-svn
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  e17-svn: Depends: giblib-dev but it is not installable
           Depends: libgtk1.2-dev but it is not installable
E: Broken packages

```

i need help

---

### Post by steve101101 on 2009-04-26
have you tried to install the two packages it says you need.

---

### Post by steve101101 on 2009-04-26
looking at my synapic you can install the 2 packages with the command 

sudo apt-get install giblib-dev libgtk1.2-dev

---

### Post by PatrickMoore on 2009-04-26
i did that and it was indeed effective however the actual windows manager will not open it redirects me into failsafe gnome instead. im confused as to why this wont work for me ha.

---

### Post by Tux Aubrey on 2009-04-26
> **PatrickMoore said:**
> i did that and it was indeed effective however the actual windows manager will not open it redirects me into failsafe gnome instead. im confused as to why this wont work for me ha.

I'm not sure, but maybe the e17 build process didn't finish or it was a bad revision (there's lots happening with e17 code right now).

When you have the time, try running the following from the Failsafe Terminal:
```

sudo easy_e17.sh -i
```

That will update and reinstall all components.

---

### Post by PatrickMoore on 2009-04-26
i am doing that now. i was wondering since i believe you are a contributor, is ozos still active? i liked that os i had it on my old laptop

---

### Post by Tux Aubrey on 2009-04-26
> **PatrickMoore said:**
> i am doing that now. i was wondering since i believe you are a contributor, is ozos still active? i liked that os i had it on my old laptop

Yes, still active - but we are having a few changes right now.  We'll do a RC based on Jaunty as soon as the e17 development cycle settles down (they'll freeze code, sort through bugs and do a "snapshot" very soon).  That should stop these bad installs!

The oz-desktop packages work OK on Jaunty, by the way.  If you get e17_svn installed OK, you can add the "other" oz repo and just install oz-desktop for the full shebang.  (Instructions are [HERE]("http://cafelinux.org/OzOs/content/how-install-ozos-desktop-existing-os"), just ignore the e17_svn stuff as you have done it already)

There are a couple of packages that won't install properly on Jaunty but they aren't critical and aptitude sorts it out just fine.

The initial setup is a bit confusing (due to some changes in e17 since we last updated the packages) and the default e17 desktop comes up instead of the "classic" OzOS one, but the tools (update, backup etc) are all OK and the oz themes work fine.

---

