---
title: "compiz failing"
date: 2010-01-17
forum: New to Ubuntu
---

### Post by quarkhirad on 2010-01-17
After installing ubuntu 9.10.

I went to system--> preferences-->appearance and set the effects to custom. It asked to install drivers for my graphics. after installing them i restarted and could set the appearance to custom.   

I then changed some seetings using compiz config setting manager like desktop cube no of virtual deskops, Annotate, Paint fire on screen etc. Now when i restart my comp and log in the setting in appearances is none. I have to select custom and then my settings take effect. Help this was not the case in my ubuntu 9.04.

---

### Post by piattos on 2010-01-17
Try adding 'compiz --replace' to your startup programs. (System > Preferences > Sessions)

---

### Post by quarkhirad on 2010-01-17
Thanks for the suggestion but still no luck. Any other suggestion. Please help

---

### Post by piattos on 2010-01-17
Are you sure you added it correctly? (Put it in the 'Command' field and without the single quotes. Make sure it's also checked.)

---

### Post by arnab_das on 2010-01-17
i hope u have setup the cube right.

check this link for screenshots, make sure your settings are exactly like the ones shown here.

[http://exploreubuntu.wordpress.com/2009/11/14/getting-compiz-to-work-on-ubuntu/](http://exploreubuntu.wordpress.com/2009/11/14/getting-compiz-to-work-on-ubuntu/)

---

### Post by quarkhirad on 2010-01-17
No i solved the problem by doing the following 

1. Logout of your current session and return to the GDM
2. Switch to the tty command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using ALT-F7
7. The gnome-control-center should be loaded. Use it to configure your GDM.
8. Click on the Appearances icon, in appearances you can change your GDM's font, theme and background image.
9. Close the gnome-control-center and login normally.

Note i got this from the following site:

[HTML]http://www.ubuntumini.com/2009/09/hack-karmics-gdm-login-screen.html[/HTML]

Note i dont know how it has rectified the problem. I know it has because now whenever i restart my ubuntu my desktop effects are as i want it. Since i dont know how it worked i dont suggest that anyone does it. 

Ps: can someone explain how this has worked. 

Also a second thing i have enabled the animations feature and in its options i have checked all the effects. Howerver whenever i open or close or minimize an application there is no effect. I had this effect in 9.04 so i know how it looks. Can anyone suggest what could be the reason.

---

### Post by quarkhirad on 2010-01-17
> **quarkhirad said:**
> No i solved the problem by doing the following 


Also a second thing i have enabled the animations feature and in its options i have checked all the effects. Howerver whenever i open or close or minimize an application there is no effect. I had this effect in 9.04 so i know how it looks. Can anyone suggest what could be the reason.




Oops should have first read [http://exploreubuntu.wordpress.com/2...ork-on-ubuntu/](http://exploreubuntu.wordpress.com/2...ork-on-ubuntu/)

Cool page thanks man.

:guitar:  :D

---

