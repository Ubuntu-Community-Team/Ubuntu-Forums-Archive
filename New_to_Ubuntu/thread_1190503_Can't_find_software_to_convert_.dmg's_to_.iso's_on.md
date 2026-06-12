---
title: "Can't find software to convert .dmg's to .iso's on ubuntu 9.04/linux mint 7"
date: 2009-06-17
forum: New to Ubuntu
---

### Post by linuxluver on 2009-06-17
This is probably an off-topic question, but I am trying to convert 4 .dmg files to .iso files on my Linux Mint 7 install. I can't find ANYTHING to use that actually works and I am extremely mad. Also, the first three files are around 650 MB and the 4th one is about 100 MB, if that helps.

[EDIT]: I just realized I put it in the wrong section. Please move it, somebody.

---

### Post by Sef on 2009-06-18
>  [EDIT]: I just realized I put it in the wrong section. Please move it, somebody. 	

Moved to absolute beginners.

---

### Post by 123456789123456789123456 on 2009-06-18
I'm not sure, I know on the mac, all I have to do is simply change the name, from .dmg to .iso, after doing so, programs like virtual pc can now read and use the file.  I don't know enough about the differences between disk image files to know exactly if they are the same, but with differnt names, or if it is programming differences.  have you googled it?

---

### Post by linuxluver on 2009-06-18
1234- the files are the install discs for Mac OS X that I got from BitTorrent, so, no, changing the file extension wouldn't work because it's formatted in HFS.

---

### Post by K.Y.A on 2009-06-18
> **linuxluver said:**
> 1234- the files are the install discs for Mac OS X that I got from BitTorrent, so, no, changing the file extension wouldn't work because it's formatted in HFS.

The admins on this forum are strongly against pirating, although I will admit I am a pirate:p

So, lets just forget you said that. . .


But I would like to know how you can do this, also. Would the convert command do it? I don't have any dmg files with me right now.

---

### Post by linuxluver on 2009-06-18
I'm afraid I'm not familiar with "convert".

---

### Post by Trebaruna on 2009-06-18
> **K.Y.A said:**
> although I will admit I am a pirate:p
This may be considered off-topic, but I for one strongly oppose piracy. There needs to be a strong international coalition to make sure the seven seas become and remain a safe place for cargo and passenger shipping, free of marauding bands of heavily armed criminals seeking to plunder and pillage.

Alternately, you may be confessing to copying a bunch of bytes digitally without the proper license. I'd say that hardly qualifies as piracy, and I wouldn't worry too much about it.

---

### Post by K.Y.A on 2009-06-18
> **linuxluver said:**
> I'm afraid I'm not familiar with "convert".

Convert is a terminal application for converting file types.

For instance:


```
convert /home/username/mac.dmg /home/username/mac.iso
```

---

### Post by linuxluver on 2009-06-18
WTF? The seven seas!? :lol: Besides, my parents want my iMac G3 fixed up soon because our old laptop blew up.

---

### Post by K.Y.A on 2009-06-18
> **Trebaruna said:**
> This may be considered off-topic, but I for one strongly oppose piracy. There needs to be a strong international coalition to make sure the seven seas become and remain a safe place for cargo and passenger shipping, free of marauding bands of heavily armed criminals seeking to plunder and pillage.

Alternately, you may be confessing to copying a bunch of bytes digitally without the proper license. I'd say that hardly qualifies as piracy, and I wouldn't worry too much about it.

I'm not the type of pirate that kills people or steals from cargo vessels.:D

I would do the latter, download a few bytes illegally. But, who cares? Not me. :)

---

### Post by K.Y.A on 2009-06-18
> **linuxluver said:**
> WTF? The seven seas!? :lol: Besides, my parents want my iMac G3 fixed up soon because our old laptop blew up.


[http://us.123rf.com/400wm/400/400/chistoprudov/chistoprudov0706/chistoprudov070600004/974145.jpg](http://us.123rf.com/400wm/400/400/chistoprudov/chistoprudov0706/chistoprudov070600004/974145.jpg)

---

### Post by ethoxyethaan on 2009-06-18
[http://vu1tur.eu.org/tools/](http://vu1tur.eu.org/tools/)

real pirates know what to do.

---

### Post by linuxluver on 2009-06-18
ethaan- ??? I need one for Linux(specifically for Linux Mint) and one that converts to iso.

kya- Did you know that the Pirate Party gained a seat in the E.U. Parliament? Arrgh!

---

### Post by Mornedhel on 2009-06-18
> **K.Y.A said:**
> Convert is a terminal application for converting file types.

What ?

Can you point the exact package you installed to provide this functionality ? Usually the command line tool 'convert' is part of the imagemagick suite of tools, and converts between image (as in jpg/bmp/etc) formats. I have never heard before of a single smart utility to convert any file type to any file type.

There is at least one tool, called iat, that converts several CD image formats into iso9660, but it doesn't understand .dmg.

---

### Post by linuxluver on 2009-06-18
kya- Yeah, morned is right, convert is an image converting tool. I just tried it in terminal and it comes up with all this stuff about converting images(like .jpg, .png, etc.).

---

### Post by Trebaruna on 2009-06-18
> **K.Y.A said:**
> I'm not the type of pirate that kills people or steals from cargo vessels.:D

I would do the latter, download a few bytes illegally. But, who cares? Not me. :)
What I meant to say was that copying information without the proper rights is not piracy; the term has been abducted to make it sound really bad, when in fact all your doing is digitally copying a bunch of binary numbers. But let's not get too much into the technicalities, politics and or moralities of digital distribution legally or otherwise.

[quote=linuxluver]
I need one for Linux(specifically for Linux Mint) and one that converts to iso.
[/quote]
IMG is pretty much the same as ISO, and you can download the source from the page linked to. Judging from the way the files in it look, you can install it like most other source packages.
So, very brief howto:
install build-essential and checkinstall.
Then, get the source, take your terminal and move to the dir where the code sits.
Type:
```

./configure
make
sudo checkinstall make install

```One by one. That should do it!

---

### Post by linuxluver on 2009-06-22
trebaruna- :confused: none of that made any sense.

---

### Post by ugm6hr on 2009-06-22
Discussions re: piracy, software piracy and politics.

Closed.

---

