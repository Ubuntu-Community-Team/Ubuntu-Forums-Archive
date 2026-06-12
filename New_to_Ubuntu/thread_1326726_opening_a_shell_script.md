---
title: "opening a shell script"
date: 2009-11-14
forum: New to Ubuntu
---

### Post by rossjman1 on 2009-11-14
I have a shell script that is executable. When I open it in gnome and choose open in terminal, the script runs fine. I recently switched to KDE4, and I can't figure how to execute the file without going to the terminal and executing it via command. How can I get KDE to run a shell script?
In the open with dialogue, is there a command I should use (like sh %U) where %U is the symbol for the filename (don't know if it is)?
I'm using Kubuntu 8.10.

To illustrate my point:
[IMG]http://img200.imageshack.us/img200/1299/snapshot1eg.png[/IMG]
[IMG]http://img20.imageshack.us/img20/2617/snapshot2qk.png[/IMG]

---

### Post by SkyNet2029 on 2009-11-14
input
 
konsole
 
where it asks for what to run it with

---

### Post by rossjman1 on 2009-11-14
> **SkyNet2029 said:**
> input
 
konsole
 
where it asks for what to run it with

First thing I tried, doesn't work (I also checked run in console). It just opens up a blank konsole window, not executing the file at all.

---

### Post by rossjman1 on 2009-11-14
bump. I also tried using sh. Is there a symbol that represents the file path and name, so I can perform something like this: sh %U (where %U is the filename). Why is the default action to open with a text editor?!?!?!?!?

---

### Post by rossjman1 on 2009-11-15
bump, someone that uses kde regularly should know this...

---

### Post by rossjman1 on 2009-11-15
bump

---

### Post by rossjman1 on 2009-11-15
really no one knows?

---

### Post by falconindy on 2009-11-15
/usr/bin/bash ?

Dunno, not a KDE guy. In Gnome, there's no need to associate shell scripts with a program -- it Just Works (tm).

---

### Post by Old *ix Geek on 2009-11-15
I had no idea how to do this, as I run scripts from a command line. But I thought I'd give it a whirl...and ended up frustrated!

I did find a method that works, though.  Install Nautilus.  It doesn't matter that it's for GNOME.  I already had it installed (I use a lot of GNOME programs on KDE), but really never use it as Dolphin is so cool.  But with no tinkering at all Nautilus did exactly what you're after.  It gives you various choices including running the program.

Note that if your script doesn't provide for some delay or interaction when it's finished, it'll close without feedback/acknowledgment.

I'm looking at Nautilus-related stuff in Synaptic right now, and although I DON'T have this installed, there's something called "nautilus-actions" you might want to install. Its description says:
> Nautilus actions is an extension for Nautilus, the GNOME file manager.

It allows the configuration of programs to be launched on files selected in the Nautilus interface.

---

### Post by NSLW on 2011-06-07
1) Add bash+run in terminal for x-shellscript
2) Turn off executable on script

That should work.

---

