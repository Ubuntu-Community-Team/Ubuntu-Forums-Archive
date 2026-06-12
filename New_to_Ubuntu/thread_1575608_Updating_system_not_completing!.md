---
title: "Updating system not completing!"
date: 2010-09-16
forum: New to Ubuntu
---

### Post by Segofam on 2010-09-16
My MSI VR60i works excellently with Ubuntu Lucid Lynx, but for some reason, when updating, it now shows the following - What should I do?

Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom://Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)/dists/lucid/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Some index files failed to download, they have been ignored, or old ones used instead.

Kind regards,

Scott

---

### Post by dcsoldschool53 on 2010-09-16
**Click System, Administration, Software source, and type in your password. Remove the check mark under CDrom with Ubuntu.**

---

### Post by Gone fishing on 2010-09-16
I think you have the CD in your repositories you need to remove this. In synaptic go to click repositories and untick the CD.

---

### Post by Segofam on 2010-09-16
Hi folks,

Thanks for that, I have un-ticked the CDrom thingy in the repository, actioned an update and all is good :)

Until next time...

Kind regards,

Scott

---

