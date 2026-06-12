---
title: "I can't copy files from Samba shared folder"
date: 2006-11-02
forum: Networking &amp; Wireless
---

### Post by mesh2005 on 2006-11-02
I have three machines, one is Redhat 7.2 , one is Ubuntu and the third one is a Windows machine. I have a folder on the Redhat machine, it is shared and the windows machine can access it (read and write). Using the ubuntu machine I can browse the folder only but I can't copy any files from / to it.

Can you help?

Thank you

---

### Post by kidders on 2006-11-02
Is it mounted in read/write mode?

---

### Post by mesh2005 on 2006-11-08
I think it is because I can read/write using my windows machine

---

### Post by kidders on 2006-11-08
> **mesh2005 said:**
> I think it is because I can read/write using my windows machine

:confused: Isn't the share on the redhat machine?

What errors do you get when you try to copy something off the share? It's strange not to be able to do that.

---

### Post by mesh2005 on 2006-11-09
The share is on a redhat machine, I have two other machines. One of them is a Windows machine with which I can read and write to the redhat share. The other one is an Ubuntu machine, I can't write to the redhat share using it.

---

### Post by mesh2005 on 2006-11-09
I figured it out, it is very simple. I didn't supply the username and password so the linux defaulted to the current user who has no permission to write to the shared. Just I had to supply the username and password:
smb://username: password@server/path
Thank you :)

---

