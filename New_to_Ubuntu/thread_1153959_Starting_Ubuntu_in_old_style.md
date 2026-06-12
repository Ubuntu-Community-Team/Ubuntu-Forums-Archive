---
title: "Starting Ubuntu in old style"
date: 2009-05-09
forum: New to Ubuntu
---

### Post by navaneethkn on 2009-05-09
Hi all,

Previously my LINUX used to start with showing many commands and a status condition.  Something like

command          [OK]
command          [OK]

But in UBUNTU, this is not happening as UBUNTU shows it's logo when booting. I wonder how do I configure UBUNTU, so that it shows like the classical linux starts. Is there anyway to that?

I am using UBUNTU 9.04

---

### Post by NightwishFan on 2009-05-09
Make a backup of the /boot/grub/menu.lst file.

Then open the original and find the ubuntu boot entry and remove the "splash" at the end. If you want a LOT of text, remove the "quiet" entry.

---

### Post by Triptol on 2009-05-09
Seems you want to disable the graphical login. You can press ctrl+alt+F1 when the graphical login display, to fall back into "command [OK]"-mode.

If you really want to disable the graphical login, you should enter the following on the command line:

```
sudo update-rc.d -f gdm remove
```

or 

```
sudo update-rc.d -f kdm remove
```

The first one will remove the Gnome graphical login (Ubuntu) the second one removes the KDE graphical login (Kubuntu). It will not remove the programs themselves, but just the links in /etc/rcx.d so they won't start automatically.

If you need them again you can start them manually by entering:

```
sudo /etc/init.d/gdm start 
```

or

```
sudo /etc/init.d/kdm start
```

And if you want to revert to automatically starting the graphical login you can enter:

```
sudo update-rc.d gdm defaults
```

Or kdm for the KDE variant, but that should be clear now ;-)

---

### Post by gmjs on 2009-05-09
I think this varies based on the distribution of Linux you are using.  Red Hat (and therefore CentOS and Fedora) tend to write [  OK  ] or [Failed] in green or red when loading.  Ubuntu and Debian (as far as I know) don't do that and print * .... done instead.

Perhaps you were using a RedHat-based distro before?  It's just a minor difference between distros.

Hope this helps,

Graham

Edit: Sorry, being dense.  It does show [OK] doesn't it!

---

### Post by Triptol on 2009-05-09
NightwishFan's answer is the better one for you.

---

### Post by navaneethkn on 2009-05-09
Thanks Guys, I followed "NightFishFan's" answer and it worked like a charm. Thanks again. BTW, I wonder from where you guys learn all these commands? Is there any manual available where all commands are listed?

Thanks to Triptol and all other answerers.

---

### Post by NightwishFan on 2009-05-09
No problem.

As for commands and other such wizardry, that comes with experience more than anything. Be willing to tinker, etc..

I do not have any good references off the bat, but I am sure someone could help you out.

Some useful Linux commands: 

Search for other commands:
```
apropos type-search-term-here
```

Get help on a command:
```
man commandname
```
or
```
commandname --help
```


Here is a reference.
[http://gd.tuwien.ac.at/linuxcommand.org/](http://gd.tuwien.ac.at/linuxcommand.org/)

---

### Post by swoody on 2009-05-09
> **navaneethkn said:**
> Thanks Guys, I followed "NightFishFan's" answer and it worked like a charm. Thanks again. BTW, I wonder from where you guys learn all these commands? Is there any manual available where all commands are listed?

Thanks to Triptol and all other answerers.

Hi navaneethkn, and Welcome to Ubuntu, and the Forums ):P

If you're looking for some good resources to help you along with Ubuntu, try the links in my signature. The first one is a thread on the forums with TONS of info to almost anything you could need. The second link is to a Free Ubuntu Guide with all kinds of info - some of which covers basic commands, too! It's a great guide, and has really come in handy for me! If you can afford the paper/toner you can print out the entire guide and have it on hand next to your computer for easy reference. Otherwise you can just save it on your computer, and look it over if you ever have an issue.

Again, welcome aboard, and if you have any other issues, don't be afraid to ask!! :D

---

