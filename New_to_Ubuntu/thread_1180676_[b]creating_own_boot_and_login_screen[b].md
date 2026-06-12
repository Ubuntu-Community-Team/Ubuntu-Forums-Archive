---
title: "[b]creating own boot and login screen[/b]"
date: 2009-06-07
forum: New to Ubuntu
---

### Post by balachandarlinks on 2009-06-07
Hi,
  I want to create my own boot screen and login screen for my ubuntu 8.10.I hope that editing
the previously created one 'll be easy instead of creating the one from scratch.I googled a lot.
But I found nothing useful to me.I am really waiting or any help to make me create my own
login and boot screens.
               Thanks in advance...
                    cheers....

---

### Post by theozzlives on 2009-06-07
Their are a ton of login screens at [http://www.gnome-look.org]("http://www.gnome-look.org")

---

### Post by balachandarlinks on 2009-06-07
I want to create my own screen.....with my touch...;-)

---

### Post by desperado665 on 2009-06-07
Have you tried startupmanager?

can be installed with "sudo apt-get install startupmanager"

or search startup in synaptic package manager.

---

### Post by MadnessRed on 2009-06-07
> **balachandarlinks said:**
> I want to create my own screen.....with my touch...;-)

try downlaoding one then extracting the files, make you changes then compress it again.

---

### Post by NilsE on 2009-06-07
The themes are in /usr/share/gdm/themes. Each folder within is a login theme. You will need to have root privileges so open "gksudo nautilus" and browse to it 

You can copy an entire folder (theme) and contents within the /usr/share/gdm/themes folder and rename it to what you want to call your theme.  You can then start editing and changing what's in the folder. The size and field position within the images is referred to within the xml file so you can use the same size graphic or start tinkering with the images sizes in the xml file.

You then assign it with the Startup Manager.

---

