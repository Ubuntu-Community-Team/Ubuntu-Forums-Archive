---
title: "accessing my external HD using terminal"
date: 2010-09-22
forum: New to Ubuntu
---

### Post by daveboy23 on 2010-09-22
i have to HD - one internal the other USB.  the thing is - i want to use terminal (also called Bash?) to access it.  why? cause i want to mount ISO from there.
my problem is - if i open the HD then right click and open in terminal, no problem.  but id like to know how to get to it with terminal the hard way.

i type:
cd /media/
dir
shows me the devices (including my My Passport HD)
but when i type cd /My Passport/ it can't find it... (or and other combo for that matter)

thx for your help

---

### Post by ibizatunes on 2010-09-22
if you want to know your device name
sudo fdisk -l
will display all your disk type device like usb pen / harddrive


mount /dev/(your device) /media/(mount point)
then cd to the /media/(mount point)

---

### Post by spiky001 on 2010-09-22
Try typing 
```
media/"My passport"/
```

if there is a space in the name of the folder/file use ""to incase the word

---

### Post by luvshines on 2010-09-22
Well is that a typo or you actually wrote

cd /My Passport/

I think once you do cd /media, you should do cd ./My\ Passport to get to your HD ["\" to escape the space in your path name]

If that works, then mounting ISO image is easy

mount -o loop -t iso9660 <file-name> <mount-path>

---

### Post by CharlesA on 2010-09-22
Try this please:

Type this:

```
cd My
```

Then hit the tab key on yer keyboard, that'll autocomplete the whole line for you.

It's probably listed as "My Passport HD"

---

### Post by daveboy23 on 2010-09-22
> **spiky001 said:**
> Try typing 
```
media/"My passport"/
```if there is a space in the name of the folder/file use ""to incase the word


That worked great!
now the second problem, if we're already on the subject...
i'm trying to mount an .ISZ
is there a way to do it with a program? even so, i'd still like to see the code in terminal (if that's possible)

---

### Post by CharlesA on 2010-09-22
Tab is yer friend for file/folder names. :)

Anyway, I don't know of any program that'll read that file type, but it might exist.

---

### Post by spiky001 on 2010-09-22
From googling it sayes it,s a compressed iso not found anything for it, they did mention uncompressing it,

[http://ubuntuforums.org/showthread.php?t=1557023&page=1](http://ubuntuforums.org/showthread.php?t=1557023&page=1)

---

