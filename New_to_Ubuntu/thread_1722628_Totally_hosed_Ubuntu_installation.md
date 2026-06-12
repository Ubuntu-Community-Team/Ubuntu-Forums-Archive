---
title: "Totally hosed Ubuntu installation"
date: 2011-04-06
forum: New to Ubuntu
---

### Post by Learning Linux 2011 on 2011-04-06
Hi,

What do you do if your Ubuntu installation gets hosed?  What are some steps to get it working again?  What are some troubleshooting tips?

---

### Post by Rasa1111 on 2011-04-06
Guess it all depends on what you did and where you're at now?
:???:

Ive hosed an installation or 2 myself..
and being more of a newb than a pro...
My "fixes" were to re-install. :lol:

---

### Post by Learning Linux 2011 on 2011-04-06
> **Rasa1111 said:**
> Guess it all depends on what you did and where you're at now?
:???:

Ive hosed an installation or 2 myself..
and being more of a newb than a pro...
My "fixes" were to re-install. :lol:


:lol:  Heh, well in this case I tried to install a third party theme called "Elementary".  It didn't work right and I tried to uninstall it, and then my system got screwed up.  Now, Ubuntu boots to a graphical (GNOME) login screen, prompts me to log in, but then when I do, it acts like it logs me in, but then just gives a warning sound and boots me out, like the graphical interface cannot load.

I was also kind of wondering if there are just general things one can do, like booting from a CD, looking for specific files or failures, editing certain files, replacing things, etc.  Things like that.

---

### Post by jamesidw on 2011-04-06
> **Learning Linux 2011 said:**
> :lol:  Heh, well in this case I tried to install a third party theme called "Elementary".  It didn't work right and I tried to uninstall it, and then my system got screwed up.  Now, Ubuntu boots to a graphical (GNOME) login screen, prompts me to log in, but then when I do, it acts like it logs me in, but then just gives a warning sound and boots me out, like the graphical interface cannot load.

I was also kind of wondering if there are just general things one can do, like booting from a CD, looking for specific files or failures, editing certain files, replacing things, etc.  Things like that.
I'm no guru but i think the fix always depends on the problem. But about the general things you can do, I recommend ```
fsck
``` for machines that wont start and ```
computer-janitor
``` for problems like yours.Neither is a "silver bullet" by any stretch of the term

---

### Post by rosencrantz on 2011-04-06
Well, there's always the text-based login with Ctrl+Alt+F1 (or F2, F3 etc.) Ctrl+Alt+F7 usually gets you back to your graphical session.

Change to the text interface with Ctrl+Alt+F1. Log in with your username and password.

I don't think your system is hosed, it just looks like gnome doesn't particularly like the theme you installed or you uninstalled a bit too much/little, or the gnome configuration files now point to a nonexisting theme.

First idea:
There should be a file called '.themes' in your home directory. Rename it to something else, e.g.
[FONT="Courier New"]mv .themes .oldthemes[/FONT] 
Gnome will not find the renamed file and hopefully initialise a new one with default settings.

Try to restart gnome with [FONT="Courier New"]gdm-restart[/FONT] If that doesn't work, reboot with [FONT="Courier New"]sudo /sbin/shutdown -r now[/FONT]

If renaming doesn't work:
Did you install the theme via synaptics or apt-get (I can see there is a repository for elementary) and was that all you did? (no configuration changed etc.?)

If you can't remember what packages you installed last, type
[FONT="Courier New"]tail -n 500 /var/log/dpkg.log | grep 'install '
tail -n 500 /var/log/dpkg.log | grep 'remove '[/FONT]
This will display those from the last 500 lines in your installer log files that contain the word 'install' or 'remove'. Identify those causing trouble with the aid of the logged installation time and the package name.
A typical line would be (from my logs)
```
2011-04-05 19:11:07 install openfoam171 <none> 0-1ubuntu2

```
To uninstall you need the <package name> right after 'install', in this example 'openfoam171'.
Try to revert all your changes with [FONT="Courier New"]sudo apt-get remove <package name 1> <package name 2> <...>[/FONT] or [FONT="Courier New"]sudo apt-get install <package name 1> <package name 2> <...>[/FONT] for every package that caused trouble.

If you still don't get a graphical interface after re-login and/or if you remember further configuration steps, we'll have to figure out where the config files are.
Cheers, rosencrantz

---

### Post by gerowen on 2011-04-06
Try deleting your Gnome settings from a terminal.  Here's how to do it.

1) From the login screen, press CTRL+ALT+F1 and you'll get to a terminal.

2) At this terminal run:
```

rm -rf .gnome .gnome2 .gconf .gconfd .metacity

```

3) Return to a graphical session with CTRL+ALT+F7

4) Log in, your Gnome should be reset to its out-of-box state.

---

### Post by HermanAB on 2011-04-06
Well, if /home is a separate partition, then you can simply re-install and *not* format /home.

If your /home is not a separate partition, then you should make it one the next time you install.

---

### Post by rosencrantz on 2011-04-06
@Herman: The thing is, his install is probably salvageable. And if the config files in /home are screwed up, re-installing Ubuntu might not even solve his problem.

---

