---
title: "ALMOST ready to make Ubuntu my only OS but..."
date: 2009-03-12
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-12
I have a few small problems that I'd like to ask about first!

1) How do I get HDMI output to work with my ATI HD2600?

2) Will CS3 applications (namely Photoshop, Dreamweaver and Fireworks) work with Wine?

3) The play/pause | stop | next | previous media buttons work on my Toshiba, but the Internet and Media Player buttons do not. When I push "internet" it opens up my home folder in nautilus, and pushing "media player" does nothing. I have them configured correctly under System > Preferences > Keyboard Shortcuts but it still doesn't work..

4) When will the bug with compiz fusion + ATI + 3D/OpenGL = flicker be fixed?!!

5) Will there be a way in the next release to change the colour of the font in panels easily?

6) If I was to re-install Ubuntu, what things should I backup so that I can just go back to where I was on a new install? At the moment I am using the "Simple Backup" app which is backing up:

/var/
/home/
/usr/local
/etc/

Will this restore all of my applications, desktop background, panel settings etc?

7) Does Ubuntu run faster if you install it as the sole OS on its own partition instead of using Wubi?

Other than those listed above, everything works fine and I am super happy with Ubuntu!! Thankyou so much!

---

### Post by supersonicdarky on 2009-03-12
6) It would probably be easier to just have /home on a separate partition, so when you reformat, all setting stay

and instead of backing up the programs, back up list of programs you installed
other things to back up
- sources.list file
- any configs you edited under /etc/
- perhaps menu.lst as well

---

### Post by Ms_Angel_D on 2009-03-12
1)Unsure on this

2)I don't use CS3 But using wine-doors I have installed Dreamweaver 8, Fireworks 8, and Flash 8 also wine-doors supports photoshop cs2 9

3)Do  you have the proper keyboard selected under Preferences->Keyboard

4)Unsure

5)as far as I know you can do that now just customize the theme.

6)waiting for someone more experienced to help with the backup question.

---

### Post by humphreybc on 2009-03-12
> **MetalHellsAngel said:**
> 
3)Do  you have the proper keyboard selected under Preferences->Keyboard

I have "Generic 105" because my laptop is not listed there. The only Toshiba is the S3000.

> 
5)as far as I know you can do that now just customize the theme.

Customizing the theme DOES change the colour, but it changes the colour of EVERYTHING (including windows). I want white windows w/ black font and a black menu with white font.

---

### Post by humphreybc on 2009-03-12
> other things to back up
- sources.list file
- any configs you edited under /etc/
- perhaps menu.lst as well

Where do I find sources.list and menu.lst files?

---

### Post by ClaytonOT on 2009-03-12
> **humphreybc said:**
> Where do I find sources.list and menu.lst files?

> whereis sources.list /etc/apt/

> whereis menu.lst /usr/share/menu

---

### Post by humphreybc on 2009-03-12
Thanks. I just added question 7 too.

---

### Post by humphreybc on 2009-03-13
bump... I'd like question 7 answered :)

---

### Post by philinux on 2009-03-13
FAQ from wubi website.

> What is the performance?

The performance is identical to a standard installation, except for hard-disk access which is slightly slower than an installation to a dedicated partition. If your hard disk is very fragmented the performance will degenerate.


---

### Post by humphreybc on 2009-03-13
Ahh cool thankyou very much.

---

