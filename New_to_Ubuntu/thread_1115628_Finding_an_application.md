---
title: "Finding an application"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by loseby on 2009-04-04
I have installed a couple of programs and cant find them. How does Ubuntu install them, is there a simple tree similar to windows where you can see you files /applications etc.

btw: one of the programs was ntop

---

### Post by jimreynold2nd on 2009-04-04
If it is a GUI app, then easiest way is to Alt-F2 then type in "ntop" (then press enter - duh). This is my prefered way - fast and precise.
If it's a console app, open the console and type in the name. Bash can help with name completion in this case.

But if it's a GUI app, it's probably in your gnome main menu already.
Softwares in *nix is not put in one directory (Program Files), then spray DLLs, settings, license info, registry keys... all over the place (and normally "forget" to remove all of them). In *nix, there are well-documented places where things of a software should go, and most (if not all) softwares followed them. Generally:

Tools executables in /bin/
Admin tools executables in /sbin/
Global config files in /etc/
Temp files in /tmp/
Logs in /var/
Bigger programs in /usr/ (this dir has similar structure to /)

Good luck hunting!

---

### Post by dtoronto on 2009-04-04
It really depends on which app you are trying to install.  Which apps are you trying to install?

---

### Post by Elfy on 2009-04-04
You can use locate or find to find programs -

```
locate [i]name[/i
find *name*
```

If a program is terminal based then it is likely that there will be no menu entry, also if the developer sisn;t make a menu item then, again, there will be none.

You can make a launcher if you want, you can also right click on the menu to get the Edit menu option.

Couple of links for folder hierarchy

[http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html](http://www.comptechdoc.org/os/linux/commands/linux_crfilest.html)
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

---

### Post by loseby on 2009-04-04
Basically I am trying to install a tool that would allow me to monitor my interent usage and have selected ntop and darkstat from Snaptic Package Manager, Now I know bugger all about these applications and cant find if they installed.

They are not in any of the menus

---

### Post by Elfy on 2009-04-04
Try in a terminal - ntop would be the command for ntop at a guess. I use vnstat to do similar - it runs from the terminal.

There will be a man page probably - man ntop

---

### Post by axelroo on 2009-04-04
Some other ways to locate the executable of a program is "whereis <name>". Provided the executable is the same as the title of the program, i.e. firefox, it should come up with its full path. 

Also, if you're just looking for a program to use or you know what you're looking and don't want to take the time to fire up synaptic, you can use 'apt-cache search <name>' and 'sudo apt-get install <name>' from the console.  

Lastly, the path of most executables you install will end up in /usr/bin. Try looking there first, then try /usr/local/bin.

For example, if I have installed a program called 'someuselessapp'.  I would first go into /usr/bin and do 'ls some*' (lists any file that begins with 'some') then id do the same under /usr/local/bin. 

If you're not familiar with the terminal, you can use your favorite file manager and search in those two folders.

Good luck

---

### Post by Elfy on 2009-04-04
I'm a muppet :lol:

thanks axelroo - 'twas the one I forgot :)

---

### Post by 3rdalbum on 2009-04-04
Ntop is not a GUI application, that's why there's no menu item for it.

You run it from the command-line and it uses a web-based interface to display its information.

Ntop is a system administrator tool, not a general purpose "how much have I downloaded". As such, it's not an easy program for a beginner to run and it can be difficult to interpret its information. If you want to know how much is being transmitted across your network, you can just open gnome-system-monitor. It keeps a tally of the uploads and downloads accrued in between reboots (that function might require you to add the System Monitor applet to your panel or keep gnome-system-monitor open... I'm not sure).

---

### Post by loseby on 2009-04-04
Ntop and Darkstat where 2 that I found but really know nothing about. On my other PC I found an application that was free  and had downloaded, installed and running in 30 mins.

btw: have been using Network Connection to get a rough idea but it really doesnt do what I want and that is get infomation for the entire month and break it down between peak and off peak

---

### Post by Christmas on 2009-04-04
Usually the binaries go to /usr/bin, but you can also try the following commands:
```
echo $PATH
```
Which will echo all the paths in which a binary will be looked after when you try to run it with ALT+F2 and typing in the name of your program. You can also try:
```
whereis program_name
```
Usually graphical programs installed with APT (the Ubuntu package manager) also have a menu entry, otherwise try to run them from a terminal by typing the first characters of the application and then TAB (which will fill in the rest of the name). Pressing TAB twice will show the available applications starting with those characters (if there are more than one applications starting with that name).

Most of the programs you install will have a suggestive name (e.g. Amarok can be ran as *amarok*, Midnight Commander as *mc* etc.

A useful command is to open the terminal and type:
```
dpkg -L package_name
```
Which will list all the files which have been installed by package_name. The binary is usually located in /usr/bin.

Regarding file structure and the way Ubuntu handles applications installed via APT or compiled from source, you can find a very good thread [here](http://forums.debian.net/viewtopic.php?t=9685). I'm sure there is something similar here on UbuntuForums but I won't bother searching now. Hope this helps a little bit clarify some of the issues.

---

### Post by loseby on 2009-04-04
have some reults and will now see what I can do with it

.
/var
/var/lib
/var/lib/darkstat
/etc
/etc/darkstat
/etc/darkstat/init.cfg
/etc/init.d
/etc/init.d/darkstat
/usr
/usr/sbin
/usr/sbin/darkstat
/usr/share
/usr/share/doc
/usr/share/doc/darkstat
/usr/share/doc/darkstat/README
/usr/share/doc/darkstat/THANKS
/usr/share/doc/darkstat/AUTHORS
/usr/share/doc/darkstat/README.Debian
/usr/share/doc/darkstat/copyright
/usr/share/doc/darkstat/NEWS.gz
/usr/share/doc/darkstat/changelog.Debian.gz
/usr/share/man
/usr/share/man/man8
/usr/share/man/man8/darkstat.8.gz

---

