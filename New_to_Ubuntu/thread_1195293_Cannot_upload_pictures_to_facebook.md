---
title: "Cannot upload pictures to facebook"
date: 2009-06-23
forum: New to Ubuntu
---

### Post by asuastrophysics on 2009-06-23
[SOLVED]
Hi everyone,

I've been trying unsuccessfully to upload photos to facebook this past month. Every time I try it, I get a blank placeholder where the image is supposed to be. I don't get any warnings about installing plugins, etc. Libflashplayer.so is in the .mozilla/plugins folder. 

What else do I need to do to get this to work?
Sorry if this has already been asked.

---

### Post by ptn107 on 2009-06-23
I had similar problems with two Ubuntu 9.04 computers.  Install these packages and restart firefox: sun-java6-bin, sun-java6-jre, sun-java6-plugin

---

### Post by asuastrophysics on 2009-06-23
UPDATE: If you find yourself having my problem with a fresh install of ubuntu, with all the Java and Flash plugins installed, it may not be your computer's fault. Facebook can be slow sometimes. I hit "change profile picture" right before going into work today. 5 hours later, my picture finally changed.

---

### Post by monroetransfer on 2009-10-18
The answers so far in this thread did not work for me. I found my solution elsewhere in the forums ([link]("http://ubuntuforums.org/showthread.php?p=3725416#post3725416")). If anybody else has this problem and this thread didn't help, I would suggest following that link.

---

### Post by BarefootSoul83 on 2010-07-03
I found something interesting looking into this problem this morning... When pictures save to our Ubuntu machine (via F-Spot)they save as ".JPG"  so I went in and renamed some pictures as ".jpg" and BOOM! they populated in the field that wasnt seeing my pictures previously... soooooooooooo....I think its safe to say that some people may be having this problem because of a case-sensitive issue....

---

### Post by bongy_nut on 2010-07-04
I found that changing .JPEG files to .jpeg populates the field

Is their anyway to change multiple pictures from .JPEG to .jpeg without doing them all individually?

Thanks

---

### Post by smbrodie on 2010-08-03
> **bongy_nut said:**
> I found that changing .JPEG files to .jpeg populates the field

Is their anyway to change multiple pictures from .JPEG to .jpeg without doing them all individually?

Thanks


I would love to know the answer to this question!

---

### Post by uziel on 2010-12-11
Execute

```
for i in *.JPEG; do mv "$i" "`echo ${i%JPEG}jpeg`"; done
```

in terminal in the directory containing files to be renamed.

---

