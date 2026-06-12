---
title: "update problem"
date: 2009-11-07
forum: New to Ubuntu
---

### Post by sauravbhaumik on 2009-11-07
I'm using ubuntu 9.10 and when i check for update, it gives me an error message: ```
Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.10 _Karmic Koala_ - Release i386 (20091028.5)/dists/karmic/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.
```

What to do?
Thanks in advance.
Saurav

---

### Post by arochester on 2009-11-07
It looks as though the computer is looking for the CD as a repository. You need to edit your sources list to make this inneffective.

Open a Terminal and input the command: gksudo gedit /etc/apt/sources.list

Look for references to the CD being a repository - probably at the top. Put a # at the begionning of the lines you want to be inneffective. Save and exit Gedit. Try again.

---

### Post by Ant59 on 2009-11-07
Or go to System > Administration > Software Sources, and untick the CD in the white box at the bottom of the window.

---

### Post by sauravbhaumik on 2009-11-07
Thank you very much.

---

### Post by pguedes on 2009-11-14
it just works!!!

---

### Post by spindoc on 2010-01-28
thank you, this fix works

---

