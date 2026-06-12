---
title: "Emerald Themes Help"
date: 2009-03-22
forum: New to Ubuntu
---

### Post by abeautifulplace on 2009-03-22
I just installed the emerald theme manager, as far as I can tell it's working just fine. I've imported a few themes, but the only problem is that when I click on a theme, nothing happens, and emerald freezes.

Any idea what's wrong?
(i'm using 8.10)

---

### Post by overdrank on 2009-03-22
> **abeautifulplace said:**
> I just installed the emerald theme manager, as far as I can tell it's working just fine. I've imported a few themes, but the only problem is that when I click on a theme, nothing happens, and emerald freezes.

Any idea what's wrong?
(i'm using 8.10)

Hi and after selecting the theme, use the alt, F2 keys and enter ```
emerald --replace
``` to activate

---

### Post by abeautifulplace on 2009-03-22
After I do that, nothing happens :(

---

### Post by overdrank on 2009-03-22
> **abeautifulplace said:**
> After I do that, nothing happens :(

Ok are you using the using the visual effects ( compiz) as emerald needs the effects to work.

---

### Post by abeautifulplace on 2009-03-22
I'm not sure, How could I enable that?

---

### Post by overdrank on 2009-03-22
> **abeautifulplace said:**
> I'm not sure, How could I enable that?

Have a look at the The Great Desktop Effects FAQ of 2009 link in my signature :)

---

### Post by abeautifulplace on 2009-03-22
> **overdrank said:**
> Have a look at the The Great Desktop Effects FAQ of 2009 link in my signature :)
Hmmm, When I try to enable desktop effects, It says they cannot be enabled.

(edit)
Ran compiz-check, this is what I get:
```
Gathering information about your system...

 Distribution:          Ubuntu 8.10
 Desktop environment:   GNOME
 Graphics chip:         ATI Technologies Inc Rage Mobility M4 AGP
 Driver in use:         Unknown
 Rendering method:      AIGLX

Checking if it's possible to run Compiz on your system...

 Checking for texture_from_pixmap...               [ OK ]
 Checking for non power of two support...          [ OK ]
 Checking for composite extension...               [ OK ]
 Checking for FBConfig...                          [ OK ]
 Checking for hardware/setup problems...           [FAIL]

There has been (at least) one error detected with your setup:
 Error: Software Rasterizer in use
```

---

### Post by overdrank on 2009-03-22
> **abeautifulplace said:**
> Hmmm, When I try to enable desktop effects, It says they cannot be enabled.

Ok have you installed the drivers for you graphics card? System, administration, hardware drivers.
What is the model of the graphics card?
You can use the command lspci in the terminal located under applications, accessories. Look for VGA and that is the graphics card.

Edit, just saw your edit and I do not believe that graphics card will support the desktop effects.

---

### Post by abeautifulplace on 2009-03-22
> **overdrank said:**
> 
Edit, just saw your edit and I do not believe that graphics card will support the desktop effects.
Well, That explains it. 
Before I tried using Emerald themes, I downloaded a few GTK2 themes from Deviantart, But I couldn't seem to get those to work either.

(edit)
I'm wondering if [this guide]("http://ubuntuforums.org/showthread.php?t=581620") will work?

---

