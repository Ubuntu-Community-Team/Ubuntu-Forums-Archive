---
title: "how to watch a DVD in ubuntu"
date: 2009-05-17
forum: New to Ubuntu
---

### Post by Ravernomina on 2009-05-17
IM trying to watch a DVD in ubuntu 9.04 32 bit. I cannot get it to run in totem without an error saying "I do not have permission to open the file". so an assistance please. TYVM
    Ravernomina

---

### Post by taurus on 2009-05-17
Is it a movie?  You probably need libdvdcss2.

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by mjitkop on 2009-05-17
Have you already checked this page?

[https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html](https://help.ubuntu.com/9.04/musicvideophotos/C/video-dvd.html)

---

### Post by Ravernomina on 2009-05-17
that didn't work :l

---

### Post by ulfj on 2009-05-17
I know it's a dumb question,but have you installed the libdvdcss2 package?
sudo /usr/share/doc/libdvdread4/install-css.sh  It's just a thought,as when I upgraded I forgot to.


sorry not quick enough to respond!

---

### Post by Marlonsm on 2009-05-17
Open Synaptic (Inside System > Administration)

Look for the package ubuntu-restricted-extras and install it.

It (along with libdvdcss2) solved the problem for me.

You can also take a look at Totem with Xine backend (inside add/remove) and change the normal Totem for it. As it's usually better at handleing DVDs, specially the menus.

---

### Post by Ravernomina on 2009-05-17
mjitkop THANK YOU :)

---

### Post by mjitkop on 2009-05-18
I'm glad it worked for you, Ravernomina. 

Note that the other posters were saying more or less the same thing as I was. I just thought of giving you a link to the official Ubuntu help page with detailed instructions.

As a general rule, I really like the official Ubuntu help pages at help.ubuntu.com. 

Enjoy your movies. :popcorn:

---

