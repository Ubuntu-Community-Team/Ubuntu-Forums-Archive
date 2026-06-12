---
title: "How do I chose another kernel?"
date: 2009-05-11
forum: New to Ubuntu
---

### Post by VitaminBB on 2009-05-11
So I just did an update to my earlier upgrade and I notice the kernel was updated from **2.6.28.11** to** 2.6.28.12** 

When it asked me if it wanted to overwrite my grub menu list I said keep the original one ...

Now how in the world do I get it to recognize the newest kernel I installed? 

I did a uname -r and it says i loaded **2.6.28.11**

Here is what the 9.04 part says in my menu.lst

> title** 		Ubuntu 9.04, kernel 2.6.28-12-generic**
root 		**(hd0,0)**
kernel 		**/boot/vmlinuz-2.6.28-11-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a **
initrd 		**/boot/initrd.img-2.6.24-21-generic**
quiet

How do I change this to the latest 2.6.28.12 kernel?

Help :)

---

### Post by logos34 on 2009-05-11
you want 

> title Ubuntu 9.04, kernel 2.6.28-12-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.28-[COLOR="Red"]12[/COLOR]-generic root=UUID=5fe272ba-42a7-447c-b5dd-34a79107f04a
initrd /boot/initrd.img-2.6.24-[COLOR="Red"]12[/COLOR]-generic
quiet

---

### Post by VitaminBB on 2009-05-11
Thanks, that did it.

Thats what I assumed but didnt want to screw it up, figured the UUID might be different or something ...

Thanks!

Hey how come theres no more "thank" function on this forum? I could have sworn there was one here ...

---

### Post by logos34 on 2009-05-11
It's a mystery why they removed the 'thank you' option...

The partition UUID doesn't change unless you format it.

enjoy ubuntu

---

