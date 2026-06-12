---
title: "Youtube problems"
date: 2010-07-24
forum: New to Ubuntu
---

### Post by Punkristo on 2010-07-24
Whenever I try to watch a YouTube video I have to click and move around the mouse on the play/pause button to get it to work. It takes me a few clicks to get it to actually press the button. Anybody else has this issue or knows how to fix it?

---

### Post by Ony on 2010-07-24
Hello,Punkristo

I am not sure how much help this is going to be with your problem, but I had the same thing. It wasn't until I installed flash then did a reboot that the problem had gone away on me, sorry if this does not help you ;-)  Just felt like I should say something.

Best of luck

Ony

---

### Post by mapes12 on 2010-07-24
Make sure you have all the non free codecs installed:-

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by lovinglinux on 2010-07-24
This usually happens when you are using the 32bit plugin on a 64bit system. To fix that you need to edit the npviewer file, if you are using a 64bit machine. Open it with the command below:

```
gksudo gedit /usr/lib/nspluginwrapper/i386/linux/npviewer
```

Then add the following line before the last line of that file:

```
export GDK_NATIVE_WINDOWS=1
```

The file content should look like this:

```
#!/bin/sh
TARGET_OS=linux
TARGET_ARCH=i386
export GDK_NATIVE_WINDOWS=1
. /usr/lib/nspluginwrapper/noarch/npviewer
```

Save the file and restart the browser.

---

### Post by Punkristo on 2010-07-24
Installing the non free codecs worked. Thanks!

---

