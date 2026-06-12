---
title: "nvidia nforce network controller driver gcc 4.2"
date: 2007-10-30
forum: Networking &amp; Wireless
---

### Post by rodencaseyw on 2007-10-30
Hi Sorry if this is a repost and this has already been fixed, but im in Iraq atm and its hard for me to actually check out the other posts that are made. Anyways here is my problem my nvidia nforce network controller isnt working and so i went to the nvidia site and downloaded the driver. went to install it and it told me i had the wrong gcc kernel installed 4.2 and not 3.4 ... well i went back and tried this command:

 $ cd “directory where you have the nvidia installer”
$ su
$ CC=gcc-3.4
$ export CC
$ exit
$ CC=gcc-3.4
$ export CC

After that tried it again and still got the same error code while trying to install it. Is there a way to manually install it or is there another way to change or trick it into installing it? lol thanks guys for anything you can do. Oh and I can't just run to my computer and work on it so if it takes me a while to get some info on it and get back sorry.

---

### Post by rodencaseyw on 2007-10-31
Anyone? if someone can link to another page that has a fix I think I might be able to vew it that way.

---

