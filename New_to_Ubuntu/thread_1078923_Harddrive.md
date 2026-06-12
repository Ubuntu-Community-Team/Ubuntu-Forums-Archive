---
title: "Harddrive"
date: 2009-02-23
forum: New to Ubuntu
---

### Post by Zach.Town on 2009-02-23
Hello :). I dual booted Ubuntu Feisty Fawn and Windows 7. I now have a separate computer for Ubuntu and I was wondering if I could format the 100gigs I gave to my dual boot and make it accessible on my Windows again.

---

### Post by JustANewb on 2009-02-23
Its possible.  You would have to run a fixmbr if you set it up so that the Grub menu loaded first...

---

### Post by Zach.Town on 2009-02-23
Any idea how I could figure out how to do that?

---

### Post by stalkier on 2009-02-23
> **Zach.Town said:**
> Any idea how I could figure out how to do that?

Use "Super Grub Disc" It is an awesome tool. It is free also.

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

---

### Post by Zach.Town on 2009-02-23
So is it self explanatory? And holy **** your avatar just gave me a nostalgia rush.

---

### Post by Zach.Town on 2009-02-23
guilty bump...

I don't know what to do... :/

---

### Post by Zach.Town on 2009-02-24
A link to a guide maybe?

---

### Post by louieb on 2009-02-24
[IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")

---

### Post by Zach.Town on 2009-02-24
Thanks :) this will make the partition usable on my windows also?

---

### Post by louieb on 2009-02-25
Two steps

[LIST=1]
[*]replace grub [IDBS Remove/Replace/Uninstal Grub]("http://www.users.bigpond.net.au/hermanzone/p18.htm")
[*]make disk space available to windows. Depends on what you want to do. Add it the existing win partition? Use it as a separate data partition?
[LIST]
[*]vista - you can use vistas disk management
[*]xp - Gparted can do it too. [GParted Documentation - general]("http://gparted.sourceforge.net/larry/generalities/gparted.htm")
[/LIST]
[/LIST]
):P

---

