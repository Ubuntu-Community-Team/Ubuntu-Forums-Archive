---
title: "Ultimate Edition 2.1 Theme Pack Uninstall"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Testrum on 2009-02-23
I installed Ultimate Edition 2.1 Theme Pack from gnome-look.org and it changed the splash screen when I start Ubuntu up. It came in a .deb package and installed some themes, I deleted the theme file thinking it'd get rid of everything but it hasn't :???: and now I'm stuck with a splash screen and a horrid theme.

Any suggestions?

---

### Post by hansdown on 2009-02-23
Hi Testrum.

It seems more complicated in 8.10, but here goes...

This tutorial may be helpful.

[http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html)

Go to applications> accessories> terminal, and copy and paste these commands into the terminal.

---

### Post by Testrum on 2009-02-23
> **hansdown said:**
> Hi Testrum.

It seems more complicated in 8.10, but here goes...

This tutorial may be helpful.

[http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html](http://www.ubuntugeek.com/how-to-change-the-bootsplash-in-ubuntu-810-intrepid-ibex.html)

Go to applications> accessories> terminal, and copy and paste these commands into the terminal.
Thanks, I'll give it a whirl and edit my post.

Edit: It helped but now I get a new error talking about a directory that isn't there. I looked for it couldn't find it. Oh well though I'll do a clean install tomorrow and have my Ubuntu back to normal in no time lol, except this time I'll be making a recovery partition once I have Ubuntu set up the way I want it :p

---

### Post by joey-elijah on 2009-02-23
Have you tried installing usplash? It normally lets you install/pick a different splash screen.

Also, not wanting to state the obvious, but did you try installing another theme after the other one messed up?

---

### Post by Testrum on 2009-02-23
> **joey-elijah said:**
> Have you tried installing usplash? It normally lets you install/pick a different splash screen.

Also, not wanting to state the obvious, but did you try installing another theme after the other one messed up?
Tried both and still no luck.

---

### Post by Mark Phelps on 2009-02-23
Did you try simply uninstalling the .deb package?

---

### Post by Testrum on 2009-02-23
> **Mark Phelps said:**
> Did you try simply uninstalling the .deb package?
That is what I did first.

---

### Post by TheeMahn2003 on 2009-03-05
Next time read:
Changelog:
Same as above, corrected 1000's of errors (permission problems) to make it lintian / Debian compliant, fixed sound issues 16 bit v/s 32 bit, Ubuntu needs to wake up ;) There will be one more release before I set it as final. I have tested it in Intrepid as well as Jaunty and works flawlessly. Hardy or less will not work as far as USplash (I do intend to check lsbrelease and if hardy or less not set usplash, then will be final).

I have installed it into UE 2.1 with 0 errors / problems (fresh ibex) as well all debs I have written. Now 46MB btw. It is now a 100% theme across the board and will take over on next boot.

If you wish to change it... it can be done as any other use sum if you wish to change the usplash, appearance System >> Preferences >> Appearance. System >> Administration >> Login for GDM.

Don't like the sound scheme? System >> Preferences >> Sound select "Sound" tab customize or change to your liking.

Hate it? sudo apt-get remove --purge ultimate-edition-theme-2.1

Final: I have successfully Built Ultimate Edition 2.1 using this package, it is w/o a doubt flawless ;) Ultimate Edition 2.1 is uploading. I did not fix hardy less, I have much on my plate. I suggest not installing it on hardy or less. If you do in order to get your usplash back you will have to use sum or similar.

Enjoy!!!

TheeMahn


Using hardy?  None the less:
> sudo update-alternatives --config usplash-artwork.so

---

### Post by eekfonky on 2009-03-26
I'm having similar problems with the .deb file. I uninstalled it but whenever I need to ctrl-atl-backspace to restart GNOME it says it cannot find the theme?! I do I set Human to default ina terminal, as I've done it through the GUI and all seems fine until I ctrl-alt-backspace. Please help

Thanks

---

