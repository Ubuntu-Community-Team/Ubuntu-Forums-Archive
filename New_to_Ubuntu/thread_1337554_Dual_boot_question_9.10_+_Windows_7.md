---
title: "Dual boot question: 9.10 + Windows 7"
date: 2009-11-25
forum: New to Ubuntu
---

### Post by listerdl on 2009-11-25
Hi - I am keen to dual boot windows 7 and the latest ubuntu release.

I have found a very good tutorial [here: ]("http://lifehacker.com/5403100/dual+boot-windows-7-and-ubuntu-in-perfect-harmony") (From Lifehacker)

does anyone know another perhaps better tutorial?

thanks

---

### Post by sandyd on 2009-11-25
its pretty simple. 
just remember these things.
1. better to install windows first. then you dont need to re-install grub.
2. resize the partitions with the WINDOWS partition editor.

---

### Post by Wiebelhaus on 2009-11-25
> **carlee said:**
> its pretty simple. 
just remember these things.
1. better to install windows first. then you dont need to re-install grub.
2. resize the partitions with the WINDOWS partition editor.

carlee is right on , I second her suggestion.

---

### Post by listerdl on 2009-11-25
So if i am dual booting windows 7 and ubuntu then i need not think too much about creating swap files for either OS?

---

### Post by pi.boy.travis on 2009-11-25
> **listerdl said:**
> So if i am dual booting windows 7 and ubuntu then i need not think too much about creating swap files for either OS?

Windows 7 will handle the swap files automatically, and the Ubuntu installer will prompt you to create a swap partition.  Install Windows first, just limit the size of it's partition, leaving some space for Ubuntu.  If you leave unpartitioned free space, the Ubuntu installer can automatically calculate and create the partitions for you.

Hope this helps. . .

---

