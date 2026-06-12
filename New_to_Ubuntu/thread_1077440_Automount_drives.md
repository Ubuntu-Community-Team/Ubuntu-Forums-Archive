---
title: "Automount drives"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by Periswell on 2009-02-22
hello

for the last couple of hours i have tried to get mythbuntu to automount my external harddrive so that it is in /media/disk as soon as my computer is on so i dont have to open it in the filemanager. I have tried telling thunar to hot-plug it but it does not work, i install nautilus and told it to hot-plug but that does not work, i created a script off of the website > [http://www.racmar.com/content/view/36/42/](http://www.racmar.com/content/view/36/42/)
but that did not work. Please does anyone have an answer, i am sick of page after page of google results. Thanks in advance.

-joshua

---

### Post by blueridgedog on 2009-02-22
I assume the external drive is on all the time and plugged in all the time?  If so, can you post the output of:

```
sudo fdisk -l
```

And tell which drive it lists as being the external drive?

Also, could you post the output of:

```
blkid /dev/s*
```

---

