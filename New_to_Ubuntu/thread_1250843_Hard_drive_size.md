---
title: "Hard drive size"
date: 2009-08-27
forum: New to Ubuntu
---

### Post by dragon_reborn on 2009-08-27
I am an absolute newbie with Linux, so forgive me if this is a stupid question. I have installed 4 new 300GB HDD's in my homeserver, formatted and partitioned them using "gparted". I tried to copy all my movies to one of the new drives but it would only copy 4.7GB. What am I missing?

---

### Post by nhasian on 2009-08-27
what filesystem did you use?  please tell me its not fat32 :)  Fat32 has a 4 gig file size limit.  you should use EXT3 or EXT4 instead.

---

### Post by dragon_reborn on 2009-08-27
I used ext3

---

### Post by j7%&lt;RmUg on 2009-08-27
Maybe it was a file i/o error iv had a few of them using ubuntu. get rid of the 4.7gigs on the hard drive already and try copying all your movies over again.

---

### Post by dragon_reborn on 2009-09-03
seems like it was a I/O error...

---

### Post by dragon_reborn on 2009-09-20
took LVM off and installed a HW raid controller - problem solved.

---

