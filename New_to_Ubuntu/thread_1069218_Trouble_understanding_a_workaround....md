---
title: "Trouble understanding a workaround..."
date: 2009-02-13
forum: New to Ubuntu
---

### Post by cosmicappuccino on 2009-02-13
I have a new installation of Intrepid Ibex on an HP Pavilion that's about 5 years old. I haven't gotten to use it all: as soon as I log in, I get stuck on a beige screen, with a responsive arrow cursor, and nothing else.

I think someone has found a workaround for my problem, and I'm not the only one it's happened to. However, being a newbie, I don't understand what to do to implement the workaround! If anyone could step me through this I'd really appreciate it.

I've copied the main part of the workaround here:

> My temporary workaround:
"Alt-Ctrl-F2" , "Login" by Textmode. "sudo rm /tmp/.X0-lock" , "startx" then it starts up OK, after that i "Enabled Automatic Login", under "System-->Administration-->Login Window".
My comuptor: Dell Latitude D520
(Also tried xserver-xgl)

...but if you want to view the whole thread, it's here: [https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/221850](https://bugs.launchpad.net/ubuntu/+source/gdm/+bug/221850)
(...and here's another related thread: [https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434](https://bugs.launchpad.net/ubuntu/+source/gnome-keyring/+bug/218434))

Thanks a lot for reading this!

---

### Post by spcwingo on 2009-02-13
It just means that when you boot and see the blank screen with only the cursor press CTRL+ALT+F2 at the same time.  This will exit X (the graphical side of Ubuntu).  You will then be asked to login via the text interface.  You will be able to see only your user name while typing, but not your password.  This is normal.  Then type the commands in like so:

```
sudo rm /tmp/.X0-lock
```(in .X0-lock it's a zero and not a capital "O")

and then:

```
startx
```

This should now bring up your desktop.  From there go to system>administration>login window  select the security tab and tick the checkbox beside "Enable Automatic Login".  Under "User" select your username from the drop-down.  Hopefully this sheds some light on your problem.

---

### Post by cosmicappuccino on 2009-02-14
Thank you for the really clear instructions, spcwingo!

...However, last time I tried Ctrl+Alt+F2 from the blank screen, nothing happened!

I have gotten a better keyboard and was going to try again, following spcwingo's instructions. BUT now I can't reach the login screen at all:

When I try to load Ubuntu, I have a black screen with white text being written across it. It pauses for some time on:

> * Starting hardware abstraction layer hald

...and then it moves on, and reaches:

> Bluetooth: SCO socket layer initialized

...and then, seems to stop completely.

Does anyone know anything I could try, to:
[LIST]
[*]reach the login screen, then
[*]log in to access my account rather than a blank screen
[/LIST]
...please? :confused:

---

### Post by cosmicappuccino on 2009-02-14
Anyone with any advice at all, please? :confused:

---

### Post by spcwingo on 2009-02-14
Have you tried any of the other F keys with the CTRL+ALT combo?  If not try CTRL+ALT+F1.  If that gets you to the terminal, proceed from there...if not, have you tried rebooting into recovery and choosing xfix?

---

### Post by cosmicappuccino on 2009-02-15
Ok, reinstalled completely, and now I'm back to the problem of the blank screen after login.

From the blank screen, neither Ctrl+Alt+F1 nor Ctrl+Alt+F2 does anything! Nothing happens at all.

I really want to get this to work but it just won't respond to anything that it's supposed to! :confused:

I've tried reinstalling several times, and burning the CD again. Always, the same problem! Does anyone have any idea what might be going on? 

Please?

---

### Post by spcwingo on 2009-02-15
If you're trying to install Intrepid...try Hardy.  If you're trying to install Hardy, vice versa.  Those releases have pretty different versions of xorg.  Intrepid fixed some problems for some, but also caused some problems for some.  This just might be one of the xorg bugs rearing it's ugly head.

---

### Post by cosmicappuccino on 2009-02-15
It worked!! Thank you so much for all your advice spcwingo! :)

---

