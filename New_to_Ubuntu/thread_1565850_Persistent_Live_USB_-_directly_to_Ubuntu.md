---
title: "Persistent Live USB - directly to Ubuntu"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by flyver on 2010-09-01
I've been searching the forum, but didn't find exactly what I was looking for.

I'd like to have my portable Ubuntu (on USB flash drive) with files and preferences saved after each session. What I'm having trouble figuring out is how to make it go directly into Ubuntu without asking whether I want to "install now" or "just try".

Thanks!

---

### Post by wilee-nilee on 2010-09-01
If you use the ubuntu startup disk creator it has a persistent function you can turn on and how large up to 4 gigs max. If you used unetbootin you will not get persisitent

You can use this loader and make a persistent then use this method if 4 gigs is not enough.
[http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/](http://www.pendrivelinux.com/create-a-larger-than-4gb-casper-partition/)

As far as I know you can't do this unless you already have created a persistent thumb.

The only way to get past the try or install screen is to actually install it to the thumb. The thumb should be around 8 gigs at least, and you want to make sure grub is installed to the thumb by checking the advanced button in the last install screen.

---

### Post by flyver on 2010-09-01
Thanks,

I managed to make a Live CD, then boot a computer with it, then select install, and then select an empty 16 GB flash drive, instead of the hard drive which was selected by default.

Works great!

---

