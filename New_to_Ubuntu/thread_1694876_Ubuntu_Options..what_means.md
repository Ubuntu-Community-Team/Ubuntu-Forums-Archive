---
title: "Ubuntu Options..what means?"
date: 2011-02-25
forum: New to Ubuntu
---

### Post by mohammedadel on 2011-02-25
[FONT=Georgia][SIZE=3][B][FONT=Arial][SIZE=2]I got an Ubuntu CD 9.10 with my laptop Dell inspiron n5010 core i3.. I upgrade it to 10.04LTS...Some Drivers stopped working.. but I found these drivers worked when I choose the " Option 3 " Please, Can you tell me what's the difference between these options for Ubuntu?

Note: That's my first time to use Ubuntu..

- If there any forums, site or anything learning me how to use Ubuntu...please submit it

See this Image (I took it with my cam):[/SIZE][/FONT]   
[IMG]http://www.freeimagehosting.net/uploads/82fc7e4d0d.jpg[/IMG][/B][/SIZE][/FONT]

---

### Post by NightwishFan on 2011-02-25
PAE is a kernel designed to use extra security features of a cpu and the ability for 32-bit to see more than 3gb of ram (or so).

If you have less than 4gb of ram, use the regular kernel and not PAE.

---

### Post by trinux_bc on 2011-02-25
since you know which kernel to boot with you can remove extra grub menu entries using this guide:

[http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/](http://www.howtogeek.com/howto/17787/clean-up-the-new-ubuntu-grub2-boot-menu/)

trinux_bc

---

### Post by grahammechanical on 2011-02-25
Oh, by the way, have you noticed that you are the only person in this thread using large letters in bold type? We do not do that. It is like shouting at someone.

The core part of the Linux operating system is called the kernel. It is being developed and improved all the time. It is not a finished product. You notice on your menu the words, Linux 2.6.31-18 and 2.6.31-28. These are different editions of the Linux kernel.

When a new edition is released Update Manager will install it for you. You will see another line at the top of the menu. The other lines are not removed because you may have problems running the very latest kernel. (not always but sometimes. I have never had a problem). But if you do have a problem, then you can choose to use the old kernel and get a working system.

Regards.

P.S. On the Ubuntu forums there is a section with tutorials.

---

### Post by mohammedadel on 2011-02-25
Thanks NightwishFan & trinux_b

@grahammechanical: Sorry for using large fonts and thanks :)

---

