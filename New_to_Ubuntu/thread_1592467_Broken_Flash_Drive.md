---
title: "Broken Flash Drive"
date: 2010-10-10
forum: New to Ubuntu
---

### Post by error919 on 2010-10-10
I was trying to install kubuntu on my flash drive using the instructions on the ubuntu website, run the installer like normal but tell it to use the flash drive instead of the hard drive. I unplugged the hard drive during this just be safe, however the program partitioned the flash drive then quit. I told I wanted 1gb of room for storage then the rest of it for kubuntu. I then selected next and it partitioned it but then the program quit. I tried booting to it and nothing happened. So I booted into windows and I found my flash drive however only the 1gb was there. So my question is how do install kubuntu on my flash drive or how to I get back all of my gigabytes? (There were 8 originally)

---

### Post by jnorthr on 2010-10-10
you HAVE made a backup of all your valuable data from the key haven't you ? You may need to reformat your key with a vfat or fat32 file structure, then try it again. This will wipe all your data from the key. Think i read somewhere that a key must have a fat32 format for the usb key creator to work corrrectly.

---

### Post by error919 on 2010-10-10
Fixed with hp usb disk storage format tool.

---

### Post by trentscott on 2010-10-10
Try this (using GParted -- a GUI utility):

[http://trentscott.com/2010/10/10/using-gparted-to-format-a-usb-stick/](http://trentscott.com/2010/10/10/using-gparted-to-format-a-usb-stick/)

---

