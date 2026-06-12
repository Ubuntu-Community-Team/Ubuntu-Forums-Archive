---
title: "Change keyboard settting to Qwerty"
date: 2008-12-05
forum: New to Ubuntu
---

### Post by neigun on 2008-12-05
Hi Guys

this is my first posting so here goes!

Well everything seemed to be going OK until I tried to use the @ key (If you're wondering I'm using XP at the moment!). I've managed to connect to the net via my wireless router, set up my sound and graphics card but I've been defeated by my keyboard:-(

I'm currently using Ubuntu 8.1 and the Gnome(?) gui included with it. It's not a full install but currently running from my DVD drive. I've tried selecting a new keyboard from the drop down menu whilst in Gnome, but an option for a UK qwerty keyboard does not seem to exist.

Having done a number of searches- I now realise that Dvorak keyboards, one of the options in the drop down menu, seem to be in fairly wide circulation but I'd like to stick to my old Qwerty keyboard, at least for the time being.

Please be gentle with me- command lines are a little unnerving, hence my choice of Ubuntu.

TTFN Neil

---

### Post by jpoRS on 2008-12-05
I thought that a qwerty keyboard was the default?  Shrug.

Try this-

Open a terminal (Applications>Accessories>Terminal, I think)

put in

```
sudo dpkg-reconfigure xserver-xorg
```

Select the proper settings, and when in doubt go for the defaults.

How does that work?

jim

*edit:*I just reread your post and saw that you are a little iffy on the command line.  I don't know of a GUI way of reconfiguring xorg (what the above script does).  However the above command is really simple and nothing to be afraid of.

Step One: Open Terminal as described above.
Step Two: Enter the command, either by typing it in piece by piece or by pasting with <Ctrl>+<Shift>+V.
Step Three: Press Enter, put in your password.
Step Four: Follow on screen prompts.  When in doubt just go with the defaults and you should do fine, but if you know your hardware to require something else, set it appropriately.
Step Five: When you get to he Keyboard part of the configure, just set it to the appropriate keyboard for you, and your problem should be solved.

Good luck!

---

### Post by neigun on 2008-12-06
Thanks

I tried the command line quoted but xserver-xorg wasn't installed probably as I'm running Ubuntu live from a DVD drive.

Funnily enough I tried running the install and when I got as far as the keyboard option the default seemed to be qwerty. I have not proceeded to a full install yet as I want to clear my second hard drive for a dual boot system.

I'm a bit cautious as I tried Mandriva 2008 Spring and that's when the problems started. Mandriva's distro seems far more quirky and setting up the wifi connection was a little frustrating- to say the least. Partly as I had to install the Netgear drivers via third party software.

My initial thoughts of Ubuntu are it's good starting place for a newby like myself. Installing and testing the drivers for my graphics and sound card was easy. Ubuntu seems to be fairly intuitive, at least for for a former XP user (well shortly anyway!)

Thanks for the prompt advice.

Neil

---

### Post by clive littlewood on 2008-12-06
Hi

All English language keyboards are Querty.

When you press @ are you getting " instead ??

If you are then you have the USA keyboard.

Just go to System > Preferences > Keyboard and select UK

Hope this helps

Clive

---

### Post by pp. on 2008-12-06
When you boot from the live CD (and presumably DVD as well) you see a menu for about half a minute.

On the bottom of your screen there ought to be several options, among them options to set the language and the keyboard mapping to be used.

As far as I remember, F3 takes you to the selection of languages, F4 to the selection of keyboards.

---

### Post by neigun on 2008-12-06
Thanks everyone.

The keyboard had defaulted to US settings. When I looked into the gnome keyboard settings I'd focused on the Dvorak etc and missed the obvious generic UK!

Ubuntu is now installed and up and running.

):P

---

### Post by jpoRS on 2008-12-06
Well good!  Enjoy!

---

