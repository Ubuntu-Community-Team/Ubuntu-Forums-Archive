---
title: "flash plugin 10"
date: 2009-11-29
forum: New to Ubuntu
---

### Post by garage jack on 2009-11-29
hi guys. now i'm going to ask a question wiich, i' pretty sure millions of people asked before. and why do i ask? because nothing seems to help me with this problem.
how to install flash plugin 10 on ubuntu 9.10? sounds familiar? but guess what, everything works fine, except firefox, which seems not to recognize it (about:plugins -nope, no flash plugin 10) but when i check synaptic package manager it says flash plugin 10 is installed. i m sure there are ways to fix this, but since i 'm beginner, i need your help. thanks in advance

---

### Post by garage jack on 2009-11-29
one more thing, when i type about:plugins in mozilla it shows that flash plugin 9 is installed. can i disable it and install flash plugin 10 on its place and how?

---

### Post by pbrane on 2009-11-29
I installed Flash 10 64-bit version on my machine like this:

1. downloaded flash 10 (.tar.gz) from adobe.com
2. created a plugins directory in ~/.mozilla
3. unzipped libflashplayer.so from the downloaded file
4. copied libflashplayer.so to ~./mozilla/plugins
5. restart firefox

if you want system-wide use of flash copy libflashplayer.so to
**/usr/lib/mozilla/plugins** 
as root

---

### Post by garage jack on 2009-11-29
didn't help, sorry. i did the first part and then i tried to start youtube, but the same audio and video problems remained. i typed about:plugins in mozilla again and this is what it says 
File name:  libswfdecmozilla.so Shockwave Flash 9.0 r999i tried  to copy libflashplayer.so to .usr/lib/mozilla/plugins  but it said** access denied **

---

### Post by garage jack on 2009-11-29
ok, i solved it now. all i needed to do is to uninstall swfdec from synaptic package manager and now flash 10 is working on my mozilla. thanks

---

### Post by laidback on 2009-11-29
You might find it worth removing Gnash as well.

---

### Post by garage jack on 2009-11-29
> You might find it worth removing Gnash as well.

i didn't have gnash installed, but thank you any way.

---

### Post by meborc on 2009-11-29
what you need to install in ubuntu-restricted-extras package, that will give you much more than flash ;)

read - [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by garage jack on 2009-11-30
> what you need to install in ubuntu-restricted-extras package, that will give you much more than flash
it's all there already, but thanks. :)

---

