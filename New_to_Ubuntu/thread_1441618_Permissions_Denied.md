---
title: "Permissions Denied"
date: 2010-03-29
forum: New to Ubuntu
---

### Post by Mr. R on 2010-03-29
OK, I need some help.

I just want to drag and drop an image file into usr/share/icons/, and It gives: "Permission denied." My image is set to the correct R/W permissions so it might be the folder. I heard that chmod might help with this problem.

Actually, my big problem is that I want a way to not receive this annoying message anymore, so I'd like to change all permissions for ***every** *directory and ***every*** file so that only my account can access every part of my machine (but if /sys/ cannot be accessed easily, that's fine.) And maybe I want to turn hidden files on permanently for all folders. How can I do these?

Sorry, I am very much a Windows person and have only been using Ubuntu for less than 24 hours.
I'm also in need of instructions to change the default oem account to something else.

---

### Post by Soulcage on 2010-03-29
Open a terminal and type something like: ```
sudo mv blah.png /usr/share/icons
``` make sure you're in the right location first, use "cd" if you need to change.

---

### Post by Mr. R on 2010-03-29
Hm, you know every time I type in "sudo . . ." it pops up with

```
sudo: unable to resolve host <username>
```Then it asks for password. I think I recently changed something relating to the username. . . I just meant to give "oem" an alias name.

It will work in the meantime, but I'd also very much like to painlessly use the file exploring UI :]

---

### Post by asmoore82 on 2010-03-29
> **Mr. R said:**
> Actually, my big problem is that I want a way to not receive this annoying message anymore,**[COLOR="Purple"] so I'd like to change all permissions for *[B]every** *directory and ***every*** file so that only my account can access every part of my machine[/COLOR][/B] (but if /sys/ cannot be accessed easily, that's fine.) And maybe [COLOR="Blue"]**I want to turn hidden files on permanently for all folders.**[/COLOR] How can I do these?

[COLOR="Purple"]Sorry, I am very much a Windows person and have only been using Ubuntu for less than 24 hours.[/COLOR]

[COLOR="Blue"]Places -> Home;
Edit -> Preferences;
check "Show hidden and backup files."[/COLOR]

As for everything else...[_[COLOR="Purple"]**Linux is NOT Windows.**[/COLOR]_]("http://linux.oneandoneis2.org/LNW.htm")

There can only be 1 root account and it ain't you.
This is how and why Unix/Linux works better.

You can get a single instance "File Browser" window with root privilege by running:
```
gksudo nautilus
```

---

### Post by 3rdalbum on 2010-03-29
On Linux, Mac OS, Unix and Windows, only the administrator can modify files outside the home directory. This is done to prevent users from interfering with eachother, and it also has the side-effect of stopping malware from attacking the system.

On Ubuntu there is no administrator account as such; but the first user created can use the 'sudo' command, which temporarily gives the user 'root' (administrator) privileges for the duration of a command.

You can use it on the command line:

```
sudo cp blah.png /usr/share/icons/
```

Or to launch a graphical program as root:

```
gksudo nautilus
```

Launching Nautilus (the file browser) as root is one of the easiest ways of doing what you want to do as regards copying the file into that directory. I'd recommend installing the 'nautilus-gksu' package from Synaptic, which will give you an item in your right-click menu that lets you open folders and files as the administrator.

I'm not going to tell you how to make your user account all-powerful. The Linux system is designed to run best when its security system is intact, and you WILL have problems if you attempt to pervert it. Work within the security system for your own safety, and only use 'sudo' and 'gksudo' when you absolutely need to. There is a reason why all modern operating systems have a similar security system, and that is that it's effective when used properly.

---

### Post by Mr. R on 2010-03-29
Thank you all. I've recently rebooted and reinstalled Ubuntu to change and reconfigure my default user account that the company I purchased the computer from had created (and kept a backup of files). I read the LNW article, and thank you for that.

OK, I confess. The bigger reason I reinstalled because I ran "chmod -R /." and it screwed up everything.

Thanks 3rdalbum for explaining more in detail. I was wondering what kind of malware you'd be referring to. Nothing serious I hope. Oh well, it has nothing to do with the question.

I'll install 'nautilus-gksu.' Or would it be easier to use a BASH shell and a launcher?

---

