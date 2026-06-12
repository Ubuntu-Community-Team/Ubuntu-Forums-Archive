---
title: "gdm themes"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by asal.mostafa on 2010-07-24
i'm ubuntu 10.4 user
and i don't know how to change my login screen
i already download a GDM-theme
[http://www.gnome-look.org/CONTENT/content-files/62964-Blubuntu-List.tar.gz](http://www.gnome-look.org/CONTENT/content-files/62964-Blubuntu-List.tar.gz)
this is it

---

### Post by davidmohammed on 2010-07-24
dont know if its directly possible to change the login screen interface itself - but you certainly can change the 'wallpaper' behind it.

see this[ link]("http://maketecheasier.com/change-login-and-boot-screen-in-ubuntu-lucid/2010/05/13") for more details.

---

### Post by Ony on 2010-07-24
I was about to post the same link ;-) Best of luck

---

### Post by Ony on 2010-07-24
Hi, [asal.mostafa]("http://ubuntuforums.org/member.php?u=1112734")

I don't recall seeing anything being mentioned about backing anything up before doing this maybe the person who posted before me, has some information on how to go about doing this just to be on the safe side.

Good luck

---

### Post by Fxy on 2010-07-24
Sorry but in the newer versions of ubuntu you cannot install custom "gdm" themes by default...  There is a way that you can install gdm themes on newer versions of ubuntu, though it is kind of tricky & as far as i can remember requires a few terminal commands.  Might be worth doing a few googles maybe ;-)  If installing gdm themes is a must, then you might want to look at older versions of ubuntu such as 8.04 etc etc ...

---

### Post by fooman on 2010-07-24
ubuntu tweak makes changing the login screen really simple:

[http://ubuntu-tweak.com/](http://ubuntu-tweak.com/)

---

### Post by Anuovis on 2010-07-24
GDM themes do not seem to be supported in 10.04 or 9.04
But I just downloaded Ubuntu Tweak, it works great.

Another way is possible if you want to change not only the wallpaper but the design of the bottom bar, etc. I found this somewhere on the net and have been using to tweak my own log in screen.

1. Logout of your current session (return to GDM, log-in screen)
2. Switch to the command line prompt using Ctrl-Alt-F1
3. Login using your normal login/password
4. at the command line prompt type: export DISPLAY=:0.0
5. then type: sudo -u gdm gnome-control-center
6. Switch back to the gdm screen using ALT-F7
7. The gnome-control-center should be loaded. Use it to configure your GDM
8. Click on the Appearances icon, in appearances you can change your GDM’s font, theme and background image
9. Close the gnome-control-center and login normally

---

