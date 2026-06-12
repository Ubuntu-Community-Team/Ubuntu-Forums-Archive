---
title: "Setting startup O/S as xp instead of linux"
date: 2006-09-13
forum: Networking &amp; Wireless
---

### Post by Phill Marley on 2006-09-13
Hello 
I am an absolute newbie to linux and have a question.
I am dual booting with win xp, but when I turn on the machine I want the default os to be windows (as the rest of my family need access). on reading up this issue I thought that to set the default os you had to go to /boot/grub and amend the menu.lst file, inserting 

default = #  (wherever the os is in your list)

when I try to save this it will not let me 

what is going on ? do I need to reset permissions, if so how?

I used unix many years ago so I know a few basics

---

### Post by sas01 on 2006-09-13
You need to have root access to change those files as regular users don't have the correct permissions. Just login as root and you can do it.

---

### Post by Phill Marley on 2006-09-13
when I set up the system i was not asked to set up a su account, I thought that the creator  had full access and permissions.

---

