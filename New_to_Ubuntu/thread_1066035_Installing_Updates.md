---
title: "Installing Updates"
date: 2009-02-10
forum: New to Ubuntu
---

### Post by daviddrys on 2009-02-10
I just installed Ubuntu and did an update, found 265 updates.  I try to install them but I get the following:

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I go into the terminal and type in the dpkg..... but it comes back and tells me the requested operation requires a superuser privilege.  How do I install these updates?

---

### Post by Temposs on 2009-02-10
you need to type:

```
sudo dpkg --configure -a
```

That('sudo') gives you superuser privelege. You can put it before any command that needs superuser privelege.

---

### Post by avtolle on 2009-02-10
If that ```
sudo dpkg --configure -a
```kicks out additional error messages, post them here. Otherwise, after issuing that command, and while still in the terminal, do```
sudo apt-get update
sudo apt-get upgrade
```to (hoepfully) finish the updates.

---

### Post by daviddrys on 2009-02-10
I am getting a whole bunch of other errors now, they are talking about not enough space.  Could this be because I am running off a CD?

---

### Post by avtolle on 2009-02-10
Yes, that is your problem. You must be running on Live CD, which is in the RAM only, and unless you have a very large supply of RAM installed, you will be running out of room (and the updates will be lost once you restart your computer or try to install on the HDD; you are not making any changes to the iso burned on the CD).

---

### Post by daviddrys on 2009-02-10
Ok, thanks.  Can I install ubuntu on the hard drive and still have windows so I can use programs not supported by ubuntu?

---

### Post by Temposs on 2009-02-10
If you are indeed running Ubuntu off of a CD, then you haven't installed Ubuntu at all. 

If you want to use Ubuntu and install all the stuff you want and use it like a regular system, you'll need to install it onto your hard drive.

---

### Post by Temposs on 2009-02-10
> **daviddrys said:**
> Ok, thanks.  Can I install ubuntu on the hard drive and still have windows so I can use programs not supported by ubuntu?

You can indeed install Ubuntu and still have Windows. It's called dual-booting.

Here is a guide to doing what you want to do: [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by daviddrys on 2009-02-10
Thanks for all your help, I got it installed and updated.  Now I am trying to log into my school's web site but I don't have all the Java plug ins I need.  The first time I went they show me a list of stuff to download but I only downloaded the first file and then closed the box with the other two links.  How do I get those links back?

---

