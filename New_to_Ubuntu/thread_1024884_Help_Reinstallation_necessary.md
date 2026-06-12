---
title: "Help? Reinstallation necessary?"
date: 2008-12-29
forum: New to Ubuntu
---

### Post by The Firkraag on 2008-12-29
I installed 8.10 some time back, and since then have been having trouble seeing Flash in Firefox (or anywhere). Several times I have removed and reinstalled the flash player (both the freeware version and adobe's) only to have flash break down again. It tells me I have a later version already installed and won't let me install manually. Lately some websites have begun to appear only as white screens with black text.

Do I need to reinstall 8.10 or go back to 8.04? If so, I have another question. I have no idea how to use the partition software. I don't understand the choices. If a fellow wanted to reformat the whole drive and then partition it for files and operating system separately, how would he do that? What formating options should I select in manual?

Thanks in advance.

---

### Post by jboy012000 on 2008-12-29
Before you attempt to reinstall try going to Synaptic Package Manager, type in the search box "Flash" then go down until you see the "Adobe flashplayer plug in", click on the little box on the left hand side and it will bring up a menu, goto click for reinstalation and see if that fixes the problem.

Let me know.

Thanks

John

---

### Post by mjheagle8 on 2008-12-29
i'm not great with the flash stuff, i had problems with it myself. but i am pretty good with partitioning. are you using only ubuntu or dual booting?
if you wanted to make separate partions for the os and your home, you'd go under manual in the install. you'd right click, edit, create new partition, of type ext3.  you'll want to have 3 partitions: about 4-8 gb for the os, 2x your ram formatted swap, and the rest for your /home.  all your files would be stored in /home.  here's a little table to go over the respective formats.  
partition - mount point - format - approx size
1 (swap) - swap - swap - 2x ram
2 (os) - / - ext3 - 4-8 gb
3 (files) - /home - ext3 - the rest of your hd

---

### Post by namdung on 2008-12-29
Go to *System-->Administration-->Synaptic Package Manager*, search for the Flash file u've installed and remove it.

Download *Flash Player 10* from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/). Ensure to select *.deb for Ubuntu 8.04+*

U don't need to reinstall Ubuntu, but if u really want to wait till 1/1/2009 for Hardy 8.04.2.

GParted is a very powerful tool, so be very careful/sure before applying 
changes.
[http://www.fsckin.com/2007/10/21/partitioning-or-resizing-drives-in-ubuntu-using-gparted/](http://www.fsckin.com/2007/10/21/partitioning-or-resizing-drives-in-ubuntu-using-gparted/)

---

### Post by The Firkraag on 2008-12-29
John,

I tried to reinstall adobe flash again, and it seemed to work, but as usual, I still couldn't see flash, but was prompted to get the flash reader. When I click there, I am told the only way to get the file is by manual download. Following the link to adobe, I download the file manually, but when it tries to unpack it, I am told I already have a more up to date version installed.

In the past I have completely removed all flash software and then tried the same process. I can then install the adobe file, but instantly the updater wants to update that file and the cycle begins again.


mjheagle8

Thank you very much. That will be very helpful if I need to reformat and reinstall. I am not completely computer illiterate, but I find the code for ubuntu a little arcane, as I'm a newbie to using it. Besides the minor headaches since I installed 8.10, I've enjoyed the OS.

---

### Post by The Firkraag on 2008-12-29
> **namdung said:**
> Go to *System-->Administration-->Synaptic Package Manager*, search for the Flash file u've installed and remove it.

Download *Flash Player 10* from [http://get.adobe.com/flashplayer/](http://get.adobe.com/flashplayer/). Ensure to select *.deb for Ubuntu 8.04+*

That is what I have been doing, but to no avail. :p

> U don't need to reinstall Ubuntu, but if u really want to wait till 1/1/2009 for Hardy 8.04.2.

GParted is a very powerful tool, so be very careful/sure before applying 
changes.
[http://www.fsckin.com/2007/10/21/partitioning-or-resizing-drives-in-ubuntu-using-gparted/](http://www.fsckin.com/2007/10/21/partitioning-or-resizing-drives-in-ubuntu-using-gparted/)

Thank you, I will look that over.

---

### Post by kansasnoob on 2008-12-29
I've had excellent luck with Ubuntuzilla:

[http://ubuntuzilla.wiki.sourceforge.net/](http://ubuntuzilla.wiki.sourceforge.net/)

They also have a forum on this site:

[http://ubuntuforums.org/forumdisplay.php?f=251](http://ubuntuforums.org/forumdisplay.php?f=251)

But also be certain you DO NOT have "gnash" installed.

```
sudo apt-get --purge remove gnash
```

Then install restricted-extras:

```
sudo apt-get install ubuntu-restricted-extras
```

And install flashblock (if using the Ubuntuzilla version of Firefox you can install just by searching add-ons in Firefox) or:

```
sudo apt-get install flashblock
```

---

### Post by The Firkraag on 2008-12-31
Okay. I tried to install ubuntuzilla and it failed on me. This is what came up:

> debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Selecting previously deselected package libnotify-bin.
(reading database ... 133059 files and directories currently installed.)
Unpacking libnotify-bin (from .../libnotify-bin0.4.4-3build1_i386.deb) ...
Selecting previously deselected package libstdc++5.
Unpacking libstdc++5 (from .../libstdc++5_1%3a3.3.6-17ubuntu1_i386.deb) ...
Processing triggers for man-db ...
Setting up libnotify-bin (0.4.4-3build1) ...
Setting up libstdc++5 (1:3.3.6-17ubuntu1) ...

Processing triggers for libc6 ...
Idconfig deferred processing now taking place
Selecting previously deselected package ubuntuzilla.
(Reading database ... 133074 files and directories currently installed.)
Unpacking ubuntuzilla (from .../ubuntuzilla-4.5.8-0ubuntu1-i386.deb) ...
Setting up ubuntuzilla (4.5.8-0ubuntu1) ...
Processing triggers for man-db ...
dpkg: error processing /tmp/ubuntuzilla-4.5.8-0ubuntu1-i386.deb (--install): cannot access archive: No such file or directory 

I wish I understood that even a little :p

---

