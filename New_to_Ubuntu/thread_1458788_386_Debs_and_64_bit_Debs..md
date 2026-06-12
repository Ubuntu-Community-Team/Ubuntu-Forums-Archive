---
title: "386 Debs and 64 bit Debs."
date: 2010-04-20
forum: New to Ubuntu
---

### Post by chrispche on 2010-04-20
Is it possible to convert an i386 deb file into a 64 bit one to use?

Thanks in advance.

---

### Post by LowSky on 2010-04-20
no not exactly but you can force install a 32bit app onto a 64bit machine

---

### Post by Paddy Landau on 2010-04-20
> **LowSky said:**
> you can force install a 32bit app onto a 64bit machine
Will the 32-bit program work? Will force-installing break dependencies? TIA

---

### Post by nothingspecial on 2010-04-20
What you need is getlibs, you can download a deb from [[COLOR="Magenta"]here[/COLOR]]("http://frozenfox.freehostia.com/cappy/").

Then install the 386 deb with this syntax
```

sudo dpkg -i --force-all deb_you_want_to _install.deb
```

Then find where the binary has installed to, usually /usr/bin, but not always - use locate or whereis or find etc, etc, etc

Assuming it is in /usr/bin

```
getlibs /usr/bin/deb_you_have_just_installed
```

This is not garunteed but it has worked for me in the past.

---

### Post by Paddy Landau on 2010-04-20
Interesting, thank you.

So, because you use dpkg, does that mean dependencies aren't broken? Or would upgrades have to be manual?

---

### Post by nothingspecial on 2010-04-20
It is a script that downloads the libraries needed for 32 bit apps for 64 bit programs.

I first used it ages ago for skype I think and more recently for the amazon mp3 downloader - useful.

---

### Post by chrispche on 2010-04-21
Thanks all.

---

