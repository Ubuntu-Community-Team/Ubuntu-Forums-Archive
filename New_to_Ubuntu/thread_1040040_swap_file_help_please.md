---
title: "swap file help please?"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by cairnzi on 2009-01-15
hi people, ive recently re-installed ubuntu 8.10 but made a rather silly error during installation,i have assigned 3.4GB to the swap file which is rather to much me thinks, does anybody no if i can re-assign the size to 512MB with out re-installing etc. ? many thanks.

---

### Post by spcwingo on 2009-01-15
You should be able to reboot with the live cd and resize your swap, then resize your Ubuntu partition to fill the extra space...just don't forget to make a backup.  ;)  After that reboot and and see if Ubuntu mounts the swap partition.  If not, you might have to manually edit fstab.

---

### Post by cairnzi on 2009-01-15
cheers for that, will i lose all my music etc. if i do it that way? cheers.

---

### Post by Captain_tux on 2009-01-15
> **cairnzi said:**
> cheers for that, will i lose all my music etc. if i do it that way? cheers.

Well, the only guarantee is that if you break it, you get to keep the pieces, hence the advice to make sure you **back up** your files... however, the process is rather simple and should be painless.

I have 2GB RAM and a 3.5GB swap partition. A bit much? Perhaps... but it's not hurting anything, so I left it alone.

---

### Post by cairnzi on 2009-01-15
@ captain_tux yeah its no hurting anyone and doesnt bother my system so think i will just leave it, cheers for the replies.

---

### Post by Captain_tux on 2009-01-15
> **cairnzi said:**
> @ captain_tux yeah its no hurting anyone and doesnt bother my system so think i will just leave it, cheers for the replies.

Cheers mate...

---

