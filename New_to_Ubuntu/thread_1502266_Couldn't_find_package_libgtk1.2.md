---
title: "Couldn't find package libgtk1.2"
date: 2010-06-05
forum: New to Ubuntu
---

### Post by Crazychicken on 2010-06-05
I need that for a game, and since I updated ubuntu to the lastest version, it's showing that error when I do "apt-get install libgtk1.2"

I found this
> **zer0pulse said:**
> Not sure about you but this worked for me.

Download these files (i386 when you're given a choice).
[http://packages.ubuntu.com/hardy/libgtk1.2-common](http://packages.ubuntu.com/hardy/libgtk1.2-common)
[http://packages.ubuntu.com/hardy/libglib1.2ldbl](http://packages.ubuntu.com/hardy/libglib1.2ldbl)
[http://packages.ubuntu.com/hardy/libgtk1.2](http://packages.ubuntu.com/hardy/libgtk1.2)

"hardy" is the 8.04 version of ubuntu, if you need something newer replace it with "intrepid" or "jaunty".
Karmic (9.10) and Lucid (10.04) don't seem to have packages built, but the 8.04 packages work for me on 10.04.

Go to a Terminal, and type these commands for each file in the order listed above.
sudo dpkg -i --force-architecture <file you downloaded>

Hope that helps!
, but what do I do exactly? I downloaded the files but when I try that command it says they're "not a debian format archive"

---

### Post by bubuzzz on 2010-06-12
why dont you use libgtk2.0 ?

---

### Post by ankspo71 on 2010-06-12
If libgtk2.0 doesn't work, the see below.
> **Crazychicken said:**
> 
, but what do I do exactly? I downloaded the files but when I try that command it says they're "not a debian format archive"
I think it's because you downloaded the source archive (tar.gz) on the upper right side of the pages. If you want the .deb files, look on the lower left side of the pages for the "i386" and "amd64" links in bold font. Those are the download links. Click on either one to download the one you need. Those will take you to download mirrors for the .deb files. 
Hope that helps

---

