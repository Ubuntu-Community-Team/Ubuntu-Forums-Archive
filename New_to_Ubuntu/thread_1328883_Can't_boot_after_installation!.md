---
title: "Can't boot after installation!"
date: 2009-11-16
forum: New to Ubuntu
---

### Post by colormoon on 2009-11-16
I install karmic on my old pc. After installation it show error after grub.

error: The initrd is too big
press any key to continue

The one solution I found out say that to disable the "Memory Hole" on bios, but my bios have no this choice. What should I do?

---

### Post by zeroseven0183 on 2009-11-17
What's the hardware specs of your **old** PC?

---

### Post by colormoon on 2009-11-17
> What's the hardware specs of your old PC? 

my **old** pc:
celeron 1Ghz
motherboard P6VEM
320 MB Ram
40 GB HDD

---

### Post by zeroseven0183 on 2009-11-17
Have you tried reinstalling it?

Although the minimum requirement of Ubuntu is 256MB and you have 320MB RAM, I would suggest trying another Linux distro that does not require hardware specs as big as that of Ubuntu. I would recommend you to try [Crunchbang Linux]("http://crunchbanglinux.org/"). It uses another kind of desktop manager, Openbox, instead of the GNOME in Ubuntu.

> CrunchBang Linux is an Ubuntu based distribution offering a great blend of speed, style and substance. Using the nimble Openbox window manager, it is highly customisable and provides a modern, full-featured GNU/Linux system without sacrificing performance.

---

### Post by ukripper on 2009-11-17
Here is a bug reported on launchpad - [https://answers.launchpad.net/ubuntu/+question/90337](https://answers.launchpad.net/ubuntu/+question/90337)

[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/429898](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/429898)

One possible soultion posted on there was:
> 
johnhowe  wrote on 2009-11-01: 
For anyone else with the same problem, the option I disabled in the bios was
Advanced -> Advanced Chipset Features -> Memory Hole Remapping



.

can you try above in BIOS

---

### Post by colormoon on 2009-11-29
thank you but my bios have no memory hole option

---

### Post by bumanie on 2009-11-29
Try crunchbang as suggested or else try [puppy linux]("http://puppylinux.org/main/index.php?file=Overview%20and%20Getting%20Started.htm"), it would fly on that machine :- now worries.

---

### Post by opt1k on 2009-11-29
I would actually recommend that you try Debian since Debian = Ubuntu .... Its just a little different ;)  
It shouldnt give you that problem and you will still have everything you had with ubuntu.

---

### Post by nikhilbhardwaj on 2009-11-29
try arch linux
if you are a noob
then chakra-project will be great for you

---

### Post by opt1k on 2009-11-29
> **nikhilbhardwaj said:**
> try arch linux
if you are a noob
then chakra-project will be great for you

I wouldnt recommend KDE in any form to anyone, but to each their own. "noobs like kde"
How about another... slitaz.org for older slow pc's.

---

