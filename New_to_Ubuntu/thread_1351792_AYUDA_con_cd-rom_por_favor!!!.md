---
title: "AYUDA con cd-rom por favor!!!"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by lrcaballero on 2009-12-10
Que tal Ubunteros!!!

estoy corriendo Jaunty 9.04, en una Acer Timeline 4810TZ-4694 Intel Duo , GMA 4500 MHD, 3GB de Ram y 320 de HDD.

Antes cuando metia un cd al cd-rom lo reconocia y podia extraer la informacion que buscaba y a la par aparicia en el desktop, ahora cuando meto un disco al ce-rom no aparece!!!!??###, pero si reinicio la computadora entonces y solo entonces si aparece el disco en el desktop. Alguien me puede ayudar para configurar el dc-rom para que vuelva areconocer los cd's normalmente!

Gracias,

Luis

---

### Post by Geoff918 on 2009-12-10
Well, I've experienced the same thing with HDD partitions.

Have you tried going to "Places" and selecting the CD-ROM?

Do you need the CD Image to appear on the Desktop? I agree it would be nice to have consistent performance here. But, perhaps this is a general bug in the GNOME desktop?

You should be able to access it one way or another. Worse case scenario, you end up going to the CLI and

cd to /mnt/cdrom (or cdrom0...whatever the case may be).

Hope this may help...

---

### Post by lrcaballero on 2009-12-10
Gracias Geoff918!!! pero esto no me ayudo, alguien mas que me pueda ayudar????? hay aguna manera en el Terminal para hacer que el cd-rom recosnosca los cd's???

Luis

---

### Post by Geoff918 on 2009-12-11
Oi! Comprendo.

Is your CD drive physically still okay? Is the light coming on when you insert the CD? Do you have a dual boot in which you can try to access the device from Windows?

Does the BIOS recognize the CD drive on boot?

I once had a system that was having similar problems. It turns out that somehow the power cable on the back of the drive had come slightly loose. It would sometimes work and sometimes not just on the whim of whether or not the cable was in the right position. Apparently at the factory they hadn't secured it well enough.

So, I guess I'm trying to think whether the problem is even software or if perhaps it's hardware related...

---

