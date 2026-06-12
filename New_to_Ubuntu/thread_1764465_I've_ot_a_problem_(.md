---
title: "I've ot a problem :("
date: 2011-05-21
forum: New to Ubuntu
---

### Post by josh11 on 2011-05-21
First of all, I have Windows XP and Ubuntu installed on a dual-boot system.

Tonight, I got a B.S.O.D. from Windows XP (SP3), rendering it useless. I think it's a virus that caused it.

Anyway, usually that aint a problem as I do not need any files. So I would just re-install the OS.

So I popped the XP disc in, hit ESC. It took me to the boot menu. I selected "boot from disk" and it progressed from there. Then GRUB came up and asked what OS I would like to use, so I selected windows XP.

Then it just booted normally, until I am again confronted with a B.S.O.D. 

I can still use ubuntu though, and was wondering if anyone knows what to do, or has came across this before. And also does any body know how to wipe a hard drive from ubuntu as I have only been using a few months.

Thank you very much in advance.

---

### Post by Thewhistlingwind on 2011-05-21
To wipe windows? Gparted will help you with this task. However, I think theres extra stuff you have to do to get the OS reinstalled afterwards, like setting boot flags.

EDIT: Also, reinstalling windows will mean that win will install the windows bootloader over GRUB.
EDIT2: It also might want the whole drive to itself.

---

### Post by josh11 on 2011-05-21
I mean to just wipe the whole thing and to start again :(

---

### Post by oldfred on 2011-05-21
Are you sure you set boot from CD not hard drive as first in boot order?

It seems like it booted the hard drive again.

---

### Post by josh11 on 2011-05-21
Yup. Unfortunately, I am sure :( I've never encountered any problem like this before I started using a dual-boot system :(

---

### Post by soapytheclown on 2011-05-21
> **josh11 said:**
> 
So I popped the XP disc in, hit ESC. It took me to the boot menu. I selected "boot from disk" and it progressed from there. Then GRUB came up and asked what OS I would like to use, so I selected windows XP.


Describe what happened here EXACTLY. What did you see on the screen? Did you get any kind of blue screen installer? Anything that remotely seemed like you were choosing to install anything? 

From the sounds of it none of this happened leaving us to believe that it didnt actually boot off the Windows Install CD or the CD is broken.

After you have installed Windows you wont have anything to do with GRUB as it writes over your MBR. Your machine will Auto Boot to Windows (but GRUB can be easily restored after)

---

### Post by wildmanne39 on 2011-05-21
> **josh11 said:**
> First of all, I have Windows XP and Ubuntu installed on a dual-boot system.

Tonight, I got a B.S.O.D. from Windows XP (SP3), rendering it useless. I think it's a virus that caused it.

Anyway, usually that aint a problem as I do not need any files. So I would just re-install the OS.

So I popped the XP disc in, hit ESC. It took me to the boot menu. I selected "boot from disk" and it progressed from there. Then GRUB came up and asked what OS I would like to use, so I selected windows XP.

Then it just booted normally, until I am again confronted with a B.S.O.D. 

I can still use ubuntu though, and was wondering if anyone knows what to do, or has came across this before. And also does any body know how to wipe a hard drive from ubuntu as I have only been using a few months.

Thank you very much in advance.
Hi, when or if you decide to wipe the hard drive this will answer your questions.:D
[http://members.iinet.net.au/~herman546/p18.html](http://members.iinet.net.au/~herman546/p18.html)

---

### Post by josh11 on 2011-05-22
> **soapytheclown said:**
> Describe what happened here EXACTLY. What did you see on the screen? Did you get any kind of blue screen installer? Anything that remotely seemed like you were choosing to install anything? 

From the sounds of it none of this happened leaving us to believe that it didnt actually boot off the Windows Install CD or the CD is broken.

After you have installed Windows you wont have anything to do with GRUB as it writes over your MBR. Your machine will Auto Boot to Windows (but GRUB can be easily restored after)

Nope. No blue-screen installer.

---

