---
title: "Dell Studio XPS 16 with Xubuntu won't power off on shutdown"
date: 2009-05-30
forum: New to Ubuntu
---

### Post by demiliterizedzone on 2009-05-30
Hi all,

Anyone know how to resolve this issue?  Whenever I shutdown or restart this computer it always appears to get stuck at the very last moment, past the shutdown progress bar, all that's left is a blank screen with a blinking cursor.  I have to CTRL+ALT+DELETE at this point but this only restarts the computer, not shutdown it down completely.  To shutdown my dual boot computer I either have to log into windows and shutdown from there or hold the powerbutton (or pull the plug).

Kind regards,
-DMZ

p.s. I've tried shutting down from terminal and from the exit icon.

---

### Post by anewguy on 2009-05-30
You may need to acpi=force in the menu.lst file used by grub.  If you are not familiar with how to do that, post back and I'll give you instructions.

Dave :)

---

### Post by anewguy on 2009-05-31
If you still need help, here's another post where I explained how to do this:

[http://ubuntuforums.org/showthread.php?p=7374808#post7374808]("http://ubuntuforums.org/showthread.php?p=7374808#post7374808")

Dave :)

---

