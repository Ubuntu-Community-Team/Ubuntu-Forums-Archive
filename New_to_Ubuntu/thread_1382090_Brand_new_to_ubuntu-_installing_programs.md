---
title: "Brand new to ubuntu- installing programs/"
date: 2010-01-15
forum: New to Ubuntu
---

### Post by Zappanale on 2010-01-15
Hi,
A few days ago my windows 7 laptop ran into some major problems. TL;DR version: it's utterly borked. It was suggested until (if) I can get it working again, I use ubuntu. 
I have never used linux before, but am giving it a go.

I was then given a copy of Postal 2 (on of my favourite games) for Linux by a friend, but cannot for the life of me install it. The problem is, after reading this:
[http://ubuntuforums.org/showthread.php?t=781352](http://ubuntuforums.org/showthread.php?t=781352)
I still am unsure as to what to do.
The game is a downloaded copy (from the official store, all legit).

Can anyone give me any advice, purely to tide me over until I really get familier with ubuntu?


As an aside, I am liking ubuntu. If I can get my head around things such as installing programs, etc, I may well not bother getting my Windows 7 up and running.

---

### Post by audiomick on 2010-01-15
How you install it depends on what sort of file you got. Perhaps you could tell us if it is a .deb file or a .tar.gz or something else.

---

### Post by Zappanale on 2010-01-15
Well, it came as a .zip file, within which there's a .bin file. The file is called postal2-linux.bin

---

### Post by audiomick on 2010-01-15
Ok. No wonder the page you linked to confused you. It is talking about installing from the repositories, which is where the "standard" software comes from.

I will have to look a bit to find out what to do with a .bin. Bear with me, I'll get back to you.

---

### Post by marshmallow1304 on 2010-01-15
Extract the archive, then open a terminal (Applications->Accessories->Terminal) and change to the directory in which the .bin resides.
```
cd </path/to/file>
```
where </path/to/file> is the location.  If the bin is on your desktop, it would be
```
cd /home/<yourusername>/Desktop
```
Make the bin executable:
```
chmod +x <name-of-file>.bin
```
then run it:
```
./<name-of-file>.bin
```

These are general instructions.  If something doesn't work or gives an error, post it.

---

### Post by Zappanale on 2010-01-15
It's installing. Thanks guys!

Oh, and as an aside, It's running faster and with better graphics than this game ever did under windows, of any version.

---

