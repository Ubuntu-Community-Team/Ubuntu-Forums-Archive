---
title: "Setting permissions in gedit"
date: 2010-07-14
forum: New to Ubuntu
---

### Post by Apostolique on 2010-07-14
I want to save a PHP file in /opt/lampp/htdocs/ but it says I don't have the permissions in order to do so. How would I be able to fix this?

---

### Post by MooPi on 2010-07-14
Start your process with sudo gedit.

---

### Post by Apostolique on 2010-07-14
Great, that worked perfectly.

---

### Post by da burger on 2010-07-14
Use gksudo gedit.

It's generally good practice to use gksudo instead of sudo for graphical apps.

---

### Post by aphatak on 2010-07-14
You need to start gedit as root - click on Applications -> Accessories -> Terminal;  at the command line type 'sudo gedit' and hit <enter>.  When you are asked for a password, key in the password with which you log in.  You will see the gedit window.  Edit your file, and then save it.  As root, you should be able to save it wherever you want.

---

### Post by Apostolique on 2010-07-14
> **aphatak said:**
> You need to start gedit as root - click on Applications -> Accessories -> Terminal;  at the command line type 'sudo gedit' and hit <enter>.  When you are asked for a password, key in the password with which you log in...

I wrote sudo but I wasn't asked to enter a password, gedit just started normally and I was able to save where I wanted.

---

### Post by new__buntu on 2010-07-14
> **Apostolique said:**
> I wrote sudo but I wasn't asked to enter a password, gedit just started normally and I was able to save where I wanted.

If you've verified your sudo within 15 minutes prior (that's the default, right?) it won't ask you again.

---

### Post by Apostolique on 2010-07-15
> **new__buntu said:**
> If you've verified your sudo within 15 minutes prior (that's the default, right?) it won't ask you again.

That's right, I forgot about that!

---

