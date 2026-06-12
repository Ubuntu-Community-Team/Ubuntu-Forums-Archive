---
title: "failure to fetch"
date: 2009-09-04
forum: New to Ubuntu
---

### Post by 2roombas on 2009-09-04
Why do I keep seeing this in a warning dialog after I run Synaptic Paxkage Manager?

[INDENT]Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 9.04 _Jaunty Jackalope_ - Release i386 (20090420.1)/dists/jaunty/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.[/INDENT]

---

### Post by Paqman on 2009-09-04
It's looking for a CD in the drive containing packages. To make it stop go to System > Admin > Software Sources and uncheck the CD as a source.

---

### Post by 2roombas on 2009-09-05
> **Paqman said:**
> It's looking for a CD in the drive containing packages. To make it stop go to System > Admin > Software Sources and uncheck the CD as a source.

Thank you!

---

### Post by Niloc on 2009-09-05
I have a desktop and a laptop. both running Ubuntu 9.04.
The desktop uses a the server at "mirror1.ku.ac.th" but the laptop cannot find a server to download from.
It does all the serches then says :'No suitable download server was found'.
How do I tell it to go where the desktop is looking?

Thanks for any assistance...

Colin in Pai

---

### Post by Paqman on 2009-09-05
And the laptop has a working internet connection? If you go into System > Admin >Software sources you should be able to pick any particular server you want, or as you say, get it to scan for the best server. If it can't find _any_ servers then something is definitely wrong.

---

