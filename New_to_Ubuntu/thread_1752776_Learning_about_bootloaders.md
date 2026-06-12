---
title: "Learning about bootloaders"
date: 2011-05-08
forum: New to Ubuntu
---

### Post by rockinruler on 2011-05-08
Hello,

I just installed Ubuntu 10.04LTS to dual boot with my Windows 7 laptop the other day.

I've used earlier versions on my desktop before and had issues with the bootloader after updating.
So I was wondering is anyone knew a good link or any other resource to learn a few essential things about bootloaders and dual-booting and how they work.

Also, this is just something that I wanted to know, how do I see if I have GRUB or GRUB2 installed?

Thanks for looking, have a great day :)

---

### Post by jramshu on 2011-05-08
```
grub-install -v
```GRUB 2 should display a version number of 1.96 or later. Legacy GRUB is version 0.97.

EDIT: This command goes in a terminal window. ctrl+alt+t will open a terminal.

EDIT 2: Forgot to give the link.

[https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

---

### Post by Rubi1200 on 2011-05-08
> So I was wondering is anyone knew a good link or any other resource to  learn a few essential things about bootloaders and dual-booting and how  they work.
Pictures worth a thousand words here:
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

Talks about both Windows and Linux bootloaders.

Hope this answers your question.

---

### Post by rockinruler on 2011-05-08
@jramshu

Thanks :-)
It shows me this

```
The program 'grub' is currently not installed.  You can install it by typing:
sudo apt-get install grub

```

And thank you for the link too.


@Rubi1200
Thanks a ton! The link seems to be pretty good :-)

---

