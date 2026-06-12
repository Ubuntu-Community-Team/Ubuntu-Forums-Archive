---
title: "How to determine which version of Ubuntu is running"
date: 2009-06-30
forum: New to Ubuntu
---

### Post by jfl on 2009-06-30
We have several machines running different version of Ubuntu (Hardy, Intrepid and Jaunty).
My brain is not loading well today, I cannot figure a way to tell which version is running (like the "ver" command in DOS.

Thanks for any input !!!

---

### Post by tgalati4 on 2009-06-30
uname -a

cat /etc/issue

---

### Post by Sef on 2009-06-30
System > About Ubuntu


> This section is an introduction to Ubuntu. It explains the Ubuntu philosophy and roots, gives information about how to contribute to Ubuntu, and shows how to get help with Ubuntu.


        
    

[B]Thank you for your interest in Ubuntu 9.04
                - the Jaunty Jackalope - released in April 2009.[/B]
                

(bold is my doing, but it is located right under the Ubuntu logo.)

---

### Post by MrWES on 2009-06-30
> **jfl said:**
> We have several machines running different version of Ubuntu (Hardy, Intrepid and Jaunty).
My brain is not loading well today, I cannot figure a way to tell which version is running (like the "ver" command in DOS.

Thanks for any input !!!

From a terminal prompt:
```
lsb_release -a
```

~Bill

---

### Post by ~sHyLoCk~ on 2009-06-30
There are many ways of finding out. :P

```
cat /etc/apt/sources.list
```

And see if it's "jaunty" or "intrepid" or "hardy" in the sources list. But it's overkill, try the "about ubuntu" method. ;)

---

### Post by tgalati4 on 2009-06-30
cat /boot/grub/menu.lst

cat /etc/motd

In firefox Help-->About  at the bottom

Less reliable:  what live CD's you have lying around.

---

### Post by jfl on 2009-06-30
> **tgalati4 said:**
> uname -a

Works, but does not give the name.



> **Sef said:**
> System > About Ubuntu

Couldn't get it to open; just got a blank page
.


> **MrWES said:**
> From a terminal prompt:
```
lsb_release -a
```
~Bill

The best !!! Lots of details.
Thanks


> In firefox Help-->About at the bottom 
works, but need to open FF.


[SIZE="3"]And a big THANK YOU to all who took the time to reply ):P[/SIZE]

---

### Post by Crunchy the Headcrab on 2009-06-30
Also, System > System Monitor > System Tab

Shows Ubuntu version, Kernel Version, and Gnome Version.

---

### Post by jfl on 2009-07-01
> **Crunchy the Headcrab said:**
> Also, System > System Monitor > System Tab

Shows Ubuntu version, Kernel Version, and Gnome Version.

**Excellent !!!**  That's the equivalent of the Windoze "Task Manager" I have been missing.
I need to spend more time browsing, instead of just using it to work.
Thanks ...

---

### Post by margazhang on 2009-07-09
In my case, I cannot load Ubuntu on hard disk because of the "grub loading stage1.5Read error". I can, however, boot from live CD. So my question is...

How can I find out the version of Ubuntu on my hard disk after booting from live CD?

---

### Post by CatKiller on 2009-07-09
> **margazhang said:**
> How can I find out the version of Ubuntu on my hard disk after booting from live CD?

Mount your hard disk somewhere and then read what that filesystem's /etc/issue says.

---

