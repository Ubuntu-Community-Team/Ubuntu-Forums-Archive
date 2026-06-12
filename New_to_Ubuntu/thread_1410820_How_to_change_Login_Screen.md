---
title: "How to change Login Screen"
date: 2010-02-19
forum: New to Ubuntu
---

### Post by iggy pop on 2010-02-19
Could someone tell me how i might change the Login Screen please. Thanks

---

### Post by Julita on 2010-02-19
In System -> Administration -> Login Window -> Login Window Preferences -> Local

---

### Post by Anuovis on 2010-02-19
Depends on what you want to do. I suppose you want to change the appearance. 
These two guides worked for me, first one for everything about the actual log-in screen, second one for changing the background of loading-into-desktop screen.
             
                                  <background>

1. Logout of your current session (return to GDM, log-in screen)
2. Switch to the command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using ALT-F7
7. The gnome-control-center should be loaded. Use it to configure your GDM
8. Click on the Appearances icon, in appearances you can change your GDM’s font, theme and background image
9. Close the gnome-control-center and login normally



                                    <loading screen>

1. Go to directory /usr/share/images/xsplash (you must login as root)
2. Find image named bg_2560x1600.jpg
3. Move this somewhere else for safekeeping
4. Move the image you want as login background an this folder and rename bg_2560x1600.jpg

---

### Post by 123456789123456789123456 on 2010-02-19
The second post was correct.  you can change the theme, and the login window, and other actions from that menu.  You can also use the third post, but that would take a while.
you can also find more themes online.

---

### Post by Anuovis on 2010-02-19
> **Julita said:**
> In System -> Administration -> Login Window -> Login Window Preferences -> Local

I can not do this on 9.10. The menu entry that is mentioned here only has two options, either an automatic login or a login screen where you can select users. There is no GUI for changing the appearance, at least not there on my system.

---

### Post by Julita on 2010-02-19
To get back the options that I have mentioned, do this:
1. Logout of your current session and return to the GDM
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using ALT-F7
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM's font, theme and background image.
9. Close the gnome-control-center and login normally.
([http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html](http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html))

---

### Post by MooPi on 2010-02-19
This was graciously offered through the forum:
[http://ubuntuforums.org/showthread.php?t=1358026&highlight=gdm-setup.py](http://ubuntuforums.org/showthread.php?t=1358026&highlight=gdm-setup.py)
Great theme changer.

---

