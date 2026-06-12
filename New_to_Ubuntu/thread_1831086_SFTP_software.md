---
title: "SFTP software"
date: 2011-08-22
forum: New to Ubuntu
---

### Post by Dead root on 2011-08-22
Hello,

I know there are software like Filezilla to connect to my server, but they show the folders and Files in Compac view (Vertically) which is bad for me.

How can I show my files like this if I connect to my server? and what software to use? I know nautilus can do it, but I am not using GNOME and I don't want to change PCMANFM.

[IMG]http://www.almostgeek.com/wp-content/uploads/2009/11/ubuntu-home-folder-hidden-files.png[/IMG]

Thanks !

---

### Post by Toz on 2011-08-23
You can use gigolo and create an "SSH" connection to the server (it will be an sftp connection), and it will open in your file manager and you can display the icons any way you want. Just make sure that you change the file manager preference to **pcmanfm** (in gigolo) or set pcmanfm as your default file manager.

[IMG]http://i56.tinypic.com/lxjlf.png[/IMG]

---

### Post by aeiah on 2011-08-23
there's also sshfs, so you can mount it like any other partition

---

### Post by Dead root on 2011-08-23
> **aeiah said:**
> there's also sshfs, so you can mount it like any other partition
Oh Thanks it worked for me :D

Thank you Toz :) but Gigolo is not my favourite name :P

---

