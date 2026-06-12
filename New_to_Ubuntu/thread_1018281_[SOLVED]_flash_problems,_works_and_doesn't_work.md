---
title: "[SOLVED] flash problems, works and doesn't work"
date: 2008-12-21
forum: New to Ubuntu
---

### Post by saxonjf on 2008-12-21
For some reason Flash works fine in Opera, but I cannot get it to work it at all in Firefox, Epiphany (webkit), Arora, etc.

I like Opera, but not as much as firefox, so I was hoping someone would help me out.

I have installed every version of flash and gnash I can find.  and nothing seems to work.

Java seems to work properly in Opera, as I can view web pages properly in it while Firefox, et al., won't perform java scripts.  Any help in this area would be most appreciated.

---

### Post by pdtpatrick on 2008-12-21
You have to make sure you installing the flash plugins under the right folder.. check under your /home directory and there should be a hidden file called .mozilla

Also if you go to adobe's website and download the .deb file, you should be able to install it using dpkg. You can also make sure that firefox isnt running before you install it.

---

### Post by SunnyRabbiera on 2008-12-21
strange, can you give us details on your processor?
Version?
I know there are (or were) troubles with flash and java on 64bit systems.

---

### Post by saxonjf on 2008-12-22
AMD Athlon 1600+ i686 processor, running Intrepid.  FOr the first time, I liked the last version better than the new one.

I didn't see anything under the .mozilla folder in my home folder, but it is recognized in the plugins box under firefox.

If I were to use .dkpg, how would I go about doing that?

---

### Post by jamesstansell on 2008-12-23
Try installing the ubuntu-restricted-extras package.

Also, you said you have an AMD processor, but I don't know off-hand if it is 64-bit capable.  If you _are_ running a 64-bit version of ubuntu you should probably check out the sticky threads in the 64-bit forum.

---

### Post by saxonjf on 2008-12-23
Like I said it's i686.  and I already have installed ubuntu-restricted-extras.

---

### Post by RomeReactor on 2008-12-23
Hi. Try removing Gnash, as it causes conflicts with Flash:
```
sudo aptitude remove gnash gnash-common mozilla-plugin-gnash
```

---

### Post by saxonjf on 2008-12-24
Thanks Rome, that took care of it.  Now, Firefox works with Flash just fine now.  Officially thanked.

---

