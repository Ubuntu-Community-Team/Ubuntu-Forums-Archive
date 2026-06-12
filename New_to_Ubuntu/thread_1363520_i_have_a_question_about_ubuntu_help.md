---
title: "i have a question about ubuntu help?"
date: 2009-12-24
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2009-12-24
i was playing this game the other day called onechanbara  and they had this weird mini game

and i thought to myself that would make an excellent boot screen for ubuntu

so is this possible at all


[http://www.youtube.com/watch?v=FlXG68hvU18](http://www.youtube.com/watch?v=FlXG68hvU18)
(this is the video game mini screen so u kno what im talking about)
 		                   		  		  		 		 			 				__________________

---

### Post by candtalan on 2009-12-24
> **pyrofreak99 said:**
> i was playing this game the other day called onechanbara  and they had this weird mini game and i thought to myself that would make an excellent boot screen for ubuntu
so is this possible at all
do you mean by boot screen - the screen display shown while booting, but before the desktop is shown fully? Or do you mean the desktop which is shown as wallpaper after the booting process is completed?

---

### Post by pyrofreak99 on 2009-12-24
yeah that one the whole  screen display shown while booting

---

### Post by candtalan on 2009-12-25
ok. I -think- it is this sort of thing:
[https://help.ubuntu.com/community/USplash](https://help.ubuntu.com/community/USplash)

hth

---

### Post by Anuovis on 2009-12-25
As of 9.10, you can not just install log-in themes any more.

I found these two solutions somewhere on the net and copied them. Did not take any notes on the sources, one was from this forum, another one from a blog somewhere. They both worked.

                                    <log-in background>

1. Logout of your current session and return to the GDM (or simply, just log out)
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: *export DISPLAY=:0.0*
5. then type: *sudo -u gdm gnome-control-center*
6. Switch back to the gdm screen using ALT-F7
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM’s font, theme and background image.
9. Close the gnome-control-center and login normally.



                                    <loading screen>

1. go to directory /usr/share/images/xsplash (you must login as root)
2. find image named bg_2560x1600.jpg
3. move this somewhere else for safekeeping
4. move the image you want as login background an this folder and rename bg_2560x1600.jpg

---

