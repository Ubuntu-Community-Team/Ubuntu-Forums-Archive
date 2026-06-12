---
title: "Nautilus, want to open terminal in the directory"
date: 2009-07-02
forum: New to Ubuntu
---

### Post by legalguy on 2009-07-02
I have a directory open in Nautilus, and I would like to open up a terminal and already hve it set to the path shown in that directory.  Maybe a bookmark that passes the working directory as a command line parameter somehow.

It can be any term app, just something that opens up to a prompt and is already in the right directory...

---

### Post by Mornedhel on 2009-07-02
You need to install the nautilus-open-terminal package, which does exactly what you want.

---

### Post by legalguy on 2009-07-02
That sounds exactly like what I want...I just installed it with Synaptic, but I can't find it.  Not in the Nautilus tab headers  or right click, not in Applications anywhere either.  How do you invoke it?

---

### Post by legalguy on 2009-07-02
Never mind, it is supposed to show up as a right click.  It didn't (even after closing all the open windows) but I rebooted and it was there after that.  Thanks again, it's just what I wanted.

---

### Post by Mornedhel on 2009-07-02
You need to close all running instances of Nautilus before the add-on can be used. Unfortunately, Nautilus also manages your desktop icons, which means that if you just close all file browser windows there still is a last instance running.

The easiest way is probably to log off and on again, but there's another method. Close all Nautilus windows. Start the system monitor (System > Administration > System Monitor), hunt the last Nautilus process and kill it. Then launch a new file browser instance, which will have the side-effect of also restarting the desktop instance (or maybe it just restarts on itself -- not sure, but the end result is identical).

The new instance should be able to use the plugin.

Edit: Sorry, I took too long writing this...

---

### Post by legalguy on 2009-07-02
not a problem..it's a home machine so rebooting is no big deal..

---

### Post by fooman on 2009-07-02
thats one of the first things i add to nautilus after installing ubuntu,  along with "nautilus-gksu", which will let you to right click on a file and have the option to "open as administrator",  allowing you to open and edit the file as root with gedit.

a couple of more are "nautilus-wallpaper",  which allows you to right-click an image and choose "set as wallpaper" from the context menu...and "nautilus-image-converter",  it allows you to right-click on an image and resize or rotate it from the menu.

i find those all to be very useful.

---

