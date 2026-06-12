---
title: "How to remove icons"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by aperture123 on 2009-07-15
So I have an acer aspire one and decided to try a linux distro for once, instead of ol' Windows. 
I must say, I am AMAZED at it, and am very happy to use it.
Recently I have tinkered with programs through wine and on the UNR quick-launch screen their little icons are up under the wine menu bar. However, I have uninstalled them, yet they remain. Unlike the favorites bar, I cannot right click and remove them. Not only that, but is there any way I could remove a bar entirely? For example, I have a system tools bar from a application I installed, and I would like to keep the app, but get rid of the bar because of the annoying scrolling. Finally, on the rightside has quicklaunch folders. Any chance I can add the trash bin to it?
Thanks oh ubuntu guru wizards......

---

### Post by CompizDoDo on 2009-07-16
have you tryed right click and remove ppanel

---

### Post by SteveNorman on 2009-07-16
any time you remove a program you have to manually remove all the extra crap such as config files, icons etc. its hard to say what will be left and what will not. for a program called foo you would do something like:
```
sudo apt-get remove --purge foo
sudo apt-get autoclean

```

then to be thorough search for all remaining stuff yourself by updating the data base, searching for everything related to your program, and removing what you find'

search:

```
sudo updatedb
locate foo
```

then remove all of it with the dreaded rm -rf command. You must be very careful with this command as it is the linux equivalent of a shotgun. dont get fancy with it and try to delete everything you find in one command. Just do them one at a time like this

for the program foo say you find /usr/bin/foo.icon and /home/.foo and others do 
```
sudo rm -rf /usr/bin/foo
sudo rm -rf /home/.foo
```

If you screw up a space or file name you have problems, for instance a space in /home/ .foo instead of the correct /home/.foo will remove your home directory, which  is bad. always double check before you hit enter on these rm commands.

repeat the update, locate and remove procedure till its all gone, then restart your desktop.


Dont do this if your not comfortable with the rm command. Replace 'foo' in the instructions with whatever the program your removing is called.

---

### Post by aperture123 on 2009-07-16
I will try the above poster,
Sorry second poster, that didn't work.
THANKS FOR HELP!:D

EDIT: I found a very EASY way to do this.
go to preferences and click main menu. From there its incredibly easy to get rid of old icons...however, I am still unsure of how to add trash can to the right side of the screen next to Documents or Pictures......:confused:

---

