---
title: "Removing mail icon from tray -&gt; sound widget also disappears"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by joffeloff on 2010-07-01
As the thread title implies.. I removed the mail icon in 10.04 as I had no use for such foolery, I use web mail. For some reason the audio icon also disappeared, and there is no audio or sound widget in the list of stuff to add to the panel.:confused:

How can I get back my volume adjuster thingy?

---

### Post by joffeloff on 2010-07-04
Hello guys.. Still no joy.

Any suggestions?

---

### Post by gandaran on 2010-07-04
which software did you remove, evolution-indicator and what else?
check if indicator-applet is still installed

---

### Post by warfacegod on 2010-07-04
Right click your Panel> select Add to Panel> find Indicator Applet and add it.

To get rid of just the envelope, you need to remove the indicator-messages package with Synaptic or the Terminal.

---

### Post by SoFl W on 2010-07-04
The indicator applet is one with the evolution mail applet.  Sorry about that, you are not the first to complain, and wont be the last.  (It sucks)
To get BOTH back right click on the panel->  Add to panel-> and add indicator applet.

---

### Post by cetoka on 2010-07-04
Remove the indicator applet,which will remove both the mail and the sound applets.
Open a terminal and write: ''*gnome*-*volume*-*control*-applet[I]''
Which will add a volume applet as a start-up program.At the next reboot you will see the new sound applet.
[/I]

---

### Post by treehermit on 2011-04-22
here's your fix:

```

[COLOR=#3366ff]**sudo apt-get remove evolution-indicator**[/COLOR]


```

---

### Post by stevek123 on 2012-03-03
Thanks - volume widgit is back & evolution is gone

---

### Post by Mcron on 2012-03-03
> **joffeloff said:**
> As the thread title implies.. I removed the mail icon in 10.04 as I had no use for such foolery, I use web mail. For some reason the audio icon also disappeared, and there is no audio or sound widget in the list of stuff to add to the panel.:confused:

How can I get back my volume adjuster thingy?

Add the indicator applet to the panel, it includes the mail icon and sound.

---

### Post by oldos2er on 2012-03-03
Closed, necromancy.

---

