---
title: "Program directories..."
date: 2010-01-20
forum: New to Ubuntu
---

### Post by driebel on 2010-01-20
I probably should have figured this out already, but I haven't found a clear explanation in a guide or reference, so I'm just going to ask.  I'm running Hardy.

Can someone give me, or point me to a clear explanation of how Ubuntu programs are organized within the directory structure of the OS?  What is the difference between
/bin
/usr/bin
/usr/local/bin

or between
/lib
/usr/lib
/usr/local/lib

Why is there /usr/share and /usr/local/share?

For example, I've been looking through the forums for advice on managing some adobe plugins for firefox, and it seems very confusing to determine where the plugin files are supposed to go.  Sometimes they go to /usr/local/...  sometimes to {home}/.mozilla, and I even saw one post that suggested Adobe reader would be found under /opt, a directory that is empty on my system.  Is there a guiding logic behind these seemingly arbitrary placements?  I can never seem to predict where I'm going to find the binaries of a given program.

Thanks!

---

### Post by llamakc on 2010-01-20
[http://www.tuxfiles.org/linuxhelp/linuxdir.html](http://www.tuxfiles.org/linuxhelp/linuxdir.html)

**< [B]/usr/local** >[/B]

 		This is where you install apps and other files for use on the local machine. If your machine is a part of a network, the /usr directory may physically be on another machine and can be shared by many networked Linux workstations. On this kind of a network, the /usr/local directory contains only stuff that is not supposed to be used on many machines and is intended for use at the local machine only.


So /usr/local/bin would represent the location that binaries or start-up scripts for non-apt installed packages would end up. Often, /opt is where non-package management software is also installed. 



Hopefully that page explains some. I'll check if there's an Ubuntu-specific page also.

---

