---
title: "How to automatically boot a program upon login"
date: 2010-02-16
forum: New to Ubuntu
---

### Post by magellancraig on 2010-02-16
Hello,
 
I would like to know how I can launch;
 
/home/simop1/X-Plane 9/X-Plane-i686
 
automatically after login. I saw how to do it in GNOME, but I didn't see anything for XFCE.
 
I tried /etc/bash.bashrc but I got a permission denied, even as su.
 
Thanks.

---

### Post by bwhite82 on 2010-02-16
I do not use XFCE but I will try to help. [According to Gentoo]("http://en.gentoo-wiki.com/wiki/Autostart_Programs"), XFCE has a graphical tool for this under: menu > Settings > Xfce 4 Autostarted Applications or a directory: ~/.config/autostart (if it doesn't exist, create it). I would read more at the link I've provided. You may need to create a simple bash script in the 'autostart' directory to autostart the program.

---

### Post by achase79 on 2010-02-16
Applications->Settings->Sessions & Startup
one of the tabs is "application autostart"
you can add it there

---

### Post by NightwishFan on 2010-02-16
Under the XFCE control panel, go to Sessions And Autostarted apps. Ignore the sessions tab, it is not what you want.

---

### Post by magellancraig on 2010-02-17
Thanks for the assist,
 
I went to "Applications", "Settings", "Session and Startup" and added x-plane there, but it dosen't comee up when booted....I still have to click the launcher. However, if I do the same thing under GNOME, x-plane starts right up when GNOME launches.
 
I probably should wirte a bash script....can someone tell me what to name the script, and where it should go? If there is an example of a launcher script I could look at, that would be great.
 
Thanks again for all the help!
 
Craig

---

### Post by bwhite82 on 2010-02-17
> **magellancraig said:**
> 
I probably should wirte a bash script....can someone tell me what to name the script, and where it should go? If there is an example of a launcher script I could look at, that would be great.
 

 
Craig

[http://en.gentoo-wiki.com/wiki/Autostart_Programs](http://en.gentoo-wiki.com/wiki/Autostart_Programs)

---

### Post by magellancraig on 2010-02-17
Soldierboy,
 
Awesome link. I think that will do it. Thanks.
 
Craig

---

