---
title: "Can't use synaptic"
date: 2009-01-15
forum: New to Ubuntu
---

### Post by mamamia88 on 2009-01-15
i tried to install moblock but it won't go past the install screen.  now whenever i try to go into synaptic all i get is an error saying E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i then run it but i still get the installer but it won't advance.  this is a really big problem since i can't use synaptic until i get it sorted it out please help me out

---

### Post by lovelyvik293 on 2009-01-15
You have to use the 
```

dpkg --configure -a

```
in terminal to solve this problem.

---

### Post by 3humps on 2009-01-15
> **mamamia88 said:**
> i tried to install moblock but it won't go past the install screen.  now whenever i try to go into synaptic all i get is an error saying E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

i then run it but i still get the installer but it won't advance.  this is a really big problem since i can't use synaptic until i get it sorted it out please help me out

thats weird, i get the same when i tried a usb pendrive version of Ubuntu, i just assumed it was because i was using a pendrive vesion not a regular version...i wait with bated breath to here some technical response...sorry i couldn't offer one but if it's any comfort your not alone!
colin.

---

### Post by mamamia88 on 2009-01-15
weird i tried that about 5 times and it would freeze during install each time but this time it worked right away.

---

### Post by avtolle on 2009-01-15
You have run ```
sudo dpkg --configure -a
```right? Try it again, and post any messages returned in the terminal.

---

### Post by mamamia88 on 2009-01-15
thats exactly what i did thanks

---

### Post by Slug71 on 2009-01-15
Try installing Packagekit and see if that works.

Make sure you get packagekit-gnome and Packagekit-backend-apt too.

---

### Post by jre on 2009-01-17
On your original problem, just quoting [https://help.ubuntu.com/community/MoBlock:](https://help.ubuntu.com/community/MoBlock:)

```
[B]I tried to install MoBlock but I'm stuck on a
screen with a Moblock warning
[/B]
This is a so called "debconf" question. Read the text and
confirm by pressing "OK". If your debconf interface doesn't
support your mouse, then you have to use your keyboard: hit
the "TAB" key until "OK" is highlighted and then press
"RETURN".

You may also do a "sudo dpkg-reconfigure debconf" and select
 "Gnome" as your interface. Then you can use your mouse for
 debconf questions.
```

---

