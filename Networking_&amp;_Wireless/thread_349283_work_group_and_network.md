---
title: "work group and network"
date: 2007-01-30
forum: Networking &amp; Wireless
---

### Post by nikhilchandra on 2007-01-30
Hello friends,

I had just migrated from Window Xp to Ubuntu 6.06,
i was using windows for last 10 years and know not much of linux platforms and i am non technical (in computers) kind of person too,

i have to connect my another computer which is still using windows xp, to my computer using Ubuntu in LAN connection/ ethernet so how can i do this???

I used to connect them in windows by config. the workgroup, so in Ubuntu is there same procedure??

---

### Post by inCursorated on 2007-01-30
Hello and welcome to the linux world! :D 

I'm using kubuntu (KDE) not ubuntu (GNOME), so I can't guide you step-by-step.. .but try clicking Places > Connect To Server

Ubuntu supports browsing windows (smb) workgroups, so it *is* just like windows xp...

---

### Post by RandomJoe on 2007-01-30
If you wish to go the other way (the Windows machine browsing files on the Ubuntu one) you will need to set up Samba as a server on the Ubuntu machine.  I don't use it myself, so don't know all the details, but the server isn't installed by default (just client utils to browse a Windows server).

I just tried sharing a folder using System -> Administration -> Shared folders.  It popped up a box that says "You need to install at least either Samba or NFS in order to share your folders."  It also has checkboxes to install them then.  Otherwise, you could use Synaptic, search for 'samba' and install the server package (just called 'samba').  Then go to the Shared folder utility and set up a share.

---

