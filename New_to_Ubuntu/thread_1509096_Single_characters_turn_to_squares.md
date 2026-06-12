---
title: "Single characters turn to squares"
date: 2010-06-13
forum: New to Ubuntu
---

### Post by KdotJ on 2010-06-13
This is a problem which seems to occur randomly and not all the time. What happens is, every now and then a character of text turns into a square. For example, let's say the character 'd'. When this occurs, every place where a 'd' should be I get a little blank square instead.

Everything gnome-based is affected; window titles, file names, folder names, paths, menu items... etc

Other text, such as in a file, on a webpage is not affected. 

The issue goes away after a reboot but it is quite annoying.

Any ideas?
Thanks in advance

---

### Post by -humanaut- on 2010-06-13
Are you using any proprietary video cards? also make sure you encoding is UTF-8

---

### Post by KdotJ on 2010-06-13
> **-humanaut- said:**
> Are you using any proprietary video cards? also make sure you encoding is UTF-8

Thanks for the reply, I have an ATI card but I'm using the open-source drivers. And as for the encoding, I haven't changed anything related to character encoding so I'm guessing it would be UTF-8 as standard

---

### Post by KdotJ on 2010-06-16
Bump.

This is getting rather annoying now. Currently, all my slashes (/) and 's' are not showing up.

Please does anyone experience this or have any other advice?

---

### Post by wojox on 2010-06-16
Try updating your font cache?

```
fc-cache-fv
```

---

### Post by KdotJ on 2010-06-27
Bump.

Now my 't' is not showing up...

Here is an example of what a dialog box from gedit looks right now...

[IMG]http://img686.imageshack.us/img686/9586/nots.jpg[/IMG]

---

### Post by DaneM on 2010-09-30
It would appear that the data on your hard drive that relates to your fonts is becoming corrupt.  I recommend doing a read-only badblocks test on your system drive.  It would be something like this (in a terminal window).

```

sudo badblocks -svb 4096 /dev/sda

```

Note: do NOT put the partition number after the drive letters (such as in /dev/sda1).

This should tell you if you have a failing hard drive.  Also, try running a memory test from the boot screen of an Ubuntu Live CD.

---

### Post by virtual reality on 2010-10-28
Hi, similar issue here, couldn't find any thread closer to the problem than this one yet (have you?).

In my case it's not single characters turning to squares, but rather pixels gone missing (e.g. I might get a "white line" through a letter, see attached screenshot: capital S, decapitated... :-( )

[IMG]http://ubuntu-ky.ubuntuforums.org/attachment.php?attachmentid=173753&d=1288280579[/IMG]

I might try to run PC Doctor / Lenovo System Toolbox, Ubuntu stuff, or other hardware checking tools unless I find a software cause / solution.

Anyone else affected?

Any further ideas?

I'm on an SSD, btw. Running Maverick.

Thanks!

tp.

---

### Post by virtual reality on 2011-03-21
(modest) bump!

ps: too lazy yet to start a new thread...

---

