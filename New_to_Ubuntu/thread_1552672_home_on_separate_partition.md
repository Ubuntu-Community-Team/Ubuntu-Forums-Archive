---
title: "home on separate partition"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by L2U2K2E on 2010-08-13
I am planning to reinstall lucid for a number of reasons, and figured this is a good opportunity to make my home directory on a separate partition from my install. Unfortunately I don't know how to do this and have had little luck finding information on it. How do I make my home file on a separate partition? How large should I set up my OS partition to be? Also, can the new /home be NTFS?

---

### Post by wojox on 2010-08-13
Scroll down to the [Here's how you do a manual partitioning with /home]("http://news.softpedia.com/news/Installing-Ubuntu-10-04-LTS-141550.shtml")

Here's a [Convert gigabyte to megabyte calculator]("http://www.convertunits.com/from/GB/to/MB") it will come in handy.

---

### Post by oldfred on 2010-08-14
Two links using different commands to copy.

To move /home uses rsync  (cp with -a should also work):
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)
Uses cp -ax
[http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html](http://www.ivankuznetsov.com/2008/04/moving-home-to-its-own-partition.html)

cp without -a and copying as sudo then root takes ownership (see below)

If you have issues this may help:
Sometimes there are dmrc errors or permission errors and this has how to correct them:
[https://help.ubuntu.com/community/dmrcErrors](https://help.ubuntu.com/community/dmrcErrors)

---

