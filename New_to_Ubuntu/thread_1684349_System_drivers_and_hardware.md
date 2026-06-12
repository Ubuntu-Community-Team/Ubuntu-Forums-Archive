---
title: "System drivers and hardware"
date: 2011-02-09
forum: New to Ubuntu
---

### Post by Velinsky on 2011-02-09
Hi again :)
Where can I see my installed hardware and devices and to add or remove drivers? I've been looking all around in Administration and Preferences but I can't find it.
I've got another question: the default text editor (Gedit ) doesn't open correctly documents written in cyrilic under WinXP. How can I change the encoding of the document?

Thanks a lot in advance :)

---

### Post by taseedorf on 2011-02-09
you can use lspci to see devices, however, things are different in linux....you must compile drivers yourself or use system/administration additional drivers.

What drivers do you need? For which devices?

Gedit probably won't display properly.... try open office.

---

### Post by Velinsky on 2011-02-09
I just want to see my devices listed but unfortunately I think it's impossible to view them as they're in Device Manager in WinXP.

---

### Post by cascade9 on 2011-02-09
Its impossible to view them exactly as you can in XP, but you can get pretty close. 

sudo apt-get install lshw-gtk 

By the way, that is just  aGUI for lshw, you can view the same information in the termial- 

sudo lshw

---

### Post by Velinsky on 2011-02-09
Thanks, that worked pretty fine :)

---

