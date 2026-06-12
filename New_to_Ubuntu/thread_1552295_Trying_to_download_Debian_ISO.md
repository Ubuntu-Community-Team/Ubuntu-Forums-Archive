---
title: "Trying to download Debian ISO"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by McTwitch on 2010-08-13
I've made it to here

[HTML]http://cdimage.debian.org/debian-cd/5.0.5/alpha/iso-cd/[/HTML] But I don't know which file I should download and burn to a CD. It's one of the ISO's, but I don't know which one.

---

### Post by Zeike on 2010-08-13
First of all, you've selected the 'alpha' architecture.  Do you actually have an alpha, or did you mean to select x86 or AMD64 instead? (This is dependent on what processor you have).

The debian installation guide is here: [http://www.debian.org/releases/stable/installmanual](http://www.debian.org/releases/stable/installmanual)

and it should walk you through the process of selecting which iso to download.  But you MUST make sure you choose the correct architecture.

---

### Post by Paul820 on 2010-08-13
If you have an internet connection the get the > debian-505-alpha-netinst.isoIt installs a basic system and then gets the rest of the files off the internet. Otherwise you might need disc1, 2, and 3.

---

### Post by McTwitch on 2010-08-13
Okay, how do I know which architecture to choose though?

---

### Post by Zeike on 2010-08-13
What processor do you have?

98% of the time i386 will work just fine.
use can use amd64 if you have a 64 bit processor (Intel Core 2 & more recent often support 64 bits), although i386 also works on these processors, if you use that you won't be able to take advantage of 64bit features.

If you run 'cat /proc/cpuinfo' in a terminal it will tell you what kind of cpu you have.

---

### Post by linux18 on 2010-08-13
ubuntu doesn't work on alpha, if you have ubuntu it's either x86, x86_64, or PPC. Unless you've converted a pre 2006 mac your computer will work with the x86. 

use this command to download:
```
 wget --progress=dot http://cdimage.debian.org/debian-cd/5.0.5/i386/iso-cd/debian-505-i386-CD-1.iso 
```

then right-click > write image to disk (or whatever the right click option is)

---

### Post by TNT1 on 2010-08-13
> **linux18 said:**
> 

use this command to download:
```
 wget --progress=dot http://cdimage.debian.org/debian-cd/5.0.5/i386/iso-cd/debian-505-i386-CD-1.iso 
```then right-click > write image to disk (or whatever the right click option is)

Why are there cd.1, cd.2, and so on?

---

### Post by Zeike on 2010-08-13
> **TNT1 said:**
> Why are there cd.1, cd.2, and so on?

They just have additional software packages.

Net install is the easiest way to go if you have internet access.

---

### Post by gvoima on 2010-08-13
I always use the netinst iso if I have internet access available.

---

### Post by McTwitch on 2010-08-13
Alright, another stupid question...Is there anyway to format or otherwise erase a CD-R? They're all I have, and apparently they've all got stuff on them.

---

### Post by linux18 on 2010-08-13
> **McTwitch said:**
> Alright, another stupid question...Is there anyway to format or otherwise erase a CD-R? They're all I have, and apparently they've all got stuff on them.
nope

---

### Post by wojox on 2010-08-13
> **McTwitch said:**
> Alright, another stupid question...Is there anyway to format or otherwise erase a CD-R? They're all I have, and apparently they've all got stuff on them.

You can't erase it but you can over write it. :)

---

### Post by McTwitch on 2010-08-13
I thought that you could only write over the RW ones.

---

### Post by wojox on 2010-08-13
> **McTwitch said:**
> I thought that you could only write over the RW ones.

CD-RW you can erase or reformat, what have you. CDR you can overwrite.

---

### Post by McTwitch on 2010-08-14
Alright, the Debian netinst iso is downloaded and burnt. Thanks for all of your help!

---

