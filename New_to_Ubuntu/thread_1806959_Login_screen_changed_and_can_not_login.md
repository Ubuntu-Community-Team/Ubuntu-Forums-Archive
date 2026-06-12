---
title: "Login screen changed and can not login"
date: 2011-07-18
forum: New to Ubuntu
---

### Post by ryman90 on 2011-07-18
[FONT=Verdana]Hello[/FONT] everyone
I've recently installed  Ubuntu (10.10) using a LiveCD alongside Windows 7 and it was booting  fine until yesterday.Even now,the GRUB menu is displayed just fine but  now when I select the "Ubuntu 2.6.35-22 generic" option to boot into  Ubuntu,I see a login window with a blue and silver colored theme which  is different than the theme I had installed earlier.
My problem is I  cant login inspite of entering the correct password.I resetted the  password and tried but still the login window comes back to diplaying  the user prompt even when I've entered the correct password..Please help  me log back into Ubuntu without having to reinstall it all over again.
Any help given as soon as possible will be much appreciated..thank you..:)

---

### Post by sanderd17 on 2011-07-18
How did you reset the password?

It looks like you installed another DE (maybe KDE or LXDE), check if you can change back to gnome on the login screen.

---

### Post by ryman90 on 2011-07-18
> **sanderd17 said:**
> How did you reset the password?

It looks like you installed another DE (maybe KDE or LXDE), check if you can change back to gnome on the login screen.
I changed the password using this [http://ubuntuguide.net/reset-the-forgotten-password-in-ubuntu](http://ubuntuguide.net/reset-the-forgotten-password-in-ubuntu)
And as much i know,I didnt install any other Desktop Environment if thats what is meant by DE.
Definitely not KDE but I did try to change the theme by downloading some,though..
could that be the cause of the problem??

---

### Post by sanderd17 on 2011-07-18
the new theme will be the cause. You probably have installed a theme that is not compatible with your version of GDM (probably an old theme).

see if this works: [http://www.stchman.com/gdm_hangs.html](http://www.stchman.com/gdm_hangs.html)

Also, the numpad might not work in the terminal, so it could be that you typed the wrong password. Try to reset it to a pwd without numbers.

---

