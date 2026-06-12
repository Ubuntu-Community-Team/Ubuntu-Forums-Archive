---
title: "how to edit ai files"
date: 2009-02-22
forum: New to Ubuntu
---

### Post by kapi on 2009-02-22
hi have a small dilemma.

designed some graphics a few years ago in illustrator and saved as AI. 

Now I use Inkscape and Gimp and can't open the old files - can anyone provide a getout?

thanks 

Kapi

---

### Post by geirha on 2009-02-22
Install [imagemagick](apt:imagemagick), then try converting them to some other format with imagemagick's convert command. For example ```
convert file.ai file.jpg
``` will convert it to jpg, that is, if imagemagick is able to read .ai-files.

---

### Post by kapi on 2009-02-22
have problems installing imagemagic
am using the commands stated but it keeps telling me that no such file exists


Kapi

---

### Post by yther on 2009-02-22
Sometimes Illustrator files are saved in EPS format.  Try typing "head yourfile.ai" in a terminal and see if it starts with something like (if I remember right) "%!PS-Adobe-x.x".  I think some of them may also be PDF internally; in that case it would have "%PDF-1.x".

The beginning of this thread [on Inkscape and AI](http://ubuntuforums.org/showthread.php?t=338632) has some ideas.  I'm thinking if Inkscape can't deal with the files by itself, you might get by with using a PS- or PDF-to-EPS conversion.

---

### Post by geirha on 2009-02-22
> **kapi said:**
> have problems installing imagemagic
am using the commands stated but it keeps telling me that no such file exists


Kapi

You need to be in the same directory as the .ai file, or provide the full path to it. If you are unfamiliar with the terminal, the easiest is to do the following (in the terminal). 

Type in convert with a space behind it.
Locate the .ai-file in nautilus and drag it over to the terminal window.
In the terminal window the full path to the .ai file should now appear behind convert.
Add another space and type in the destination filename. E.g. file.jpg, file.csv, file.png or whatever you prefer.

---

### Post by mcduck on 2009-02-22
> **kapi said:**
> have problems installing imagemagic
am using the commands stated but it keeps telling me that no such file exists


Kapi

the thing is that it really *is* called Imagemagick, with the "k" at the end.. ;)

Also, when using the commands you of course need to be in the directory where the file is (or use full path) and replace "file.ai" with the actual file name.

Anyway, the downside of this way is still the fact that it won't allow you to edit .ai files, or even keep them as vectors. That's the nasty thing about proprietary file formats, they rarely really work with anything else than the program they were made with.

Inkscape is able to open .ai files (if you install some extra libraries, can't remember which ones), but it doesn't have full support for them which means that only very basic illustrations work correctly. But to give some good news as well, Illustrator works quite fine with Wine..

---

### Post by geirha on 2009-02-22
> **mcduck said:**
> Inkscape is able to open .ai files (if you install some extra libraries, can't remember which ones), but it doesn't have full support for them which means that only very basic illustrations work correctly. But to give some good news as well, Illustrator works quite fine with Wine..

+1, if Adobe Illustrator works with wine, then install it with wine and use it to convert the images.

---

