---
title: "booting an operating system"
date: 2010-01-10
forum: New to Ubuntu
---

### Post by vinceDUG on 2010-01-10
Hello,

PLease can any forum people help me?

My operating system needs a single feature added to it's Kernel file.

an extra line...

"pfix=ram"

How do i add this line into my kernel boot up sequence?...

The operating system is currently installed on the hard drive and does boot up.

thankyou

Vince.

---

### Post by vinceDUG on 2010-01-10
Hello there,

PLease can any forum people help me?

My operating system needs a single feature added to it's Kernel file.

an extra line...

"pfix=ram"

How do i add this line into my kernel boot up sequence?...

The operating system is currently installed on the hard drive and does boot up.

thankyou

Vince.

---

### Post by aaronp on 2010-01-10
Your post is a little vague so forgive me if this answer is completely irrelevant to your question.
To add parameters to the kernel that you are booting, on Ubuntu assuming you use grub, you need to edit the file **/boot/grub/menu.lst**

***BACK IT UP BEFORE EDITING IT***

Find the kernel line that you want to add the parameter to and then add it.
An even safer way (still back it up) would be to copy the entry into a new entry and add the parameter there. Then you can test it by choosing the 'copy' from the grub menu.

---

### Post by CharlesA on 2010-01-10
If you are using Grub2 the location of the config file would be: /boot/grub/grub.cfg. Use "update-grub" to make changes to it. See [here]("https://wiki.ubuntu.com/Grub2").

---

### Post by Captain_tux on 2010-01-10
A quick Google query of **pfix=ram** seems to indicate that it's a *Puppy Linux* parameter...

---

### Post by QLee on 2010-01-10
If you are using GRUB2 do not try to edit the grub.cfg file. Instead, edit the file /etc/default/grub, add your chosen kernel options to the line, GRUB_CMDLINE_LINUX_DEFAULT="quiet splash" (in this case, "quiet" and "splash" are kernel options. After editing that file, run update-grub and your changes will be installed to grub.cfg and stick.

---

### Post by bapoumba on 2010-01-10
Threads merged.

---

### Post by vinceDUG on 2010-01-10
Hello,

thankyou for your replies....yes it is Puppy linux.

This operating system allows you to make a "frugal" install to the HDD.

But to get the operating system to then use itself in the way it
was designed...(getting the whole os to load into "ram" from the hdd)
then you must tell the "frugal" version to do this.

This is what i was reading on the web.

Vince.

---

