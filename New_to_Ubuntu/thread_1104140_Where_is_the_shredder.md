---
title: "Where is the shredder?"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by yeehi on 2009-03-23
Where is the shredder/recycle bin?

Do we have to install one?

---

### Post by drs305 on 2009-03-23
The recycle bin for each user in Hardy and later is ~/.local/share/Trash. There are two subfolders, *info* and *files*. Root's trash is in /root/.local/share/Trash.

The Trash bin should be installed by default. You can add it to a panel if it's not there via right click, Add to Panel, Trash.

---

### Post by ubuntu27 on 2009-03-23
> **yeehi said:**
> Where is the shredder/recycle bin?

Do we have to install one?

The Trash is always "installed" by default. You can access it by typing **trash:///** to the Location Bar.

If you don't see the location bar in Nautilus (Gnome's file browser), then press Control (Ctrl) + L



Also, you can add Icons for Trash, Computer, My network, etc to your desktop by following [this guide]("http://www.howtoforge.com/display_my_computer_and_trash_icons_on_gnome_desktop"):

[URL="http://www.howtoforge.com/display_my_computer_and_trash_icons_on_gnome_desktop"]
Displaying "MyComputer", "Trash", "Network Servers" Icons On A GNOME Desktop[/URL]

---

### Post by SunnyRabbiera on 2009-03-23
The trash bin is in the lower right corner of the screen.

---

### Post by stchman on 2009-03-23
> **yeehi said:**
> Where is the shredder/recycle bin?

Do we have to install one?

The ~/.Trash does not shred.

TO shred files(make unrecoverable) use the shred command.  Shred does not work on folder

To shred files and folders use the wipe command.  You will need to install it first.

```
sudo apt-get install wipe
```

Refer to the shred and wipe documentation for syntax.

---

### Post by icanfly0307 on 2009-03-23
You're probably looking for the Trash on the Desktop. Ubuntu doesn't have any Desktop Icons by default. However, just open a terminal, type "gconf-editor" and press enter. This should open up a window. On the tree structure on the left, navigate to apps-->nautilus-->desktop. You should see a list of options with check boxes on the right. Check the "Computer" "Home Folder" and "Trash" boxes and you should be good to go. Hope this helps! :D

---

### Post by HermanAB on 2009-03-23
Please people, the program 'shred' doesn't really work.  Well, it does, if you use the Microsoft FAT file system, but nobody does these days (except Tom Tom it seems).  So please stop promoting the installation of 'shred'.

If you are worried about security, then boot with the alternate install CD and use LUKS.

Cheers,

Herman

---

### Post by ubuntu27 on 2009-03-23
> **HermanAB said:**
> Please people, the program 'shred' doesn't really work.  Well, it does, if you use the Microsoft FAT file system, but _nobody does these days _(**except Tom Tom it seems**).  So please stop promoting the installation of 'shred'.

...............
Herman

That made me laugh :D

---

### Post by billgoldberg on 2009-03-23
```
rm -rf ~/.local/share/Trash
```

---

### Post by Xero Xenith on 2009-03-23
> **billgoldberg said:**
> ```
rm -rf ~/.local/share/Trash
```

That deletes all files in the trash.

I think the answer you're looking for is that the trash can is on the lower-right corner of the screen; clicking it will bring up the folder with a button to empty it. This will delete the files.

If you want to completely remove files (only necessary in secure environments, when simply removing the file is not enough) use *wipe* as described above.

---

### Post by boof1988 on 2009-03-23
> **HermanAB said:**
> Please people, the program 'shred' doesn't really work.  Well, it does, if you use the Microsoft FAT file system, but nobody does these days (except Tom Tom it seems).

This is simply an incorrect statement.

According to the man-pages for shred:

> In the case of ext3 file systems, [COLOR="Red"]the above disclaimer applies[/COLOR] (and shred is thus of limited effectiveness) [COLOR="Red"]only in data=journal mode,[/COLOR] which  journals  file  data in addition to just metadata.  [COLOR="Red"]In both the data=ordered (default)[/COLOR] and data=writeback modes, [COLOR="Red"]shred works as usual[/COLOR].  Ext3 journaling modes can be changed by adding the data=something option to the mount options for a particular file system in the /etc/fstab file, as documented in the mount man page (man mount).

Please note the text highlighted in red...

It seems "shred is thus of limited effectiveness... only in data=journal mode" and in "data=ordered (default)" mode "...shred works as usual".

So please stop misinforming people.

---

### Post by Andrew.Z on 2009-06-09
> **HermanAB said:**
> Please people, the program 'shred' doesn't really work.  Well, it does, if you use the Microsoft FAT file system, but nobody does these days (except Tom Tom it seems).  So please stop promoting the installation of 'shred'.

Shred works on many Linux file systems including the default for Ubuntu.  The shred man page states the situations where it works, and [I validated shredding](http://bleachbit.blogspot.com/2009/06/validating-secure-erase.html) in the default ext3 file system when I re-implemented it in my program.

---

