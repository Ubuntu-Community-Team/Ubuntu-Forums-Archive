---
title: "how to view cdrom contents in terminal"
date: 2009-05-04
forum: New to Ubuntu
---

### Post by raymondvillain on 2009-05-04
Running Jaunty.  Would like to open a terminal session and view the audio tracks on a CD in the CDROM drive.

On my machine, if I type ls -l cdrom

I get back "cdrom -> media/cdrom"

What identifies a cdrom drive in the shell (bash for my machine)?

I can easily see everything from Nautilus, but I need to be able to do it from a terminal window.

Thanks in advance.

---

### Post by Vonnick on 2009-05-04
Try...

```
cd media/cdrom
cd media/cdrom0
cd media/cdrom1
```

Whichever one of those works.

Then...

```
dir
```

Which will show you the contents of directory.

---

### Post by Tyke91 on 2009-05-04
please stop lying :P

those commands will work if you're already in the / folder. if not, then

```

cd /media/cdrom
ls -a
```if you want to move and look.

the -a is used to see hidden files.

OR

if you just want to look
```
ls -a /media/cdrom
```dir will work as well, but ls has more features (like syntax highlighting for different types of files!). If you want to recursively show every file in the CD so that you can scroll through them (which is sometimes handy)
then type
```
ls -Ra /media/cdrom | less
```

---

