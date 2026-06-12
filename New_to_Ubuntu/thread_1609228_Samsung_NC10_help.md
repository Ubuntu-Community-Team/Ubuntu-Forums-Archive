---
title: "Samsung NC10 help"
date: 2010-10-30
forum: New to Ubuntu
---

### Post by rjmanmac on 2010-10-30
hello everyone
i have a samsung nc10 netbook, installed with ubuntu 10.10 but im having a few problems :-k
i have ubuntu installed with mac OSX and windows XP as my other operating systems but have not had the same problem
Firstly, i cant type using any of the letters with the numberpad printed on, to type a letter i have to hold down the blue Fn button on my keyboard.
I am not sure whether this is down to the OS but vertical movement on the touchpad is much less responsive than horizontal movement..
Thanks in advance! :P

---

### Post by rjmanmac on 2010-10-30
i forgot to add i cant adjust the brightness/volume either :-(

---

### Post by rjmanmac on 2010-10-30
update: i can now adjust the volume and have sorted the keyboard problem out :)

---

### Post by DirtyPC on 2010-10-30
> **rjmanmac said:**
> i forgot to add i cant adjust the brightness/volume either :-(
Hello mate, good to see your problem is now solved! The brightness/volume is a common problem, just search around on this forum and you may find your answer. Could you please now mark this thread as closed?

Thanks

---

### Post by Verbeck on 2010-10-30
> **rjmanmac said:**
> update: i can now adjust the volume and have sorted the keyboard problem out :smile:

its a good thing to include how you fixed the issue, so others with the same problem can get a solution too while searching the forums :)

---

### Post by rjmanmac on 2010-10-30
sorry @verbeck
i solved my keyboard problem by turning the numlock off! it seemed to have turned itself on during the initial install :$
regarding the volume issue, i had to use the keyboard shortcuts program to make Fn+right/left turn my computer up or down

---

### Post by DirtyPC on 2010-10-30
> **Verbeck said:**
> its a good thing to include how you fixed the issue, so others with the same problem can get a solution too while searching the forums :)
He had numlock on... Aha.

So the fix is turn numlock off, but if it doesnt work.. you can re map your keys with xev and xmodmap, and i'll post a how to if need be

Edit: Sorry Ryan, didn't see your post

---

### Post by SirReel on 2011-04-29
I tried the fix at the following URL for my Samsung NC-10 and I am now able to adjust the brightness with the function keys:

[http://poweredbypizza.blogspot.com/2010/10/ubuntu-linux-1010-brightness-fix.html](http://poweredbypizza.blogspot.com/2010/10/ubuntu-linux-1010-brightness-fix.html)

Steps were:

sudo add-apt-repository ppa:voria/ppa

sudo apt-get update && sudo apt-get upgrade

sudo apt-get install samsung-backlight

Special thanks to PoweredByPizza (From the above URL).

---

