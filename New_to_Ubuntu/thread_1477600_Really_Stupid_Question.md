---
title: "Really Stupid Question"
date: 2010-05-08
forum: New to Ubuntu
---

### Post by houcker on 2010-05-08
first day using Ubuntu:
I am trying to add a background picture on the GRUB screen, everything is working fine, but it wont let me copy my picture into the folder i need because I do not have permission, only the owner does, who is "Root". How do i get the picture into there?
Location of picture: storage/pictures/ubuntu.png
where i need it: boot/grub

---

### Post by sandyd on 2010-05-08
> **houcker said:**
> first day using Ubuntu:
I am trying to add a background picture on the GRUB screen, everything is working fine, but it wont let me copy my picture into the folder i need because I do not have permission, only the owner does, who is "Root". How do i get the picture into there?
Location of picture: storage/pictures/ubuntu.png
where i need it: boot/grub
```

gksudo nautilus
```

navigate to /boot/grub

now, drag and drop onto the nautilus window.

---

### Post by suryaccnamcse on 2010-05-08
this link will help you out
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Mitchell Hale on 2010-05-09
I have [Ubuntu Tweak]("http://ubuntu-tweak.com/") installed.

There's an option to manage nautilus scripts. Enable the "browse as root" (or something like that, forgot the phrasing) script. 

Right click the folder, go to "scripts > browse as root".

---

### Post by romeug on 2010-05-09
really stupid questions may be made much smarter and relevant to a greater number of people if the title of your question reflects the subject matter.
Your question was not stupid at all...

---

