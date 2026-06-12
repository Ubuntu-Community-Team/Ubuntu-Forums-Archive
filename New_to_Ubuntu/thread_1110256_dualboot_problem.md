---
title: "dualboot problem"
date: 2009-03-29
forum: New to Ubuntu
---

### Post by zxy on 2009-03-29
Whenever I start my laptop up it let's me choose ubuntu or vista...

my ubuntu has an error so I cant use it so I go to vista. 

I don't really starting my laptop up and choosing ubuntu/vista since it annoys me and need to know how to get rid of it.

I have everything of ubuntu removed from add/remove and whenever i try to repaid using the vista repair cd but it doesnt solve the problem. I tried doing that fixmbr thingie but it didnt work either, someone told me to run bootfix... but I don't know where to run it from...when i go to my repair section x:\ comes up. When i start vista up normally and run c:\ bootfix it says file not found.

Someone  told me it was a grub problem but told me to remove wubi and it would go away but I already removed wubi  but it's still there..

Please help me get rid of this annoying option...

[IMG]http://i8.photobucket.com/albums/a9/mppaki/P3230211.jpg[/IMG]

just want to get rid of the ubuntu option and let my laptop turn on automatically to vista... I will still retry ubuntu but not at the moment for now...

---

### Post by yeats on 2009-03-29
This is what you need:

[https://wiki.ubuntu.com/WubiGuide#Uninstallation]("https://wiki.ubuntu.com/WubiGuide#Uninstallation")

---

### Post by zxy on 2009-03-29
That's the thing wubi is already removed from my laptop and the error still comes up


i cant even find a ubuntu folder when i go into c:\


heres the error that comes up when i try ubuntu.

File: \ubuntu\winboot\wubildr.mbr

---

### Post by zxy on 2009-03-29
also the status is 0xc0000000f

---

### Post by mrsteveman1 on 2009-03-29
On vista that boot menu is controlled by the BCD store, you will need a program such as VistaBoot Pro or EasyBCD to alter it and remove the ubuntu entry.

---

### Post by bytan on 2009-03-29
edit...

---

### Post by zxy on 2009-03-29
> **mrsteveman1 said:**
> On vista that boot menu is controlled by the BCD store, you will need a program such as VistaBoot Pro or EasyBCD to alter it and remove the ubuntu entry.

Thanks alot mrsteveman1, that was perfect, i downloaded easybcd since it was free ^.^ and it let me remove the ubuntu option :D

---

