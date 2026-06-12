---
title: "[SOLVED] Desktop needs adjusting or something"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by MelL on 2008-12-07
I decided today to switch over to KDE for my GUI, and after logging in after installing it, I noticed that the desktop was going off of either side to the left and right. Using the monitor's, a Gateway EV700, little control proved to be futile, though I did get one side to show up. I've tried looking at the xorg.conf file, but I have no idea what is ideal.

Any suggestions, hopefully something simply for a Linux newbie? :)

Mel

---

### Post by Yuki_Nagato on 2008-12-07
First, try this:

You seem to know where the xorg file is, so hop into Terminal, (or Konsole now) and rename the file.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

This will back up your xorg.conf file and leave nothing in its place.  X can run with out a config file, so we will see if that fixes things.

Close all applications, and either restart the computer, or restart X with "Ctrl + Alt + Backspace" (not Delete).

Did it work?  No?

If that did not work, try this:

```
system-config-display --reconfig
```

This supposedly will create a fresh, new xorg.conf file for you.  Restart X again.  And yes, it seems as if no xorg.conf is better than an xorg.conf with errors.

---

### Post by abn91c on 2008-12-07
does you monitor have an auto-adjust button? try pressing that also check in system settings>display check screen resolution, set to 60mhz

---

### Post by MelL on 2008-12-07
> **Yuki_Nagato said:**
> First, try this:

You seem to know where the xorg file is, so hop into Terminal, (or Konsole now) and rename the file.

```
mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

This will back up your xorg.conf file and leave nothing in its place.  X can run with out a config file, so we will see if that fixes things.

Close all applications, and either restart the computer, or restart X with "Ctrl + Alt + Backspace" (not Delete).

Did it work?  No?

If that did not work, try this:

```
system-config-display --reconfig
```

This supposedly will create a fresh, new xorg.conf file for you.  Restart X again.  And yes, it seems as if no xorg.conf is better than an xorg.conf with errors.


The first command re-centered my desktop, though it is still extended offscreen. The second command resulted in:

bash: system-config-display: command not found

and sudo came up with:

bash: system-config-display: command not found



> **abn91c said:**
> does you monitor have an auto-adjust button? try pressing that also check in system settings>display check screen resolution, set to 60mhz

Unfortunately, there is no auto-adjust button, only a dial to make changes. Also, I can't find a menu option of 'system settings.'

---

### Post by dracayr on 2008-12-07
boot in recovery mode (esc at startup if you don't have a dual boot), and choose "fix X server"

dracayr

---

### Post by MelL on 2008-12-07
> **dracayr said:**
> boot in recovery mode (esc at startup if you don't have a dual boot), and choose "fix X server"

dracayr

I did as you instructed and came up with the same desktop. Here is what it looks like, just so you can get a better idea of what it might be.

[[IMG]http://img231.imageshack.us/img231/4786/desktopmu6.th.png[/IMG]](http://img231.imageshack.us/my.php?image=desktopmu6.png)

Edit: Rubbish! Treacherous screenshot!

If you were sitting in front of the machine, you would not be able to see the clock and most of the 'Start' button would be gone as well.

---

### Post by MelL on 2008-12-07
> **dracayr said:**
> boot in recovery mode (esc at startup if you don't have a dual boot), and choose "fix X server"

dracayr

I did as you instructed and came up with the same desktop. Here is what it looks like, just so you can get a better idea of what it might be.

[[IMG]http://img231.imageshack.us/img231/4786/desktopmu6.th.png[/IMG]](http://img231.imageshack.us/my.php?image=desktopmu6.png)

Edit: Rubbish! Treacherous screenshot!

If you were sitting in front of the machine, you would not be able to see the clock and most of the 'Start' button would be gone as well.

---

### Post by abn91c on 2008-12-07
Unfortunately, there is no auto-adjust button, only a dial to make changes. Also, I can't find a menu option of 'system settings.'[/QUOTE]

in kubuntu if you have the kickoff menu, applications tab>system>system settings

---

### Post by abn91c on 2008-12-07
Not sure if I missed it but what version Kubuntu you have, is it 8.04 or earlier, if so then alt+f2 then type kcontrol, you can adjust the display settings there, make sure you hit administrative mode button then set aspect ratio to 4:3 if you have a regular crt monitor or a non wide screen monitor

---

### Post by MelL on 2008-12-08
> **abn91c said:**
> Not sure if I missed it but what version Kubuntu you have, is it 8.04 or earlier, if so then alt+f2 then type kcontrol, you can adjust the display settings there, make sure you hit administrative mode button then set aspect ratio to 4:3 if you have a regular crt monitor or a non wide screen monitor

I am using Ubuntu 8.04 Hardy.

The problem seems to have fixed itself. I started my Ubuntu machine and the desktop is fully on the screen now, with no overhang. Maybe it took a night of me sleeping for it to see the error of it's ways.

Anyway, thank you all for the suggestions and advice on how to fix it!

---

