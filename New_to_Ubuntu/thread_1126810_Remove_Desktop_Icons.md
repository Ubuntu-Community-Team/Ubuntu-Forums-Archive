---
title: "Remove Desktop Icons?"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by GaryPG2 on 2009-04-15
The upper left corner of my desktop has icons for a USB flash drive, a USB hard drive and my Windows Vista partition (labeled Hard Drive). I would rather not have those icons there, but I have not found a way to delete them. I still would like to access these drives from the Places menu so I do not want to unmount them.

Can anyone tell me why the icons are there and how to remove them?

---

### Post by LostMagix on 2009-04-15
hit Alt+F2

put in 

gconf-editor

go to

apps\nautilus\desktop

untick 

"volumes_visible"

---

### Post by GaryPG2 on 2009-04-15
This is first time that I have seen the Configuration Editor! This solves the problem. Thanks!

---

