---
title: "Why is /root/.local/share/recentlyused.xbel missing?"
date: 2011-06-22
forum: New to Ubuntu
---

### Post by unapendeza on 2011-06-22
I was trying to turn on numlock x and I was having difficulty so I followed the instructions in this thread:
[http://ubuntuforums.org/showthread.php?p=9198174#post9198174](http://ubuntuforums.org/showthread.php?p=9198174#post9198174)

After editing the file in gedit this is the output I get in the terminal:

$ gksudo gedit /etc/gdm/Init/Default

(gedit:2645): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.NRBXXV': No such file or directory

(gedit:2645): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

(gedit:2645): Gtk-WARNING **: Attempting to store changes into `/root/.local/share/recently-used.xbel', but failed: Failed to create file '/root/.local/share/recently-used.xbel.NSATXV': No such file or directory

(gedit:2645): Gtk-WARNING **: Attempting to set the permissions of `/root/.local/share/recently-used.xbel', but failed: No such file or directory

Why is /root/.local/share/recentlyused.xbel missing?

I tried to edit the same file using sudo nano instead of gksudo gedit as a command and I didn't run into the same warning, could someone explain to me what this means?

---

### Post by Extrm3 on 2011-06-30
I got the same problem, i even tried to manually make this file an still the warnings show up...

---

### Post by yetiman64 on 2011-07-01
I see those style of warnings all the time using gksudo gedit or even worse when using gksudo nautilus. I *_suspect_* it is because the root account is locked by default in Ubuntu. As a result root is not normally accessed by certain graphical apps and as such a lot of those files are generally not needed whereas they would be provided in a users account with user privileges.

I have ignored them here for the last few years and continued with whatever I am involved in at the time and so far it has never caused any problems. Occasionally with gedit and quite often with nautilus on exiting the program the terminal won't be released, in this case simply using the keys CTRL + C on the keyboard will release the terminal.

Hope this helps you. yetiman64

---

### Post by Vincent Vermeulen on 2011-07-03
By default /root/.local/share directory does not exist. The warning is given because a file can not be created if its directory does not exist. I solved this by running:

```
sudo mkdir /root/.local /root/.local/share
```

Which creates the directories gedit is trying to write in (gedit keeps a log of recently used files, and as you are running as root because of the sudo or gksudo command it is trying to write this in the root user homedir).

No more warnings from sudo gedit or gksudo gedit after this :-)

---

### Post by CatKiller on 2011-07-03
To add to the above, there are several reasons why *sudo nano* doesn't give the same errors as *gksudo gedit*. Firstly because nano doesn't try to keep track of recently used files and the like in the way that gedit does, which means it doesn't try to create those files, so it doesn't fail to do so, and so you don't get error messages about it.

Secondly, sudo uses *your* Home folder environment for settings while gksudo uses *root's* Home folder (/root). This means that if you run the kind of program that creates these kinds of files (largely graphical programs rather than command-line programs) then files in your Home folder will end up being owned by root. This can be a bad thing. In particular, if you run Firefox as root with sudo rather than gksudo you will no longer be able to run Firefox as a normal user without fixing the ownership of those files. Something to bear in mind.

FWIW, those error messages can be safely ignored. You aren't going to be running gedit as root all the time, so you don't especially care what documents you've recently opened. If the error messages bother you, you can make them go away by creating the directories that gedit needs, as outlined above.

---

### Post by Arny006 on 2011-11-23
> **Vincent Vermeulen said:**
> By default /root/.local/share directory does not exist. The warning is given because a file can not be created if its directory does not exist. I solved this by running:

```
sudo mkdir /root/.local /root/.local/share
```Which creates the directories gedit is trying to write in (gedit keeps a log of recently used files, and as you are running as root because of the sudo or gksudo command it is trying to write this in the root user homedir).

No more warnings from sudo gedit or gksudo gedit after this :-)

Thanks a lot, that avoid me further headeche.

By starting "gksudo"-command I got at first the "consolekit"-error. Solve the topic by install "consolekit" from [COLOR=Blue][here]("https://launchpad.net/%7Egnome3-team/+archive/gnome3/+packages").[/COLOR] After download and install appear in the "Ubuntu Software Center"  "Reinstall"-button. If you click the reinstall-button you will get an error-message, so, due the fact that "consolekit"-error don't come up any-more, I decide do decline the reinstall.

Again, thanks a lot, I hope other user have the "consolekit"-error find here the solution.

---

