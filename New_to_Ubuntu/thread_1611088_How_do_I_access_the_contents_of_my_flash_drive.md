---
title: "How do I access the contents of my flash drive?"
date: 2010-11-01
forum: New to Ubuntu
---

### Post by redfox1160 on 2010-11-01
I want to view the contents of my flash drive in the terminal, how would I do this???

---

### Post by NertSkull on 2010-11-01
once its mounted you can just cd to it like a normal directory.

it probably mounts in /media 

so I'd look for it there.

you can also do

sudo fdisk -l

to list all your drives and see what one it is if needed

---

