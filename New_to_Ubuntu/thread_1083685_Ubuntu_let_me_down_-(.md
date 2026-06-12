---
title: "Ubuntu let me down :-("
date: 2009-03-01
forum: New to Ubuntu
---

### Post by bobigeorge on 2009-03-01
Dear friends,

I have asked for help on this matter before...

When I log on to Ubuntu 8.10 my theme automatically changes into a strange theme and when I try to change it through System -> Preferences->Appearance it shows this error message

```
Unable to start the settings manaUnable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.ger 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
```

Please help me out on this problem.. I have been always boasting around about the advantages of Ubuntu over Vista.. But now a days ubuntu is more annoying me than vista do!!!!(Please take your time to read this [http://ubuntuforums.org/showthread.php?t=1083661](http://ubuntuforums.org/showthread.php?t=1083661) post also)

Thanks in advance...

---

### Post by Ms_Angel_D on 2009-03-01
A [google search]("http://www.wikihow.com/Search-Google") for [your error messages]("http://www.google.com/search?num=50&hl=en&ei=oJ2qSbrsH4HasAOVucXtDw&sa=X&oi=spell&resnum=1&ct=result&cd=1&q=Unable+to+start+the+settings+mana+Unable+to+start+the+settings+manager+%27gnome-settings-daemon%27.&spell=1") turned up these threads you might wanna try what they suggest.

[http://ubuntuforums.org/showthread.php?t=579167](http://ubuntuforums.org/showthread.php?t=579167)
[http://ubuntuforums.org/showthread.php?t=189961](http://ubuntuforums.org/showthread.php?t=189961)

---

### Post by kansasnoob on 2009-03-01
I'd try:

```
sudo apt-get install --reinstall ubuntu-desktop
```

Then:

```
sudo apt-get -f install
```

Then restart.

---

### Post by Ben Page on 2009-03-01
This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.ger 'gnome-settings-daemon'.

Error says it all, have you recently installed window manager? Have you installed KDE or xfce?

Try installing the compiz fusion icon app, it gives you the choice to select a window manager. Select metacity and try then.

---

### Post by bobigeorge on 2009-03-02
Dear MetalHellsAngel,

I have already tried above links and no help....

---

### Post by bobigeorge on 2009-03-06
no help????!!!!!

---

### Post by redseventyseven on 2009-03-06
> **bobigeorge said:**
> Dear MetalHellsAngel,

I have already tried above links and no help....

Well, can you describe what actually happened when you followed those instructions? Which instructions did you follow? What happened?

It's difficult to make any further suggestions when no details of what happened after the first suggestion are provided.

---

