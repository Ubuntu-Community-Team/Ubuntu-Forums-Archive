---
title: "Login Loop?"
date: 2010-06-25
forum: New to Ubuntu
---

### Post by p22dude on 2010-06-25
I just installed Xubuntu on an old Dell Inspiron Laptop. The laptops has a 1.7 ghz Pentium IV, and less than 512 MB RAM. The laptop display does not work, so it is currently hooked up to an external monitor via VGA. I installed Xubuntu side-by side with XP, on my very low capacity 20 GB HDD. I had no problems during install, and was configuring settings for appearance, window manager, etc. when my screen blacked out and then forced me to the login menu. Upon entering my correct login information, the dialog box dissappears, a white Xubuntu logo shows up, and the computer returns to the login screen with no error message. I have no experience in Xubuntu, but have about a year's worth in Ubuntu, both on 9.10, and 10.04.

Any help would be much appreciated.

---

### Post by Friend-Atish on 2010-06-25
Hi,

Have you changed the display resolution during, configuring the xubuntu ?

---

### Post by p22dude on 2010-06-25
No, I believe it defaulted to something like 1680 x 1050. It's on a roughly 20" widescreen flat panel monitor. I attempted to lower the resolution on the Live CD (before install) to 1280 x 1024, and it basically crashed, the screen went black etc. I had to force the PC to shut down, even though I know my monitor supports this resolution.

---

### Post by linux-hack on 2010-06-25
just try reconfiguring the xserver-xorg and may be even KDE or I don't rely know witch desktop environment is on the Xubuntu.

---

### Post by p22dude on 2010-06-25
> **boogy9 said:**
> just try reconfiguring the xserver-xorg and may be even KDE or I don't rely know witch desktop environment is on the Xubuntu.

Xubuntu uses the xfce desktop environment. Does that help?

---

### Post by linux-hack on 2010-06-26
Actually you have the same commands .. you just do :

```
sudo gpkg-reconfigure xfce
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by p22dude on 2010-06-26
> **boogy9 said:**
> Actually you have the same commands .. you just do :

```
sudo gpkg-reconfigure xfce
sudo dpkg-reconfigure xserver-xorg
```

I entered "sudo gpkg-reconfigure" *enter*

then at the sudo prompt I put "xfce"

and got

"no command 'xfce' found: did you mean:

command 'xfe' from package xfe (universe)
command 'xpce' from package 'swi-prolog-xpce' (universe)
command 'xfte' from package 'fte-xwindow' (universe)

for the 'xorg' one I got a similar error. Does it make a difference if I booted into a shell vs running a terminal in recovery mode low-graphics mode?

Thanks.

---

### Post by linux-hack on 2010-06-26
after the sudo dpkg-reconfigure dont hit enter copy paste the commands as I wrote them..

the prompt of the sudo is for the admin password.

---

### Post by WinRiddance on 2010-07-02
> **boogy9 said:**
> after the sudo dpkg-reconfigure dont hit enter copy paste the commands as I wrote them..

the prompt of the sudo is for the admin password.


The second line was accepted for me, but not the first sudo line. For the first sudo line I received a "command reconfigure not found" message. Oh, and when you log in as root from the recovery mode the "sudo" isn't even needed since you're already at the highest admin level.

**Bottom line,** I have the same problem as described by p22dude. Under xfce settings I changed the Theme to Albatross which worked without a problem. But then I went into the Window Decorator (think that's where it is, not the one with all of the opacity/transparent adjustments)) and wanted to change the "stuff" (don't even know what those things are) from Albatross to something else in that huge long list.
_The instant that I did that the system froze up completely._ Couldn't do anything at all except for a hard reset. The login came back up as described by p22dude. Every time that I log in I can see the mouse change to whatever color/size I had previously selected in the settings, but then it changes right back to the login screen a moment later. **No errors** or anything else.


**Here's a [COLOR=DarkRed]working solution[/COLOR] that I found for [COLOR=DarkRed]Xubuntu[/COLOR] users ...**

>[I] When you get to the log in screen, Select your user,
[/I]>[I] then on the bottom, there should be a 'Session' field, click the
[/I]>[I] drop-down menu and select '**xterm**', then type in your password, and
[/I]>[I] login, you should be presented with a terminal. (mine was upper left of the screen)
[/I]>[I] Once, there enter the following commands into the terminal:
[/I]
[I]$ mv .config/xfce4 DOTconfig_xfce4
[/I][I]$ mv .cache/xfce4 DOTcache_xfce4
[/I][I]$ exit

[/I]>[I] That should log you out, then log back in, remembering to change the
[/I]>[I] Session field to 'Xfce4 Session' after you select your user but before
[/I]>* you enter your password.*[I] Those two commands should give you a stock xfce4 session

[COLOR=DarkRed]**NOTE:**[/COLOR]  [/I]The seond line did not work for me as I received an error message. However, I did go ahead and
exit the terminal session as described, followed by selecting the user login with the xfce session,
which then provided me with the very fast xfce desktop. From there I was able to get back into the
xfce-settings in order to undo what I did previously. Then I logged off, followed by logging in with the
Xubuntu session ... and everything was fine once again. I did have to redo some of my session settings
but most of the stuff, including custom background, came back as I had left it.
Thanks to Linux registered user 425915 for this information.
Hope this helps someone out there ....

---

