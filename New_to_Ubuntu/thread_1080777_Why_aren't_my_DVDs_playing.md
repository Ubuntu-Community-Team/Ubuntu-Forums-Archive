---
title: "Why aren't my DVDs playing?"
date: 2009-02-25
forum: New to Ubuntu
---

### Post by Carolynhilton on 2009-02-25
This seems like a simple enough question, but nonetheless, I can't answer it. 
When I opened up a DVD in Ubuntu Movie Player, it played the federal disclaimer and then my computer froze up entirely. Of course, I've tried others (VLC, Gnome MPlayer, MPlayer Movie Player) and they're no help either. MPlayer attempted to play it but then a dialogue box opened with something along the lines of "Could not read. Too many files." 
This has happened with more than one DVD.


Any thoughts?
Thanks!

p.s. I admit that I am *very* new, so try to explain as if I was born yesterday.

---

### Post by ulfj on 2009-02-25
I have the same problem! Give us some insite folks.

---

### Post by MockY on 2009-02-25
[http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux](http://www.debuntu.org/how-to-play-dvd-under-ubuntu-linux)

---

### Post by philinux on 2009-02-25
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

And click the medibuntu link below.

---

### Post by regonzal on 2009-02-25
Thank you for the link Philinux. 

A question: 

Is there a difference in the codecs provided by the ubuntu-restricted-extras package in synaptic and the ones in medibuntu?

---

### Post by philinux on 2009-02-25
> **regonzal said:**
> Thank you for the link Philinux. 

A question: 

Is there a difference in the codecs provided by the ubuntu-restricted-extras package in synaptic and the ones in medibuntu?

Yes, libdvdcss2 is only available from the medibuntu repo.

---

### Post by theozzlives on 2009-02-25
> **philinux said:**
> Yes, libdvdcss2 is only available from the medibuntu repo.

libdvdread3 has the libdvdcss2 in it

---

### Post by philinux on 2009-02-25
> **theozzlives said:**
> libdvdread3 has the libdvdcss2 in it

So is libdvdcss2 redundant?

---

### Post by presence1960 on 2009-02-25
[http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html](http://www.dailygyan.com/2008/11/10-things-you-should-do-immediately.html)

Note: the open office part disregard it doesn't work. But for the DVDs part it is a go. I use 1,2 &3 on that list.

---

### Post by mc4man on 2009-02-25
> So is libdvdcss2 redundant?

libdvdcss2 isn't part of libdvdread3, just a shell script to install it. In the past it retrieved an old version from chalmers blah, blah, now it gets it directly from medibuntu without the need to add medibuntu as a repo.

This command will always cause libdvdcss2 to be installed on 32 bit installs

```
sudo apt-get install libdvdread3 && sudo /usr/share/doc/libdvdread3/install-css.sh
```

---

### Post by ulfj on 2009-02-26
I ran libdvdcss and dvd's started playing,then I got a error icon come up in toolbar at the top of my screen when I rightclick on it this comes up, 

E dpkg was interuped must manually run 'dpkg --configure -a' to correct

when I do this it tells me I must be a superuser to continue,what does this mean and how do I fix it?

---

### Post by philinux on 2009-02-26
run it like this


```
sudo dpkg --configure -a
```

Info.
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by ulfj on 2009-02-26
Ok I'll give that a go!

---

### Post by ulfj on 2009-02-26
Grrrrrrrrr no that didn't do it. will give it a go later. need to get some work done now.

---

