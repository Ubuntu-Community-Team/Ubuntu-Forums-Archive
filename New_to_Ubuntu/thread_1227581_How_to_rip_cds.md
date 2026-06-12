---
title: "How to rip cds"
date: 2009-07-30
forum: New to Ubuntu
---

### Post by Sup3r3g0 on 2009-07-30
I have an .nrg file. Rather than burn a cd and then try to rip it, is there a way to mount it to some sort of virtual drive and then rip the individual music files onto my hard drive so I can play it with Amarok? Or is there a way to make amarok play .nrg? The main goal is to be able to play all of my music with amarok.

---

### Post by apjone on 2009-07-31
Try using one of the below programs. Simple apt-get or use the ubuntu package synaptic.

iat - Converts many CD-ROM image formats to iso9660
mountmanager - User-friendly management of disks and partitions
nrg2iso - Extracts ISO9660 data from Nero ".nrg" files

---

### Post by binbash on 2009-07-31
you can convert it to iso with nrg2iso and mount it via mount command

---

### Post by neobux on 2009-07-31
Oh my god... Thanks so much for this. If this site didn't exist I think I would have gone insans! I don't understand how it can be SO hard to rip CDs as mp3 in ubuntu!! Thank god SOMEBODY has made it simple for an idiot like me to understand... Thanks!

---

### Post by llamabr on 2009-07-31
> **neobux said:**
> Oh my god... Thanks so much for this. If this site didn't exist I think I would have gone insans! I don't understand how it can be SO hard to rip CDs as mp3 in ubuntu!! Thank god SOMEBODY has made it simple for an idiot like me to understand... Thanks!

Well between the apps listed above, and the fact that gnome "just does it" when you put a blank cd in, I don't see that it's very hard at all.  What trouble are you having?

---

### Post by sydbat on 2009-07-31
> **llamabr said:**
> Well between the apps listed above, and the fact that gnome "just does it" when you put a blank cd in, I don't see that it's very hard at all.  What trouble are you having?The trouble all spam bots have - trying to sound like they are a real person and get people to click the links in their posts...

---

### Post by vinutux on 2009-07-31
Try **gisomount**```
sudo apt-get install gisomount
```
:D

---

### Post by llamabr on 2009-07-31
> **sydbat said:**
> The trouble all spam bots have - trying to sound like they are a real person and get people to click the links in their posts...

Hi.  Yes, thanks for putting me in check.  I *was* curious about the propriety of the links in the signature.  I'll be more vigilant in the future.

---

