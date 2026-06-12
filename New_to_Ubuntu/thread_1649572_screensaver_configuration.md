---
title: "screensaver configuration"
date: 2010-12-20
forum: New to Ubuntu
---

### Post by ebcovert3 on 2010-12-20
Ok, this is dumb. I am trying to change the background color on the Fuzzyflakes screensaver from that pepto pink to blue. Here is my modified .desktop file for the program:
```

[Desktop Entry]
Name=FuzzyFlakes
Exec=/usr/lib/xscreensaver/fuzzyflakes -root -color "blue"
TryExec=/usr/lib/xscreensaver/fuzzyflakes -color "blue"
Comment=Falling colored snowflake/flower shapes. Written by Barry Dmytro.
StartupNotify=false
Terminal=false
Type=Application
Categories=Screensaver
OnlyShowIn=GNOME;
```

However, when i run:
```
 /usr/lib/xscreensaver/fuzzyflakes 
```
it still comes up pink. I can run:

```
 /usr/lib/xscreensaver/fuzzyflakes -color "blue" 
```
and it comes up fine, but I can't get the normal screensaver to do it without manually invoking it from the CLI.

Advice?

Thanks!

---

### Post by psychoelf on 2011-01-14
Any luck?  

I like fuzzy flakes, but Ubuntu screen savers in general lack options, and a pink background sucks for snowflakes.

Would be nice to let it run for winter ambiance.

---

### Post by ebcovert3 on 2011-01-23
Nope. The pink seems a bit silly. I ended up using Flying Toasters instead. Went old school. LOL

---

### Post by gmargo on 2011-01-23
> **ebcovert3 said:**
> 
However, when i run:
```
 /usr/lib/xscreensaver/fuzzyflakes 
```it still comes up pink. 

You ran the screensaver directly, without going through the .desktop file, so of course the default pink color showed up.

Your .desktop edits to add the -color blue option are fine, but if you want the changes to work through the gnome screensaver, you have to refresh the desktop cache (/usr/share/applications/desktop.en_US.utf8.cache).  Use this command to do so:
```

sudo dpkg-reconfigure python-gmenu

```After that the gnome screensaver will start the Fuzzy Flakes with the blue background.  You can also specify the color in RGB form, like "-color #FF0000" for red.

---

### Post by ebcovert3 on 2011-01-23
Thank you very much. Now when I pull up the screensavers menu, I have the desired color for fuzzyflakes. However, whenever I lock the screen (which invokes the selected screensaver), it is still pink.

Thoughts?

Thanks again!

---

### Post by gmargo on 2011-01-23
> **ebcovert3 said:**
> it is still pink.
I saw the exact same thing.  Right after I posted that message!  I rebooted, and now the screensaver is in the specified color (red in my case).  Perhaps I could have changed the screensaver to another, and then changed it back?

---

### Post by ebcovert3 on 2011-01-23
I tried switching them around, but no joy. However, rebooting the machine did the trick. Thanks.

---

