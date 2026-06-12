---
title: "additional hard drive for storage 2.0"
date: 2011-09-04
forum: New to Ubuntu
---

### Post by hookitup on 2011-09-04
This thread is in regards to [THIS ONE]("http://ubuntuforums.org/showthread.php?t=1838459") now that my computer recognizes the additional HD when i move files to it, it copies them to it instead of moving them like i would like it to do.

any idea where i went wrong ,,, i used [this guide]("http://tuxtweaks.com/2008/11/how-to-add-a-new-hard-drive-in-ubuntu/") to help me to get the hard drive to be able to be recognized and mounted .

Thanks for the help,

---

### Post by cavh on 2011-09-04
How are you copying the files across - using the graphical file manager or via the command line? If using the command line, use the *mv* command, not the *cp* command - do a search on [http://manpages.ubuntu.com/]("http://manpages.ubuntu.com/") if unsure as to what these commands do.

---

### Post by hookitup on 2011-09-04
i was just dragging and dropping the files . and it copied it which i dont want. , i basically want this hard drive to act like its just more space and not like an external HD or usb jump drive where in that case you would want to copy for the most part.

---

### Post by cavh on 2011-09-05
Maybe nautilus-add provides you a way to do this:

[http://www.makeuseof.com/tag/add-custom-functionality-to-nautilus-linux/]("http://www.makeuseof.com/tag/add-custom-functionality-to-nautilus-linux/")

Haven't used it myself.

---

### Post by hookitup on 2011-09-05
is there a way to format the HD to act as an extension of the other .... ?

---

### Post by cavh on 2011-09-05
Not that I am aware of. In effect, you are asking to have a single partition over two physical devices. Others more knowledgeable may correct me, but I don't think it's possible unless you have a RAID set up.

---

### Post by hookitup on 2011-09-06
yeah i get what your sayin now.... its just cause i have a bunch of .iso and .avi files id likes to move over to it but it would take for ever to do cause it would copy them ....

---

### Post by Wim Sturkenboom on 2011-09-06
As far as I know there is no way to achieve what you want; simply because it's not on the same disk so it needs to be copied / moved physically.

---

