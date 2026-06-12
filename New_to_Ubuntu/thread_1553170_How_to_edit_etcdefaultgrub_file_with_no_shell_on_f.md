---
title: "How to edit /etc/default/grub file with no shell on fresh install?"
date: 2010-08-14
forum: New to Ubuntu
---

### Post by rivendell678 on 2010-08-14
Just installed Linux for the first time. Am longtime unix user from a number of years back but recently have been stuck with just Windows. Any help most appreciated.

I've run into the same 'terminal' problem described in this thread: [http://ubuntuforums.org/showthread.php?t=1501143](http://ubuntuforums.org/showthread.php?t=1501143)

error: no suitable mode found
error: unknown command 'terminal'

The fix is apparently to edit the default grub terminal setting. However, this single boot machine brings up the ubuntu login screen but once I log in, I do not see any way to create a shell (/bin/sh, csh, etc) to edit and make these changes to fix the screen resolution problem.

Can anyone give me any advice?

More info:
Here's what I see when I log in, get blank screen (no icons, or anything) except for a pink-ish white swirling colored background. 
Installed [ubuntu-10.04-desktop-i386.iso]("file:///C:/Documents%20and%20Settings/rbecker/My%20Documents/Downloads/ubuntu-10.04-desktop-i386.iso") as single boot on re-formated disk
Left mouse button does nothing. 
Right mouse button gives me the following menu:
   Create Folder
   Create Launcher
   Create Document
   Clean Up ByName
   Keep Aligned
   Paste
   Change Desktop Background

I ran "Create Launcher", browsed the file system and created an icon for /bin/sh but it does not seem to run when I click on it, or right click on it and select "open". I also tried to do a search in Create_Launcher for 'terminal' or other command which might create a window and spawn a shell but the search seems to be a no-op.

I also tried to run telnet off my windows box but the connection to this host times out so I'm guessing that telnetd is probably not running. If I run 'ping' on the IP address from a Windows cmd, the machine does respond.

Any pointers most appreciated. (Sorry if something on this topic is already posted. I tried searching here on the forums but couldn't locate anything related)

---

### Post by blazemore on 2010-08-14
Try hitting alt+f2 and then typing
> gnome-terminal
then hit Enter

If gnome-terminal doesn't work, try "xterm"

And if that doesn't work you can use the key combination "Ctrl + Alt + F1" to get to a full-screen terminal. (Press Ctrl + Alt + F7 to get back to the graphical desktop)

---

### Post by NewDisciple on 2010-08-14
I use nautilus scripts more often for editing files as I am inclined to forget terminal commands and don't care to spend much time looking.  Available at [http://gnome-look.org/]("http://gnome-look.org/")
If it doesn't already exist, create a file "nautilus scripts" in
./gnome2 in your home folder.  Then go to the file you want to edit, right click, go to scripts, choose rootilus or scripts which give you root. Edit your document, save, and most likey reboot.

---

### Post by nocare on 2010-08-14
```

alt-ctrl-shift-f1
$sudo nano /etc/default/grub

```

Alternatively, while booting you can edit the boot parameters temporarily. Through that, if you tag "single" at the end it'll bring you up in init 1, which should allow you to edit it.

---

### Post by NCLI on 2010-08-14
I second what nocare said, just remember to run "sudo update-grub" in the terminal afterwards.

---

### Post by rivendell678 on 2010-08-17
Thank you to everyone who responded on this. It's most appreciated.
alt-ctrl-shift-f1 is just the trick that I was needing, tho I'm sure the other approaches will work great, as well.
Thanks again!

---

