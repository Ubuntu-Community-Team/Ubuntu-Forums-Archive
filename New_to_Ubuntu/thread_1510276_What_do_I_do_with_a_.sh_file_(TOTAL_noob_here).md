---
title: "What do I do with a .sh file? (TOTAL noob here)"
date: 2010-06-15
forum: New to Ubuntu
---

### Post by logos2501 on 2010-06-15
So I'm trying to install a Linux equivalent of AutoCad.  I found one and I have to compile it myself. "A script to build everything  from scratch on any Linux / Unix system is also included" with the source code.  I've navigated my way to the .sh file with the terminal, now what?

Also, I have very limited experience with Linux and programming (C, C++), so I'm not totally helpless.

Thanks!

---

### Post by NCLI on 2010-06-15
Usually, you just have to run it. Right-click the file, select properties, permissions, then check the "Allow to run as program box, if it isn't already checked.

Then just open a terminal, drag-and-drop the file in it, and press enter.

If it complains about permission, drag-and-drop it again, but before hitting enter, use the arrow keys to get to the beginning of the line, then enter "sudo."

Example:
```
sudo '/home/someguy/Downloads/Some Application/Install.sh'
```

---

### Post by Rytron on 2010-06-15
Try this:

```
./yourfile.sh
```

---

### Post by logos2501 on 2010-06-15
Both of those work, but it's not finding something that it needs.  This is what happens when I do either of the things you say:
> 
build_qcad.sh
Usage: ./build_qcad.sh [options]
options:
  demo        build demo version
  debug       add debug menu
  cam         build CAM support if available
  scripting   build scripting support if available
  prof        build professional version
  noclean     don't clean (speeds up building if the options don't change)
  noconfig    don't run configure (speeds up building if the options don't change)
  noprepare   don't run prepare (speeds up building if the options don't change)
  notrans     don't generate translations
  distcc      use distcc for distributed compilation. DISTCC_HOSTS must be set.

QTDIR is: 
QMAKESPEC is: 
Platform is Linux
QTDIR not set. Aborting..

Is QTDIR where it is supposed to install? and I didn't specify it?

---

### Post by NCLI on 2010-06-15
Try install the package "build-essential" from the software center.

---

### Post by NCLI on 2010-06-15
I can see on the QCAD website that you also need the package "libqt3-mt-dev", which can also be installed from the Software Center.

---

### Post by logos2501 on 2010-06-15
New problem: I don't have the software center.  I'm running a Dell laptop with Ubuntu 9.04.  I tried using the synaptic package manager, but this is what it says:

> Failed to run /usr/sbin/synaptic as user root.

The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.

This is my work computer, so maybe they've set it up so I can't do certain things?

Is there anyway that I can install the software center?  I've looked around and I haven't found anything about installing it, just using it.

Thanks,

---

