---
title: "Problem with wireless on my tx2120us"
date: 2009-12-12
forum: New to Ubuntu
---

### Post by theflanman on 2009-12-12
I am a computer geek with knowledge of how these things work, but i'm new to linux(got it so that I could do coding easier), and i have no idea what drivers to use on my wireless card.:(
Please send help.

---

### Post by Hetepeperfan on 2009-12-12
Some of the problems discussed on this ubuntu page:

[https://help.ubuntu.com/9.10/internet/C/index.html](https://help.ubuntu.com/9.10/internet/C/index.html)

Perhaps you can find what you are looking for on these pages. It is possible to use your windows drivers to get your problems solved, but that is ususally as a last resort.

---

### Post by theflanman on 2009-12-12
that's not the problem, I can't find a driver that supports my wireless card, that's what i really need.

---

### Post by bkratz on 2009-12-12
First thing needed is to determine the wireless card used.

Go to the terminal
Applications ...Accessories..terminal
type in the following:

lspci | grep Wireless

(that is LSPCI in lowercase)

and paste the ouput back here or just decode.

If you don't see anything just try lspci

---

### Post by Favux on 2009-12-12
Hi theflanman,

You need the Broadcom proprietary wireless driver (wl).  It should be available in System > Administration > Hardware Drivers.  If it isn't check in System > Administration > Software Sources in the Ubuntu Software tab that Proprietary drivers is checked.  If that doesn't do it try the Updates tab and check Unsupported updates/backports.

---

### Post by theflanman on 2009-12-12
Thank you everyone for your help, it's up and running now!

---

