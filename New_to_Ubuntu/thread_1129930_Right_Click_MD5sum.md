---
title: "Right Click MD5sum"
date: 2009-04-19
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-19
Is there a program that will let me check the md5sum of a file easily?

---

### Post by Anthon on 2009-04-19
on the commandline:
  md5sum filename

---

### Post by thunk77 on 2009-04-19
Untar file and place it in your home folder, under .gnome2/nautilus-scripts. Then right click on the file you want to check and choose it from the menu "Scripts" that will appear.

---

### Post by yeehi on 2009-04-19
Thank you very much! :)

That will be just what I want, when I get it working. :confused:

At the moment, whatever file I check, I receive the following:

> =-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=-=
No MD5-Sum for /home/...

It is Ubuntu 64 alternate, I am running.
btw, what is the md5sum for this file? :)

---

### Post by zzHanks on 2009-04-19
Here are the sums for 8.10: [http://mirror.anl.gov/pub/ubuntu-iso/CDs/8.10/MD5SUMS](http://mirror.anl.gov/pub/ubuntu-iso/CDs/8.10/MD5SUMS) (just change 8.10 in the URL to the release you have, if you have to).

---

### Post by thunk77 on 2009-04-19
> **yeehi said:**
> Thank you very much! :)

That will be just what I want, when I get it working. :confused:

At the moment, whatever file I check, I receive the following:



It is Ubuntu 64 alternate, I am running.
btw, what is the md5sum for this file? :)


hm, you know you have to have the .md5 file along with the .iso in order to have it checked against, right?

---

### Post by yeehi on 2009-04-19
I dont know the .md5 and .iso files.

I do know that if I navigate to the folder and do ```
md5sum filename
``` I get an md5sum reading.

Where do I get those other files?

---

### Post by thunk77 on 2009-04-19
The point for checking an md5 sum (as far as I'm concerned) is to verify that the file is not corrupted. Usually this is a concern when you're downloading files (especially large ones like for example .iso's) and you want to verify their signature so that they are safe to run. 

For example when you download the latest version of ubuntu and want to burn it to a cd in order to install it to your machine and you want to be sure that the file is downloaded properly and it is not corrupted, you run an md5 check AGAINST the original md5 sum that the source (ubuntu site) provides.

So you just want to look at the md5 sums for what?

---

### Post by yeehi on 2009-04-19
I want to make sure that the files I receive on my computer are exactly the same as the files that are published.

The script isn´t working properly on my computer, it isnt yielding md5sums, so I would like to check whether the file I received has been downloaded properly.

---

