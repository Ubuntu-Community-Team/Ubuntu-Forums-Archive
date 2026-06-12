---
title: "My Karmic laptop wont boot into graphical desktop, stops at tty1 login"
date: 2009-11-04
forum: New to Ubuntu
---

### Post by rod40cool on 2009-11-04
I need help.
Just yesterday I ran apt-get upgrade now it just boots to a flashing TTY1 terminal.
When I say flashing, I mean literally the screen is flashing blank then the tty text logon screen about 4 times a second and I can't login.  

The new karmic splash screen displays fine, it's after this when the screen goes blank preparing to show the login screen that it fails. It looks like something has screwed up my nvidia display driver as the GDM wont start, but if I try holding down shift during grub load I can successfully get into the text recovery mode ok.

I've tried running "dpkg   Repair Broken Packages" but that hasn't fixed it.

Can anyone shed any light on how I can troubleshoot and recover this?


EDIT: Just found this which fixed my problem. I removed all my nvidia drivers but xorg.conf still had "nvidia". Changed to "nv" and I have a desktop again.
[http://ubuntuforums.org/showpost.php?p=8243899&postcount=24](http://ubuntuforums.org/showpost.php?p=8243899&postcount=24)

---

### Post by ninjapirate89 on 2009-11-04
I had the same problem. Glad you got it fixed.

---

