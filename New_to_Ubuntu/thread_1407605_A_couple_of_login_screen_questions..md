---
title: "A couple of login screen questions."
date: 2010-02-15
forum: New to Ubuntu
---

### Post by Flying Pikachu on 2010-02-15
Hello Everyone, 

I have a couple of questions I need answered, 

Q1. I'm running ubuntu 9.10 and yesterday I wanted to install a couple of different desktop environments... so then i installed xubuntu-desktop (xfce) and kubuntu-desktop (KDE) using the terminal. I log-off to switch to a different desktop environment and see that the GDM was replaced with XSplash (Xubuntu Login Splash) and also the boot up was replaced with the xubuntu logo. i then looked around and found how to change the boot-up so i did and now the boot-up is back to normal.

I was wondering how to change it back to the normal GDM.

P.S I have already reinstalled ubuntu-desktop and it didn't seem to work.

**QUICK EDIT: **I just reinstalled ubuntu again, so i do not need question 1 answered anymore but you are free to still answer it in-case anyone else has the same problem :popcorn:

Q2. This is another question about the login screen and the simple question is how to i change the resolution of it? My desktop is at 1280 X 1024 and the log-in screen is at 1280 X 960 because when i log-in it slows the computer down when it has to change resolution (it is as not as seamless as it would be if there in the same resolution.)

P.S.S Ubuntu 9.10 does not use X11 because i have already tried that and you cannot change it in the log-in settings in System ----> Administration -------> Log-in screen

Please any help would be appreciated and thanks for your time. ;)

---

### Post by jcoles on 2010-02-15
I'm also curious about the answer to this one. I get a 4:3 image on my widescreen monitor and it shifts sideways, as you describe. Before 9.10, there were actually some options configurable from the login screen itself. The new login screen is completely dumbed down and unconfigurable. Unfortunately, much of 9.10 is like that. 

In the menus, there is System > Configuration > Login screen. Pathetic. Almost completely useless, it covers so little. 

For a login screen, I don't really want every user listed on a menu. A simple dialog with Username and Password fields like I had in previous releases would be ideal. Is there some way to get that? 

We need good configuration tools, or at least a good guide to the configuration files we'll have to play with. 

Unfortunately, 9.10 is a step backwards in configurability.

---

### Post by Flying Pikachu on 2010-02-16
> **jcoles said:**
> I'm also curious about the answer to this one. I get a 4:3 image on my widescreen monitor and it shifts sideways, as you describe. Before 9.10, there were actually some options configurable from the login screen itself. The new login screen is completely dumbed down and unconfigurable. Unfortunately, much of 9.10 is like that. 

In the menus, there is System > Configuration > Login screen. Pathetic. Almost completely useless, it covers so little. 

For a login screen, I don't really want every user listed on a menu. A simple dialog with Username and Password fields like I had in previous releases would be ideal. Is there some way to get that? 

We need good configuration tools, or at least a good guide to the configuration files we'll have to play with. 

Unfortunately, 9.10 is a step backwards in configurability.

Jcoles, I agree with you on this. Ubuntu should put the login configuration back to what it was at 9.04 and every user listed is a good thing or a bad thing dependant on what the situation is. For example, my younger brother and sister which are only (5 and 8 ) would not remember the username (or maybe even password...) very well and it was alot easier for them to click their name ***but on the other hand ***if i owned a big company and all my employees had a networked account, i wouldn't want a big list of names on the log-in screen.

In 10.04 ubuntu should really put the old login screen configuration and an option to either display all the users names or for you to enter your username and password manually,    

Also if you didn't get my quick edit, i do not need question 1 answered anymore but everyone is still free to answer it incase anyone else needs it (or it happens again :P )

---

### Post by Flying Pikachu on 2010-02-21
Bump! Does anyone have any ideas how to get this fixed?

Thanks

---

### Post by JiuJitsu500 on 2010-02-21
You can change to log-in screen picture resolution.... and btw I had the same issue when I installed xfce and kubuntu :) solved it in the package manager by re-installing "ubuntu-desktop" or something... solved the menu clutter by editing scripts individually by adding "STARTONLYIN=GNOME, KDE, XFCE" etc... or something similar..

Anywho though, screen resolution I have no idea, but picture resolution is easy, you getting the thing where it shows the splash, changes resolution for the log-in, then goes back to the original splash until the desktop boots?

---

### Post by JiuJitsu500 on 2010-02-21
Well, screw it.... I should have added instructions sorry :) first set a root password (type "sudo passwd" in a terminal)

I don't want to insult intelligence... but to edit the splash pictures/animation, etc... press Alt+F2 and type "gksu nautilus" to change you to root, and open up the wonderful nautilus (as root, thusly files are easily modifiable)... navigate to filesystem/usr/share/images/xsplash and put your picture here as the first one on the list in your resolution (just add an "a" or "1" in front of the name).... this edits the xsplash....

To create total awesome fully-seamless login experience from the heavens.... at the log-in screen press CTRL+ALT+F1 (maybe F2...) to open a terminal... and log in, then type (case sensitive) "EXPORT DISPLAY=:0.0" without the quotes, then "gdm gnome-control-center" and a bunch of crazy stuff will fly by, then stop.... now press CTRL+ALT+F7 to exit the termianl, and be in the gnome control center for the login screen :) add the same image you put in the xsplash folder to the background, set it... and VIOLA!!!! Just make sure the images are in your desktop's resolution.....

worked for me like 4 times now anyway... and if theres an easier way excuse my ignorance please :) hope I helped man!

Oh and yeah... I do agree about the not eaily modifiable login screen... that was seriously something to ponder about....

---

### Post by Flying Pikachu on 2010-04-30
I have now upgraded to 10.04 and it's still the same but now the bootup screen is the correct resolution but changes back to the wrong one at the login screen and changes back to the correct one when i login.

BTW loving 10.04 :) :)

---

