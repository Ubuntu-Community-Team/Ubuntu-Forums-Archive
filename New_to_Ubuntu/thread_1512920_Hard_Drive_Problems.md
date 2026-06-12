---
title: "Hard Drive Problems"
date: 2010-06-18
forum: New to Ubuntu
---

### Post by Hunter Morrell on 2010-06-18
Recently, I've been trying to upgrade my small 13 gig hard drive to a slightly more spacious 40 gig one. I turned my computer on earlier and was stunned to see the following:
[IMG]http://i433.photobucket.com/albums/qq54/hjmrrll13/image.jpg[/IMG]

Naturally, I tried to fix it, even going as far as to remove every cable in the CPU. I even removed the BIOS battery. Nothing. I tried it with another hard drive. Same thing. I know for a fact that both work, because both worked earlier today. Simply put, I am stumped. Any help would be greatly appreciated, because I am about to cry in frustration.

---

### Post by skatinjj on 2010-06-18
Did you try pressing "F" to fix the errors?  If so, what kind of output were you given?

---

### Post by Hunter Morrell on 2010-06-18
I did. And I got this:

[IMG]http://i433.photobucket.com/albums/qq54/hjmrrll13/0618001745.jpg[/IMG]

---

### Post by skatinjj on 2010-06-18
Did you swap the hard drives out or have both in your system?

Did you do a fresh install on the 40 gig?

---

### Post by skatinjj on 2010-06-18
Also, I would boot using the live cd, then in a terminal:

sudo apt-get install smartmontools

then

smartctl -t long /dev/sda 

replacing /dev/sda with what drive your testing is

---

### Post by ashwinrao on 2010-06-18
It seems that the hard drive partition has the bad sectors in it. I had a same issue with 10.04. It displays error message and fails to boot on next attempts. My suggestion is to backup your valuable data and re-install the 10.04 on clean partition.

---

### Post by Hunter Morrell on 2010-06-18
Yes, I did do a fresh install on the 40 gig. And I tried it with both in, then with one in, and then the other in. Got the same result each time. I don't have anything of important value on there, so I'm probably just going to do a fresh install

---

