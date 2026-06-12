---
title: "k9copy (Segmentation fault)"
date: 2011-03-22
forum: New to Ubuntu
---

### Post by mushroom08 on 2011-03-22
hi i got k9copy and i have restricted extras, libdvdcss2, and the sudo command downloads from the medibutu site however every time i try to copy a disk i get

Executable: k9copy PID: 7012 Signal: 11 (Segmentation fault) 

the PID: number is differnt each time but the program always crashes at the same point plz help

---

### Post by mushroom08 on 2011-03-23
i figured it out

---

### Post by danabel on 2011-04-19
> **mushroom08 said:**
> i figured it out

Any chance you can expand on this? I'm getting the same error every time I try to rip a DVD

---

### Post by Jerry N on 2011-04-19
My efforts at copying a non-protected video DVD with K9copy over the last two or three years have always failed.  Nerolinux 4 does the job just fine though.  

Jerry

---

### Post by h3lium on 2011-05-07
Well, the following worked for me on 10.04:

1) installed libdvdcss2 like recommend somewhere else using...

sudo aptitude install libdvdread4
sudo /usr/share/doc/libdvdread4/install-css.sh

2) installed ubuntu-restricted-extras

sudo aptitude install ubuntu-restriced-extras


After step 2 it should work but didn't so I went on and...

3) installed the following dev packages with...

sudo aptitude install libdvdcss-dev libdvdnav-dev libdvdread-dev


Guess what? After step 3 k9copy works like a charm! :D

Hope that helps anyone out there.

Greets, h3lium

---

### Post by heavy metal on 2011-05-11
I Followed H3llium's instructions and it worked like a charm, thank you hellium!:KS

---

### Post by Martijn van Es on 2012-03-07
Thanx H3llium!

---

### Post by jesE on 2012-03-09
Thank you, k9 copy works fine now. I'm using ubuntu 11.10.

---

