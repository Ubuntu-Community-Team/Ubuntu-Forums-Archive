---
title: "iso files"
date: 2009-04-01
forum: New to Ubuntu
---

### Post by vagelism on 2009-04-01
Hello .
I have some iso files that when I load them , I see no files inside them... Is there a possibility to be hidden somehow?
Any ideas how to manipulate it? I can not see regular or hidden files on them...
Any help is appreciated.
Thank you in advance.

---

### Post by doas777 on 2009-04-01
how do you mount them?

---

### Post by aeiah on 2009-04-01
how are you 'loading' them? the usual phrase to use is mount, since you're mounting them like you'd mount a filesystem or drive or something. are you loading/mounting the iso in a different way? what are you expecting to find on these .iso images?

---

### Post by vagelism on 2009-04-01
i expecto to find some word and pdf files.
I am trying to mount it with AcetonelISO2.
It can not mount the iso file.
In window the file is mounted but is totaly empty the drive when I open it.
Thank you

---

### Post by aeiah on 2009-04-01
in windows? do you realise you're posting in a linux forum? we could tell you how to mount the iso file in linux, if that helps...

---

### Post by ibuclaw on 2009-04-01
To view the contents of an iso image:

```
mkdir ~/mount
```
```
sudo mount -o loop **name_of_file**.iso ~/mount
```

Or install gmountiso
```
sudo apt-get install gmountiso
```
Then go to **Applications->System Tools->Gmount-ISO**

Presuming that you are using one of these methods to mounting the iso images using then what you see is what you have access to seeing.

ISO image files contain alot more than a data layer on them, and can be composed of various other layers that may/may not be readable.

Regards
Iain

---

### Post by vagelism on 2009-04-01
well when i try to mount it on linux i get the message
CD-ROM is not an ISO 9669 FORMAT.

---

### Post by lisati on 2009-04-01
If it's not a silly question, what are the ISO files referred to by the OP? 

One of the common uses for ISO files is as a snapshot of what's on a CD or DVD, and they're often intended to be burned directly to disk as a disk image.

---

### Post by ibuclaw on 2009-04-01
> **aeiah said:**
> in windows? do you realise you're posting in a linux forum? we could tell you how to mount the iso file in linux, if that helps...

Not everyone is quite as fluent in english as others. But I think he means **Nautilus** when he says **window** (note, he didn't say window**s**).

---

### Post by vagelism on 2009-04-01
I get an error.

You must specify filesyste type!!!!

---

### Post by Sir Jasper on 2009-04-01
Hi,

It may be necessary to convert each ISO file onto a CD.

Can you give us the name of one of your ISO files and
say where you downloded (or got it from) and what type
of program you are expecting it to run?

This might help me to help you.

My regards

---

