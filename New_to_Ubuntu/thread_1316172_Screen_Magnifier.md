---
title: "Screen Magnifier"
date: 2009-11-05
forum: New to Ubuntu
---

### Post by smitty96 on 2009-11-05
I was messing with the login screen and turned on the screen magnifier. It made half of my screen a big version of the other half, and now I can't turn it off, because it's covering the half that the options button was on. Help!

---

### Post by akelsall on 2009-11-05
> **smitty96 said:**
> I was messing with the login screen and turned on the screen magnifier. It made half of my screen a big version of the other half, and now I can't turn it off, because it's covering the half that the options button was on. Help!

Sounds like you have enabled something in Compiz. Either way, you may just want to reboot and get back where you were. You can try "Ctrl+Alt+Backspace" to reload your desktop (but be aware any unsaved work will be lost).

If that don't work, you can try to bring up a console by press 
Ctrl+Alt+F1 (I think that's the correct sequence. It might be Ctrl+F1). You'll know you have a console window because you will see a black screen with text and a shell prompt ($ or %). From there, try entering **reboot** to gracefully reboot your PC (again, all unsaved data will be lost).

---

### Post by smitty96 on 2009-11-05
Rebooting didn't help. The settings are still the same.

---

### Post by kansasnoob on 2009-11-05
Can you go to System > Preferences > Preferred Applications and click on the Accessibility Tab?

Make sure all options are unchecked.

Basically same thing at Sys > Pref > Assistive Technologies.

---

### Post by smitty96 on 2009-11-06
That doesn't help either, its only on the login screen, not my desktop.

---

### Post by smitty96 on 2009-11-06
I found the solution, just had to delete the program. ;)

---

### Post by Joelmac on 2009-12-03
> **smitty96 said:**
> I found the solution, just had to delete the program. ;)

How did you delete it?  what's the program called?

I'm having the same problem, but my system hangs when the magnifier is activated.  Had to hold the power button to shut if off.  Now when I start up I hear the sound for the login screen, but then I see half the screen go black and nothing else happens, there's no mouse cursor, I can't do anything.

Is there a way to get control of the system before the login screen starts to load?  Does anyone know how to fix this?

Thanks.
Joel

EDIT:
I found my way to the command prompt by continually pressing Ctrl+Alt+F1 while booting.  I'm not really sure what combination of those keys got me there.  I'm logged in, but I'm still unsure as to how to start the GUI, or disable the login screen's magnifier.  I tried "startx" and got the following:
------------------------------------------------------------------------------------------
Fatal server error:
Server is already active for display 0
    If this server is no longer running, remove /tmp/.XO-lock
    and start again.

ddxSigGiveUp: Closing log
Invalid MIT-MAGIC-COOKIE-1 keygiving up.
xinit: Resource temporarily unavailable (errno 11):  unable to connect to X server
xinit:  No such process (errno 3): Server error.
------------------------------------------------------------------------------------------

Does that mean anything to anybody?  Thanks!


EDIT:
Tried again, was able to reboot cleanly from the command prompt.  It booted normally without activating the magnifier so everything is back to normal. :)

Joel

---

### Post by aramodo on 2010-01-11
I'm still having this problem. :-(... Same thing... fiddling around. I've removed Orca and disabled all compiz fusion magnifying components. 

It happened when I clicked "magnify" in the accessibility options on the login screen. Now half the screen is magnified, and the magnified area covers the button I clicked to enable the magnifier, so it's not clickable.

Does anyone know what configuration file this would be in?

---

### Post by cheysmith on 2010-01-26
I ran into the same problem. It seemed to have locked up my login screen.

At first I ran the following but it did not solve my problem.

```
sudo dpkg -P gnome-orca
```Then I tried this and it did the trick.

```
sudo dpkg -P gnome-mag
```After purging the gnome-mag package I rebooted and my login screen was back to normal. :popcorn:

---

### Post by MarkK. on 2010-04-26
For me, I went to the spilt log in screen, clicked on the accessibility icon, bottom right and left of the date. This brought up a menu, I unchecked; use on screen keyboard, use on screen reader and use on screen magnifier. Clicked close. I loggged in,out and back in with the correct, non split login screen.

---

### Post by satyanash on 2010-06-30
> **cheysmith said:**
> I ran into the same problem. It seemed to have locked up my login screen.

At first I ran the following but it did not solve my problem.

```
sudo dpkg -P gnome-orca
```Then I tried this and it did the trick.

```
sudo dpkg -P gnome-mag
```After purging the gnome-mag package I rebooted and my login screen was back to normal. :popcorn:


Very cool what the second command actually does is it just removes the magnifier application.. AND THAT'S IT  now next time you log on you still have assistive technologies and the options to enable the other feature excluding the magnifier !!!

---

### Post by bl1ndm0nk on 2010-11-14
> **cheysmith said:**
> I ran into the same problem. It seemed to have locked up my login screen.

At first I ran the following but it did not solve my problem.

```
sudo dpkg -P gnome-orca
```Then I tried this and it did the trick.

```
sudo dpkg -P gnome-mag
```After purging the gnome-mag package I rebooted and my login screen was back to normal. :popcorn:
Thank you very much for the tip.  
My 2 4y.o. twins are always trying to get a hold of the laptop to play GCompris  or enigma when we are not around. I ended up locking laptop, but when they are trying to hack into it. - I was getting half screen without ability to login. :confused:
so now i am a happy customer.
Thanks.):P

---

### Post by Binayak on 2011-06-07
for ubuntu 9.10 and above user
open terminal and write

cd /usr/share/gdm/autostart/LoginWindow
sudo rm gnome-mag.desktop

logout to see the difference....

---

