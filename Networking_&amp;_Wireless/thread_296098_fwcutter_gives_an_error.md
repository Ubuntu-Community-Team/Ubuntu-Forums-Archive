---
title: "fwcutter gives an error"
date: 2006-11-09
forum: Networking &amp; Wireless
---

### Post by manishk on 2006-11-09
I have a Broadcom 4311 wireless card on my HP nx6325 laptop.

I have installed fwcutter from source code and have a copy of wl_apsta.o onto my desktop. When I run the command to extract the firmware I get an error message as follows:
> Sorry, the input file is either wrong or not supported  by bcm43xx-fwcutter. I can't find the MD5sum a252e362boe117dd62a116d069bdfdd0 :(

Whats wrong? I dont have net access through Ubuntu as wireless is my only option

---

### Post by manishk on 2006-11-10
I successfully extracted the firmware today. For future reference

I think the problem was with the .o driver...I tried with bcmwl5.sys and it worked.

I use a BCM4311 card so may be .o doesn't work for that. Just guessing

---

