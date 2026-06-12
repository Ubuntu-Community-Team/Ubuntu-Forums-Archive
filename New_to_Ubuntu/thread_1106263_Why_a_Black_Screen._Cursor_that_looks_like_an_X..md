---
title: "Why a Black Screen.?? Cursor that looks like an X.??"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by Edgar09 on 2009-03-25
Hello.....
Iam new at Ubuntu 8.10 & i have problem.......
Like 5 days ago i changed something on the login window appearence... it will go through the normal boot stuff (all that white text, "Starting System" or whatever, and even the black loading screen with the orange progress bar and "Ubuntu") then it gos to a black screen.!! And the cursor has a shape of an X..

In other words i cant get to my desktop....
I removed compiz,gnome & i think even grub..... but i still cant get to my desktop.... Ubuntu Pros.!! i need help.....

---

### Post by damis648 on 2009-03-25
First, don't remove compiz, it's part of ubuntu (ubuntu-desktop), just don't use it if you don't need it. Second, you couldn't have removed GRUB or else you wouldn't be able to boot at all. Third, you removed gnome? Are you sure about that? If you removed gnome, than that is entirely your problem. You can't just remove gnome, that IS the graphical environment. To try and fix this, let's do a few things:
Press Ctrl+Alt+F1. You will be thrown into a TTY asking for login. Login using your username and password. (For security reasons, you will see no text when typing your password) Now, from here, type the following:
```
sudo apt-get install ubuntu-desktop
```
if it installs something, then you should be okay. Just type in
```
sudo /etc/init.d/gdm restart
```
and see if it works now. If nothing installs (it tells you that it is already at the newest version) then try this:
```
sudo /etc/init.d/gdm stop
sudo /usr/share/recovery-mode/options/xfix
```
and now finally
```
sudo /etc/init.d/gdm restart
```
and see if that fixes it.

---

### Post by Edgar09 on 2009-03-25
Nothing happened... Nothing changed... i did evertything.!
it says...........
xserver-xorg post inst warning: overwriting possibly-
customised configuration
file; backopin /etc/X11/xorg.conf.20090325141205

& then i wrote the last command but nothingg.....
What should i do.???????:confused:

---

