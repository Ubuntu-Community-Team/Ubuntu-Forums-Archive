---
title: "Backing Out a Wrong Command - Skype Upside Down Video"
date: 2011-06-14
forum: New to Ubuntu
---

### Post by MPacheco on 2011-06-14
Hello All,

I really blew it!

I'm new to Ubuntu and Linux and tried to second guess/edit the command line I'm supposed to use to make Skype video come out right side up (right now it's upside down).  The command line I found was:

LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

But using using a 64 bit system, I changed the command line to read:

LD_PRELOAD=/usr/lib/libv4l/v4l1compat.so  skype

When it didn't work, I tried entering the original command line, but the command continues to revert to the originally inputted command line and all I a screen full of error messages:

~$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2616): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2616): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2616): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2616): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2616): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2616): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2616): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2616): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2616): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2616): Gtk-WARNING **: Loading IM context type 'ibus' failed

How do I delete the command line I don't want in favor of one I do?  I don't want to do more damage than I already have by deleting a file I shouldn't.

Any guidance is greatly appreciated.

Thanks,

-MP

---

### Post by Perfect Storm on 2011-06-14
LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype

should be right, as skype needs 32bit libs on a 64-bit system. So changing it to look in /usr/lib would not work, it's the place for 64-bit libs.

---

### Post by MPacheco on 2011-06-14
Yes, it is the right command and I was able to make it work; however, my tooling around on this caused a secondary issue.  The incorrect command initially entered:

LD_PRELOAD=/usr/**lib**/libv4l/v4l1compat.so skype

still activates when I enter the right command:

LD_PRELOAD=/usr/**lib32**/libv4l/v4l1compat.so skype

and I get this:
 
~$ LD_PRELOAD=/usr/lib32/libv4l/v4l1compat.so skype
ERROR: ld.so: object '/usr/lib/libv4l/v4l1compat.so' from /etc/ld.so.preload cannot be preloaded: ignored.
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2545): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2545): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2545): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2545): Gtk-WARNING **: Loading IM context type 'ibus' failed

(<unknown>:2545): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2545): Gtk-WARNING **: Loading IM context type 'ibus' failed
/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2545): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so

/usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so: wrong ELF class: ELFCLASS64

(<unknown>:2545): Gtk-WARNING **: Failed to load type module: /usr/lib/gtk-2.0/2.10.0/menuproxies/libappmenu.so


(<unknown>:2545): Gtk-WARNING **: /usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so: wrong ELF class: ELFCLASS64

(<unknown>:2545): Gtk-WARNING **: Loading IM context type 'ibus' failed


I presume all this is because of the incorrect command.  Where in the system do I find the incorrect command to delete it?

---

### Post by trozamon on 2011-06-14
Just to make sure - libv4l is installed, right?

You could put a link to the file in the "/usr/lib/libv4l/whatever.so" and try to use that

---

### Post by MPacheco on 2011-06-14
> **trozamon said:**
> Just to make sure - libv4l is installed, right?

You could put a link to the file in the "/usr/lib/libv4l/whatever.so" and try to use that

Newbie here.  How do I do that?

Thank you, BTW, for the help.

---

### Post by trozamon on 2011-06-14
Open up a terminal and type:

```
gksudo nautilus
```

You're gonna have to be careful now; you have root power, and anything you do is final.
Navigate the file browser to /usr/lib32/libv4l/. Right click on v4l1compat.so, click "make link". Right click on the created link, then move the link to /usr/lib/libv4l/. Now, you'll have to rename the link from "Link to v4l1compat.so" to just "v4l1compat.so". That should fix the problem, I think.

---

### Post by MPacheco on 2011-06-15
I got as far a attempting to make the link, but couldn't determine how to do that; guess I'm still too much of a Newbie.  Think I'll wait until I have more experience with Linux before I irrevocably change something I'll not want to.

Thank you for your guidance.  I will return to this and let you know how it turn out.

---

