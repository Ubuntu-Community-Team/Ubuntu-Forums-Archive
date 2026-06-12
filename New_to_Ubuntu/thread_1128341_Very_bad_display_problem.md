---
title: "Very bad display problem"
date: 2009-04-17
forum: New to Ubuntu
---

### Post by fslezak on 2009-04-17
I have a terrible display problem.:(:(:( I was installing a second monitor on a IBM 600x running 8.04. When I logged in, my Usplash was fine, but when I saw my login screen, it had many colored bars and was a 600x800 view instead of my 1024x768 view. It was also very fuzzy as in my desktop. When I logged in, all of the colors on the screen were different. I REALLY NEED HELP!

---

### Post by Twitch6000 on 2009-04-17
It seems like it needs to know there is a new screen attached. Go into recovery mode and type xfix or fixx(I forget which it is) and that should reset your video settings.

After doing so then all you will need to do is reinstall your graphics card and problem solved.

---

### Post by fslezak on 2009-04-17
It knows that the monitor is there. I now do not want to use my second monitor anymore.

P.S. How do you reinstall your graphics card?

---

### Post by markofealing on 2009-04-17
Reboot Ubuntu, and chose recovery mode. From the recovery menu select fix xorg, this will give you a fresh xorg.conf file. Your existing one will be saved, make a note of the file name.

Alternatively, you can edit your xorg.conf file from terminal by entering sudo gedit /etc/X11/xorg.conf.

---

### Post by fslezak on 2009-04-17
There is no fix xorg command

---

### Post by markofealing on 2009-04-17
> **fslezak said:**
> There is no fix xorg command

I've just checked mu Ubuntu 8.10 laptop:

1. From the GRUB menu select recovery mode
2. From the recovery menu select XFIX to fix X server. This is at the bottom of the menu i.e. last item.

Once done your will be returned to this menu, select the first option, Resume normal boot.

---

### Post by fslezak on 2009-10-16
BUT, how can I install the monitor without having to run XFIX again???

---

### Post by overdrank on 2009-10-16
> **fslezak said:**
> BUT, how can I install the monitor without having to run XFIX again???

Hi and can use reach the terminal with the ctrl, alt, F1 keys? Login and use the command ```
sudo dpkg-reconfigure xserver-xorg
``` Then you can use the command ```
sudo /etc/init.d/gdm restart

```
Edit you may also use the command using the alt, F2 keys  gksu displayconfig-gtk and adjust the resolution.

---

