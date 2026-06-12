---
title: "ctrl+alt+F2 and no more GNOME"
date: 2010-07-28
forum: New to Ubuntu
---

### Post by FostyStudent on 2010-07-28
I was working on compiling and installing some software to install on my computer running 10.04 and I went to hit ctrl+alt+T for a new terminal window but my brain must have misfire because I accidentally hit ctrl+alt+F2 instead. I got launched into the console and just used the reboot command (and I now know of ctrl+alt+F7) and now when it boots, I see the default wall paper and cursor but that's it. Nothing else happens. Any suggestions? (Aside from clean install?)

---

### Post by jrothwell97 on 2010-07-28
Welcome to the Forums!

Try logging in at the terminal you get when hitting Ctrl+Alt+F2, and run the following command:

```
sudo stop gdm && sudo start gdm
```

If this doesn't work, it might be because something went horrendously wrong during the software compilation/installation (probably if you were doing a *make install*) - in this case, tell us what you were trying to compile and we'll do our best.

---

### Post by FrostyStudent on 2010-07-28
Sorry. I was having issues with my username/password (aside from the typo)

I tried that and I still get the same thing. It seems like the login window and toolbar just aren't appearing so it would have made sense to restart gdm. But for some reason it didn't help.

There weren't any actual compilings running but I was working on installing openSSL in order to install open SSH. I got openSSL installed but openSSH said it couldn't find the openSSL library. I found a possible solution for it else where on the forums but didn't have a chance to try it.

---

### Post by linux18 on 2010-07-28
the fast way:

ctrl+alt+f7


The long but sure way:


STEP 1:
-choose recovery mode at grub

STEP 2:
-drop to a root prompt

STEP 3:
-type: 
```

telinit 3

```
 and login

STEP 4:
-then type:
```

 xinit

```

STEP 5:
-when xinit starts type:
```

metacity &

```
- for ubuntu OR:
```

compiz &

```
- if you have it OR flux/openbox & - if you have it OR:
```

fvwm4 & 

```
- for xubuntu

STEP 6:
-then type:
```

 gnome-panel & 

```
-for ubuntu OR:
```

 xfce4-panel & 

```
-for xubuntu

STEP 7:
-lastly type:
```
 
nm-applet & 

```
-for networking

======================================================

---

### Post by FrostyStudent on 2010-07-28
Well it got me to the desktop but it looks very bare bones... Any suggestions on where to go from here to get it back to how it was before?

EDIT: And thanks for that!

---

### Post by linux18 on 2010-07-28
usually when you manually start it like in my post, restarting the computer will bring everything back to normal.

---

### Post by FrostyStudent on 2010-07-28
Sadly, all you see in the screen shot is all I get...

---

### Post by linux18 on 2010-07-28
If the screenshot is all you get when you reboot, then all of the components are loaded, just not configured, you can change your background/theme and generally bring it back to normal.

---

### Post by FrostyStudent on 2010-07-28
When I boot into recovery mode (or even when I don't it appears on the screen anyway while Ubuntu is loading on top of the purple) I get for lines that appear on screen that say

```
            [   19.551057] codec_read: codec 0 is not valid [0xfe0000]
[   19.558060] codec_read: codec 0 is not valid [0xfe0000]
[   19.565205] codec_read: codec 0 is not valid [0xfe0000]
[   19.572206] codec_read: codec 0 is not valid [0xfe0000]
```

It appears as though it is still showing the command line and is displayed on top of the recovery menu. When I scroll through the recovery menu, it disappears to display the menu but anything on the side of the menu is still displayed.

---

### Post by FrostyStudent on 2010-07-28
But that is when I follow your instructions. It still won't boot normally. I still get the log in screen without the login window.

---

### Post by llamabr on 2010-07-28
If you create a new user, does that new user also have the same trouble?  If so, you screwed up a dot file, or some other config file.

---

### Post by nmaster on 2010-07-28
> **linux18 said:**
> the fast way:

ctrl+alt+f7




in case anyone else reads this thread in the future.  this is all that should have been done.  the other advice is more complicated than it needs to be.  CTRL+ALT+F1 ... CTRL+ALT+F6 take you to virtual terminals (no X, no GUI ).  CTRL+ALT+F7 takes you back to the X environment.

---

### Post by FrostyStudent on 2010-07-29
It isn't a problem with the user profile because the login window/user list doesn't appear when I boot the computer. When I get to where it should be, I just get the wallpaper and cursor.

Would it be possible to just reinstall the core system while leaving profiles, programs, and preferences in tact?

---

