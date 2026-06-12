---
title: "a way to check my laptop temperature?"
date: 2009-06-29
forum: New to Ubuntu
---

### Post by heyyy on 2009-06-29
i mean graphic card(nvidia) and cpu(intel centrino)

---

### Post by unutbu on 2009-06-29
Install the lm-sensors package, then open a terminal (Applications>Accessories>Terminal) and type
```

sudo sensors-detect
```

Say yes to all the questions, and then, to check the laptop temperature, type
```

sensors
```
(You might get a bit of information the first time; more information after you reboot).

---

### Post by heyyy on 2009-06-30
> **unutbu said:**
> Install the lm-sensors package, then open a terminal (Applications>Accessories>Terminal) and type
```

sudo sensors-detect
```

Say yes to all the questions, and then, to check the laptop temperature, type
```

sensors
```
(You might get a bit of information the first time; more information after you reboot).
 
thanks can i have something like a gadget on my screen showing this?

---

### Post by Paqman on 2009-06-30
> **heyyy said:**
> thanks can i have something like a gadget on my screen showing this?

Try installing sensors-applet, it'll let you add an applet to a panel.

---

### Post by unutbu on 2009-06-30
If you are using a gnome panel, you can install the sensors-applet package, then right-click on the gnome panel and select "Add to Panel". Add the "Hardware Sensors Monitor" applet.

You can configure what it displays by right-clicking the applet and selecting "Preferences".

Also, some Ubuntu users like to use the conky package to custom design monitors that live in the background root window. This is a world and adventure unto itself. A tempurature monitor can be displayed by conky as well. For an example of stuff people do with conky, see

[http://conky.sourceforge.net/screenshots.html](http://conky.sourceforge.net/screenshots.html)
and this venerable megathread: [http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)


If you are interested in trying this and have time to kill, here is a [URL="]http://ubuntuforums.org/showthread.php?p=6365702"]
HOWTO Guide[/URL]

---

### Post by superprash2003 on 2009-06-30
i use the command **acpi -t ** for cpu temp

---

### Post by Mikael P. on 2009-07-02
I just found this applet but I got stuck when trying to customize it. For some reason I only get access to my graphics card temperature. There are no options for adding the CPU.
All the requirements where a bit beyond me (I am learing this ubuntu stuff).
How do I go about adding controls for displaying my CPU too?

---

### Post by unutbu on 2009-07-02
Have you installed lm-sensors and run "sudo sensors-detect"?
(as described in post #2).

---

### Post by Mikael P. on 2009-07-02
RTFM. no I hadn't done that. Cheers for bearing with me.
It works fine now!

---

