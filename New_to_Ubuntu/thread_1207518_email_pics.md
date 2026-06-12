---
title: "email pics"
date: 2009-07-08
forum: New to Ubuntu
---

### Post by zenneth on 2009-07-08
how do i send large picture files by email. can i reduce the size easily or compress the file.to clarify i want to send lots of photos by email this used to easy in windows but i cant find a method. solved by fooman thank you all

---

### Post by alexlafreniere on 2009-07-08
I would suggest putting all the pictures in a .zip archive and emailing them to whoever you want. .zip's do a little compression but not too much, you don't want to compress your pictures so much they look terrible for the recipient anyway. How did you use to do it in Windows? Are you using a web based or native email application?

---

### Post by fooman on 2009-07-08
there is a nautilus extension that will allow you to resize by right-clicking and choosing resize image from the context menu.  ...it also allows for batch or multiple re-sizing.

install from synaptic...system > administration > synaptic package manager ...search for/install "nautilus-image-converter"

or just open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
sudo apt-get install nautilus-image-converter
```you may have to log-out and back in again for it to take effect.  after that,  just right-click an image to see the new option.

hope that helps.

---

### Post by Malta paul on 2009-07-08
You can split into parts and then send the smaller parts by email. Your friend can then rejoin into the original file if you also send the splitter program.

I find the java version of HjSplit works well.

[http://www.freebyte.com/hjsplit/](http://www.freebyte.com/hjsplit/)

:cool:

---

### Post by zenneth on 2009-07-08
> **fooman said:**
> there is a nautilus extension that will allow you to resize by right-clicking and choosing resize image from the context menu.  ...it also allows for batch or multiple re-sizing.

install from synaptic...system > administration > synaptic package manager ...search for/install "nautilus-image-converter"

or just open a terminal (applications > accessories > terminal) and type or copy/paste the following:

```
sudo apt-get install nautilus-image-converter
```you may have to log-out and back in again for it to take effect.  after that,  just right-click an image to see the new option.

hope that helps.
thank you it works fine

---

