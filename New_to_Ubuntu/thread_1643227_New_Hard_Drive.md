---
title: "New Hard Drive"
date: 2010-12-11
forum: New to Ubuntu
---

### Post by Chrissd on 2010-12-11
Hi all,

My hard drive is on the small size (40GB) and I'm looking at changing it for a bigger one. Ideally, I would just like to swap them over. 

Is there a safe and easy way of copying all the data on the old one onto a new one? The reason I don't really want to just copy my home directory is because there are lots of silly little details that I would like to keep, like the way I have apache2 configured at the moment, the way my duel screens are configured (took me two weeks to get them working, and I have no idea what I did to get them working.)

Appreciate I  almost certainly would have to fettle with /etc/fstab before it will work properly.

Many thanks in advance for any help and suggestions.

Chriss

---

### Post by albert s on 2010-12-11
clonezilla

this may be worth a try, Ive never used it, but have a copy just in case,
might be worth a google for you.

---

### Post by Chrissd on 2010-12-11
Do you think there would be any problem with installing Ubuntu onto the new hard drive, and then just copying all the files across with the old versions, or is that a recipe for disaster?

---

### Post by albert s on 2010-12-11
clonezilla will make an exact replica of your HD and let you move it to a new one.
Ive had a look at it and I think its what you need for a simply fix.

---

### Post by Chrissd on 2010-12-12
Hi,

I'm going through step by step the guide, but it looks too complicated for me. I don't understand what a 'repository' is.

Is there a even simpler way to create and then restore a disk image that uses plain english? I'm concerned I'll destroy my external hard drive with all my backups on.

---

### Post by tajiknomi on 2010-12-12
> **Chrissd said:**
> Hi,

I'm going through step by step the guide, but it looks too complicated for me. I don't understand what a 'repository' is.

Is there a even simpler way to create and then restore a disk image that uses plain english? I'm concerned I'll destroy my external hard drive with all my backups on.

[SIZE=2]Sorry for interfairing [/SIZE], [SIZE=2]But you can try Remastersys-backup > [/SIZE][http://www.dedoimedo.com/computers/remastersys.html](http://www.dedoimedo.com/computers/remastersys.html)

---

### Post by warfacegod on 2010-12-12
Indeed. Remastersys is excellent for this. Clonezilla is good too though.

---

### Post by Chrissd on 2010-12-28
Hi, I actually managed to do exactly what I want with dd and a guide that I found here on the forums.

Appreciate all the help offered and given.

---

