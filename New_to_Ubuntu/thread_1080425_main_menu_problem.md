---
title: "main menu problem"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-02-25
when i open the main menu add/remove all i get is an icon showing all and none of the applications that i have installed. any idea how to fix/tks cheesemaker -note i cant even search for any apps

---

### Post by rburkartjo on 2009-02-25
have found this fix but cant fiqure out how to do and this problem occurs for both users on this computer. see the last post
[http://ubuntuforums.org/showthread.php?t=1075294&highlight=main+menu](http://ubuntuforums.org/showthread.php?t=1075294&highlight=main+menu)

---

### Post by llamabr on 2009-02-25
Have found the solution under Ubuntu wiki alacarte. Renamed folder .local/share/applications and .config/menus to reset the menu.

Are you having trouble with alacarte?  I don't know what that is.

But the instructions want you to do this:

```
rm -rf .conig/menus/
rm -rf .local/share/applications/
```
I just looked in there, and I don't see anything you can't live without.  

I guess the problem is that something you installed didn't make it to the application menu, and is messing things up.  alacarte maybe?

Let us know what happens.

---

### Post by rburkartjo on 2009-02-25
lla, used the rm commands you gave me still didnt fix problem/cheesemaker

---

### Post by llamabr on 2009-02-25
After you do this, you'll have to log out, and log back in.  Might even be prudent to reboot.  Logging into gnome will create those directories.

Why do you keep saying cheesemaker?  Did I miss part of the problem?

---

### Post by rburkartjo on 2009-02-25
lla did not work. sory about the cheesemaker thing i use that on a linux form i moderate just habit. hey just an idea i think the problem is with vlc i tried to add some skins and have had the problem mentioned above since. i was going to try and fix by using the add/remove. so what would command would i use to completely remove vlc from the terminal. heck it is worth a shot unless you have another idea

---

### Post by rburkartjo on 2009-02-25
found a link for complete removal
[http://ubuntuforums.org/archive/index.php/t-651201.html](http://ubuntuforums.org/archive/index.php/t-651201.html)

removed did a reboot still problem
then reinstall vlc and still problem

note the following from the terminal maybe a clue

ray@ray-desktop:~$ sudo apt-get install vlc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libstrigiqtdbusclient0
Use 'apt-get autoremove' to remove them.
Suggested packages:
  mozilla-plugin-vlc videolan-doc
The following NEW packages will be installed:
  vlc
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1668kB of archives.
After this operation, 3703kB of additional disk space will be used.
Selecting previously deselected package vlc.
(Reading database ... 305838 files and directories currently installed.)
Unpacking vlc (from .../vlc_0.9.4-1ubuntu3.1_i386.deb) ...
Processing triggers for man-db ...
Processing triggers for menu ...
/usr/share/menu/cairo-dock: 1: Syntax error: word unexpected (expecting ")")
Execution of /usr/share/menu/cairo-dock generated no output or returned an error.
Setting up vlc (0.9.4-1ubuntu3.1) ...

Processing triggers for menu ...
/usr/share/menu/cairo-dock: 1: Syntax error: word unexpected (expecting ")")
Execution of /usr/share/menu/cairo-dock generated no output or returned an error.
ray@ray-desktop:~$

---

### Post by rburkartjo on 2009-02-25
okay now i removed vlc and used the rm commands again after i completely removed vlc did a restart and still same problem.

---

### Post by rburkartjo on 2009-02-26
upgraded to 9.04 that fixed

---

