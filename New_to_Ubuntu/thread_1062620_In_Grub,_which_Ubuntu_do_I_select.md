---
title: "In Grub, which Ubuntu do I select?"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by deleyd on 2009-02-07
When I boot my computer (dual-boot with Ubuntu & Windows Vista) it starts with the Grub bootloader menu and gives me 10 options:
[LIST=1]
[*]8.04.2 kernel 2.6.24-23-generic
[*]8.04.2 kernel 2.6.24-23-generic (recovery mode)
[*]8.04.2 kernel 2.6.24-19-generic
[*]8.04.2 kernel 2.6.24-19-generic (recovery mode)
[*]8.04.2 kernel 2.6.24-16-generic
[*]8.04.2 kernel 2.6.24-16-generic (recovery mode)
[*]Ubuntu 8.04.2, memtest86+
[*]Other operating systems:
[*]Windows Vista/Longhorn (loader)
[*]Windows Vista/Longhorn (loader)
[/LIST]
Not sure why it offers me 3 Ubuntu and 2 Vista, when there really is only one of each.

For Ubuntu, should I pick the one with the highest number, the 2.6.24-23-generic at the top? Does it matter which one I pick? (I've never tried the other Ubuntu ones. Why does it offer me 3 kernel versions to choose from?)

That's my simple absolute beginner question. 

**Question #2:**
My other related question is a bit more advanced. I'm trying to edit the **/boot/grub/menu.lst** file so I can change the default number. Right now it's booting to the memory test by default (#7). My notes say to go to the terminal prompt and enter:

[INDENT]**gksudo gedit /boot/grub/menu.lst**[/INDENT]

I do that, it asks for my password, I enter it, nothing happens.

I can see in File Browser the file is indeed there. I can get the file into the editor by double-clicking on it, but then it won't let me save because I didn't do the [FONT="Courier New"]gksudo [/FONT]thing (and what's the difference between **gksudo** and **sudo**?)


(All was working, then yesterday I did an update for Ubuntu, and now instead of 4 Ubuntu choices there are now 6, and Grub is now selecting the memory test by default, instead of Vista.)

---

### Post by utnubuuser on 2009-02-07
Hi --  for the menu.lst, I believe the command is> sudo gedit /boot/grub/menu.lst

sudo is a temporary root priviledge.

Here's a "what is gksu, gksudo, sudo?", thread: [http://ubuntuforums.org/showthread.php?t=760947]("http://ubuntuforums.org/showthread.php?t=760947")

And you could just comment out the un-needed kernels in the menu.lst.
Whenever a kernel is ubdated it's added to the menu.lst.

---

### Post by konqueror7 on 2009-02-07
its normal for you to have many kernels, probably you just updated you ubuntu... you can select any of them, but probably you would select the latest version above...

also you can try using "StartUp Manager" which you can find in the add/remove application menu. it enables you to customize your bootloader and other things...

also, to edit the menu.lst, is as what he said...
```
sudo gedit /boot/grub/menu.lst 
```

hope it helps...

---

### Post by owenll on 2009-02-07
You can remove an unwanted kernel through synaptic. Search for **2.6.24-16-generic**. I always keep one "spare" in the bootloader. 

As for Vista, I am on dual boot, and the bottom option is the one I select to boot Vista, the other is some kind of recovery mode for Vista I think.

---

### Post by Paqman on 2009-02-07
> **utnubuuser said:**
> Hi --  for the menu.lst, I believe the command is

sudo is a temporary root priviledge.

You should use gksudo for gedit, since it's a graphical app. Sudo is only for command-line work.

Anyway, to answer your question deleyd, each time you get a kernel update it'll get added to Grub (actually, during the update, it'll ask you what you want to do with Grub)

Use the most recent kernel, which will probably be the Grub default anyway. If you want to clean up the list you can install startupmanager, which can restrict the number of kernels shown and change the default, etc.

Alternatively, if you're happy that the new kernel works fine for you, just uninstall the old kernels from Synaptic. Look for packages called linux-image. Make sure you don't uninstall your current kernel! ;) Doing this will clean up Grub for you. Many people advise to keep the previous kernel around in case of borkage in the updated one, but that's pretty rare. Up to you.

Regarding you multiple Vista entries, I have no idea how that happened. You can manually edit the Grub list by opening a terminal and entering:
```

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup

```
(this creates a backup copy) Then:
```

gksu gedit /boot/grub/menu.lst

```
Which opens the Grub list for editing.
Scroll waaay down to the bottom and you'll see your Vista entries. Just delete whatever ones you don't want (or aren't working) If you mess it up, just restore to the backup you just made.

---

### Post by utnubuuser on 2009-02-07
Hi -- to edit the menu.lst file: sudo gedit /boot/grub/menu.lst

I believe sudo is for temporary root priviledge in terminal. gksu and gksudo are for root priviledge in the graphical environment.  

Here's a (what's sudo, gksu, and gksudo?") thread.

---

### Post by mister_pink on 2009-02-07
In all honesty, while this is good advice the easiest thing to do is install start up manager from add remove programs. It appears in your System, admin menu and you can set it to only show a maximum of 2 kernels (so you can get to an old one if an update breaks something, and change the default.

As for the two vista entries, I suspect one is Vista and one is some kind of recovery mode partition that came with your computer. If you work out which is which you can then rename them appropriately.

---

### Post by carml on 2009-02-07
The bootable entry of Vista is the last one,the other is for recovery. :)

---

### Post by drs305 on 2009-02-07
If you haven't received enough information already ( ;-) ), here's a link describing how to use StartUp-Manager, how to edit menu.lst, and what to do with older kernels:
[_http://ubuntuforums.org/showthread.php?t=818177_]("http://ubuntuforums.org/showthread.php?t=818177")

---

### Post by oldos2er on 2009-02-07
If you install the package nautilus-gksu, you can simply right-click on a file and choose 'Open as Administrator.'

---

