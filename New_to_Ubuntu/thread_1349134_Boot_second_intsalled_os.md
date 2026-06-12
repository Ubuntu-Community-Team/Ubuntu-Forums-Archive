---
title: "Boot second intsalled os"
date: 2009-12-07
forum: New to Ubuntu
---

### Post by Dreigo42 on 2009-12-07
I have ubuntu 9.10 and windows xp in a dual boot using grub. I use ubuntu most of the time but there are just some things that I still need windows for. They are installed on seperate hard drives and I would like to know if there is a way to simply boot the other hard drive in a virtual machine? I have tried different virtual machine clients and they all want to do a clean install. Can anybody help?

---

### Post by jimmy the saint on 2009-12-08
[http://lmgtfy.com/?q=virtualbox+boot+existing+partition](http://lmgtfy.com/?q=virtualbox+boot+existing+partition)

---

### Post by lidex on 2009-12-08
> **jimmy the saint said:**
> [http://lmgtfy.com/?q=virtualbox+boot+existing+partition](http://lmgtfy.com/?q=virtualbox+boot+existing+partition)

Wow. Very nice.

---

### Post by The_Pirate_King on 2009-12-08
No need to install a virtual machine; you can edit grub to allow you to boot from your XP partition.  Chances are, GRUB is just set to immediately boot into Ubuntu without allowing you a chance to choose a different OS. 
Here's how to do that: [https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

