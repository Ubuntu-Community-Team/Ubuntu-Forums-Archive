---
title: "Reading data on Ubuntu HDD from Vista HDD"
date: 2009-03-03
forum: New to Ubuntu
---

### Post by nitroguy on 2009-03-03
So here's the deal:

I have a laptop (HP dv9000) with two hdd slots in it. I want to put 64bit ubuntu on one hard drive (the primary, 320gig one), and put in a second, 40 gig drive (cannibalized from my old computer) with Vista on it - for those programs that just won't work in wine.

But the problem comes in that my wife primarily uses the computer for picture stuff, mostly those online photo albums, so she needs to access all our pictures, which would be stored on the ubuntu HDD.

So here's my question: can I, when booted into my Vista HDD, "reach over" and read files from my Ubuntu hdd? I don't need to write, just read.

Is this possible? How?

---

### Post by taurus on 2009-03-03
Normally, windows cannot read ext2/ext3 filesystem.  However, you just need to install fs-driver in windows and you now can access your Ubuntu from windows.

[http://www.fs-driver.org/](http://www.fs-driver.org/)

---

### Post by nitroguy on 2009-03-04
That is EXACTLY what I was looking for. Thank you, Thank you, Thank you!!!

---

