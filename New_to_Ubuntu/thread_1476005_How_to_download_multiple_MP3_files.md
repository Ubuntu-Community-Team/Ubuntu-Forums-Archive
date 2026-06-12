---
title: "How to download multiple MP3 files"
date: 2010-05-07
forum: New to Ubuntu
---

### Post by cforput on 2010-05-07
There is a web site [www.gutenberg.org](www.gutenberg.org) that has fully LEGAL e-books and audio books you can download. My problem is that the audio books are broken up into multiple MP3 files and I don't want to sit and download a bunch of files. If you go here:   [http://www.gutenberg.org/files/26219/mp3/](http://www.gutenberg.org/files/26219/mp3/)

You will see that there are 27 MP3 files for this book. I have tried using some download manager programs such as GWget or MultiGet but I'm not sure if they are the right thing to use. I also tried FileZilla but can't get connected to the site.

Can someone give me help here. What program to use and how to use the program. I found that the documentation for MultiGet didn't help.

---

### Post by YuiDaoren on 2010-05-07
If you use firefox, the DownThemAll add-on does a fab job.

---

### Post by cforput on 2010-05-07
I tried Download Them All as well but couldn't figure it out. Could you send me some directions?

---

### Post by kwacka on 2010-05-07
See: [An exaustive guide on how to use dTa.]("http://www.downthemall.net/howto/help/")

---

### Post by nothingspecial on 2010-05-07
Or


```
wget -r -l1 -A.mp3 http://address/of/ebook/page 
```

wget is the download manager

-r means get everything

-l1 means only on this page (if you used -r without -l1 it would download the entire website :shock:)

-A means all files of a type, so -A.mp3 means all mp3 files

lastly you just need the address of the page.

***EDIT

I`ve just checked the wget man page and although I always understood -A to mean all, it actually means accept(files of this type) so you could -A.mp3,.jpg and get all the jpgs on the page too.

This works in conjunction with -R which means reject, so specifying -R.mp3 would download everything on the web page except for mp3s.

***EDIT

---

