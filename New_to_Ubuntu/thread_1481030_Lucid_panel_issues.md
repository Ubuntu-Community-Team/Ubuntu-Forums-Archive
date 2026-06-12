---
title: "Lucid panel issues"
date: 2010-05-12
forum: New to Ubuntu
---

### Post by SteelCore on 2010-05-12
I'm facing some problems with the panels in Lucid. Every several reboots the network manager icon doesn't show and connection to the network cannot be established. Sometimes the username appears twice and the shutdown button gets covered. I normally have to reboot once or twice for the panel to go back to normal.
There is also a minor problem with the lower panel. Often I get a white strip right next to the 'show the desktop' button. This doesn't affect functionality and often gets resolved after a reboot.
The attached screenshots show these problems.
I would appreciate any help on how to report these issues.
Thanks

---

### Post by warfacegod on 2010-05-12
Instead of rebooting your system, try:

```
sudo restart gdm
```

Its not a fix but it will at least make things go faster than rebooting.

---

### Post by adam22 on 2010-05-12
I've had quirks like that, and it's probably because of the theme. Try installing one from gnome-look or using one of the one it comes with. Another cause might be a bad driver.

---

### Post by SteelCore on 2010-05-12
I'm actually using the default theme. As you said it is probably the driver.

---

### Post by warfacegod on 2010-05-12
Just for a goof, try adam22's idea. I seem to recall seeing that there are some issues with the default theme. I know the UNE panel has *allot* of problems and it uses the same theme.

---

### Post by piratemurray on 2010-05-14
Hi there, I'm having the exact same issues.

So the only way around this is to change theme?

Is there a bug open for this? I'll create one in a day if no one replies. I'll also create it against the ambience theme since from what I've read it doesn't seem to be an issue with the panels themselves

---

### Post by mjuhasz on 2010-05-19
> **warfacegod said:**
> Instead of rebooting your system, try:

```
sudo restart gdm
```

Its not a fix but it will at least make things go faster than rebooting.


I usually just activate the hide button on the panel, hide it and restore it. This way it is repainted.
I am experiencing the same issue on multiple installations. Compiz enabled with nvidia driver.

---

### Post by warfacegod on 2010-05-19
I don't *think* this is a Compiz issue. I very occasionally have this issue in 9.10 when I boot up, regardless of whether or not Compiz is set to autostart.

Using the hide buttons is a fine idea. Personally, I don't like having the hide buttons on my panel. The controls I use don't have transparency for them.

---

### Post by mjuhasz on 2010-05-20
I tried and it really happens without compiz and with the default nvidia nouveau driver as well. It is not a compiz or nvidia binary driver issue then.

---

### Post by warfacegod on 2010-05-20
Which leaves either (I think) gdm or nm-applet.

---

### Post by swizman on 2010-05-20
[http://ubuntuforums.org/showthread.php?t=1474932](http://ubuntuforums.org/showthread.php?t=1474932)

---

### Post by lidex on 2010-05-20
If this is an upgrade you may be experiencing cruft. Try a different theme and / or make sure you are up to date. I've seem some updates recently that fixed panel icons for me.
```
sudo apt-get update
sudo apt-get upgrade
```
Reboot if prompted, especially for new kernel.

For NM, have a look here:
[http://ubuntuforums.org/showpost.php?p=9236722&postcount=16]("http://ubuntuforums.org/showpost.php?p=9236722&postcount=16")

---

### Post by theozzlives on 2010-05-20
With the default theme, NM used to get replaced with a non-working volume icon. Since I downloaded a new theme... no problems.

---

### Post by cboteros on 2010-06-15
I also think the problem is in the theme, since I change the theme to any other and then back to Ambience and the problem gets solved.

I'm adding some screenshots to ilustrate the steps I take.

---

### Post by SteelCore on 2010-06-16
I changed to theme to 'Dust' instead of 'Ambiance' and still had problems though not as frequently. The attached screen shot is after my latest reboot. Note how the keyboard indicator has vanished.
BTW, Mjuhasz' solution to activate the hide buttons so as to repaint the panel is working fine for me, up to now.

---

