---
title: "Installation Issues with Komodo Edit 6"
date: 2011-06-12
forum: New to Ubuntu
---

### Post by Mazorak on 2011-06-12
So I downloaded Komodo Edit 6 from [http://www.activestate.com/komodo-edit/downloads]("http://www.activestate.com/komodo-edit/downloads"). It came as a tar.gz file.

After that I extracted it, and then installed it with "sudo ./install.sh"

Anyways I now have the software installed, and a shortcut was placed on my desktop. However, there's really no other way to access it. For example, if I search for it, I don't get any results.

I'm pretty sure this is a simple problem, any help on this would be appreciated.

---

### Post by DirtyPC on 2011-06-12
Did you insert your executable into your path variable? You need to do that after running the shell script

sudo ln -s "/home/myuser/Software/Komodo-Edit-6/bin/komodo" /usr/local/bin/komodo

---

### Post by Mazorak on 2011-06-12
> **harrylucas1 said:**
> Did you insert your executable into your path variable? You need to do that after running the shell script

sudo ln -s "/home/myuser/Software/Komodo-Edit-6/bin/komodo" /usr/local/bin/komodo

So I ran the command. Now how do I "insert my executable into my path variable"?

---

### Post by DirtyPC on 2011-06-12
It was taken from a google link. What i mentioned was step 6, you seemed to finish on step 5. You should know more than me.

---

### Post by gareththomasnz on 2011-11-23
May I please ask for the link ?

---

### Post by beew on 2011-11-23
Open you home folder, click View > Show hideen files and open  .local/share/applications, copy your desktop launcher file to it and then reboot. Then it should show up in the dash, if not you may need to do some editing of the .desktop file.

Edited: Just installed it myself. Don't need reboot, just copy the desktop launcher file to   .local/share/applications, that's it.  You can then drag the icon from   .local/share/applications to the Unity bar if you want.

---

