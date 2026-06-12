---
title: "simple command script to resize images"
date: 2010-01-02
forum: New to Ubuntu
---

### Post by Ylon on 2010-01-02
I need to upload some photo on a old cellphone, image need to be resized to be viewable on it: so I need my linux-box resize them for me.



What I do:
this executable in /home/user/ConvertImages
```
#!/bin/bash
convert -geometry 220x220 "$1" "$1"
```
Then make a lancher link on my desktop, this is not *exactly* what I do want since it "overwrite" the old file.

I want the same exact file copy and resized over my desktop.. with samefilename (and overwritten if source file is on dekstop as well)
IE, the file: /media/UsbKey/Photos/Sea/beach_0001.jpg
end resized in: /home/user/Desktop/beach_0001.jpg


Secondary: is this also possible make input multiple file (multi select > drag&drop)

---

### Post by Ylon on 2010-01-02
Ok, I did just discover: sudo apt-get install nautilus-image-converter

which already do this job in such charming way that I do need nothing else. Solved

---

### Post by Paqman on 2010-01-02
> **Ylon said:**
> Ok, I did just discover: sudo apt-get install nautilus-image-converter

That's one of my favourite plugins :P

It uses a command line app called imagemagick, if you ever want to use it in a scritp, btw.

---

