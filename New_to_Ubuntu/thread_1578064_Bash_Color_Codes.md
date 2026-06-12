---
title: "Bash Color Codes"
date: 2010-09-19
forum: New to Ubuntu
---

### Post by proxyofsocks on 2010-09-19
I have a directory that is highlighted, the text is red and I can't cd to it. The directory is on a different partition of a separate install. Any idea what it means?

---

### Post by bodhi.zazen on 2010-09-19
red is often a broken link.

List the directory with 

```
ls -l
```

---

### Post by Ahava591 on 2010-09-19
If I remember correctly, here are some other common color codes you may see when you use 

ls -l

in bash:

Black text = regular file
Light blue text = directory
Green text = program or shell script
Pink text = image or video file

---

### Post by dcsoldschool53 on 2010-09-19
The codes are:

```
Executable files: Green
* Normal file : Normal
* Directory: Blue
* Symbolic link : Cyan
* Pipe: Yellow
* Socket: Magenta
* Block device driver: Bold yellow foreground, with black background
* Character device driver: Bold yellow foreground, with black background
* Orphaned syminks : Blinking Bold white with red background
* Missing links ( - and the files they point to) : Blinking Bold white with red background
* Archives or compressed : Red (.tar, .gz, .zip, .rpm)
* Image files : Magenta  (.jpg, gif, bmp, png, tif
```

As you can see the directory color is blue not red.

---

### Post by llamabr on 2010-09-20
Where are they set?

---

### Post by bodhi.zazen on 2010-09-20
> **llamabr said:**
> Where are they set?

for bash or ls ?

bash :

[http://www.cyberciti.biz/faq/bash-shell-change-the-color-of-my-shell-prompt-under-linux-or-unix/](http://www.cyberciti.biz/faq/bash-shell-change-the-color-of-my-shell-prompt-under-linux-or-unix/)

[http://www.systhread.net/texts/200703bashish.php](http://www.systhread.net/texts/200703bashish.php)

There are many more tutorials on that.

ls :

[http://linux-sxs.org/housekeeping/lscolors.html](http://linux-sxs.org/housekeeping/lscolors.html)

---

