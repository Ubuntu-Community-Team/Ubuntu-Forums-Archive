---
title: "HELP WITH INSTALLING! installing xawtv"
date: 2009-03-21
forum: New to Ubuntu
---

### Post by completenovice on 2009-03-21
I wwant to install xawtv to watch video with the rca connector on the videocard
i have downloaded the .tar.gz file and extracted it
when i run the ./configure thing it tells me i need to get :

(n)curses library  and some
*-devel package

i have no idea what these are. could someone tell me waht they are and how to install them
thanks!

---

### Post by Kosimo on 2009-03-21
> **completenovice said:**
> I wwant to install xawtv to watch video with the rca connector on the videocard
i have downloaded the .tar.gz file and extracted it
when i run the ./configure thing it tells me i need to get :

(n)curses library  and some
*-devel package

i have no idea what these are. could someone tell me waht they are and how to install them
thanks!

Why don't you try to install it from repos?

open a terminal and type


sudo apt-get install xawtv

---

### Post by lovinglinux on 2009-03-21
xawtv is already in the repositories, so you don't have to compile it. Just go to "Applications >>> Add/Remove", then select "All available applications" in the "show" drop-down menu and type "xawtv" in the search.

You just have the "Universe" repository enable to find it. 

You can also install it from command-line:

```
sudo apt-get install xawtv
```

Additionally, you must make sure you card is properly configured and that the application is compatible with it. Some TV applications work only with analog cards and others just with DVB cards.

You might wanna try tvtime too.

---

