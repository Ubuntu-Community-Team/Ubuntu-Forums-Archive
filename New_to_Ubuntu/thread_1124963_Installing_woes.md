---
title: "Installing woes"
date: 2009-04-13
forum: New to Ubuntu
---

### Post by SpenceMakesSense on 2009-04-13
After formatting my hard drive I'm having problems installing.

I had a 400 gb hd and I have 300 gb for /home, 10 gb for /, 4 gb for swap and the rest for windows. When I go to install it says ubiquity has crashed and when running from terminal all I get is the following out put

```
ubuntu@ubuntu:~$ ubiquity
/usr/share/themes/Human/gtk-2.0/gtkrc:82: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.
/usr/share/themes/Human/gtk-2.0/gtkrc:83: Murrine configuration option "lightborder_ratio" will be deprecated in future releases. Please use "lightborder_shade" instead.
/usr/share/themes/Human/gtk-2.0/gtkrc:194: Murrine configuration option "highlight_ratio" will be deprecated in future releases. Please use "highlight_shade" instead.

```

Any help? I've tried from an 8.10 disc and 9.04 disc

---

### Post by juancarlospaco on 2009-04-13
This is a Warning, doesnt matter, try :

**ubiquity --verbose**
or
**ubiquity --debug**

---

### Post by SpenceMakesSense on 2009-04-13
same output happened with debug and verbose didnt work at all.

Any help?

---

### Post by SpenceMakesSense on 2009-04-14
bump

---

### Post by halitech on 2009-04-14
have you tried using the alt install cd instead of the live cd?

---

### Post by SpenceMakesSense on 2009-04-14
*face palm
Ya I guess I should try that. >.>

---

### Post by SpenceMakesSense on 2009-04-15
yep, worked. Thanks! I wonder what was going wrong with  the live CD:-k

---

### Post by halitech on 2009-04-15
what kind of video card do you have? Maybe it was an issue with video drivers

---

