---
title: "gparted and vista"
date: 2009-04-04
forum: New to Ubuntu
---

### Post by pyrocumulus on 2009-04-04
Hi
Ive just bought a Dell studio and would like to install Ubuntu 8.10 on it . Here is how my partition tables look

C: Ntfs  287     -  windows Vista

D: Ntfs  10 GB  -  recovery drive


This is how i wish to partition it.

C: 40 gb - windows Vista

D: 10gb recovery drive

E: 200 gb  Ntfs  partition for data storage

F : 40 gb Ubuntu


I want to know if i can do this using gparted. For some reason I cannot use the vista partition software to shrink the drives to the required size.

---

### Post by tad1073 on 2009-04-04
yes

---

### Post by BoogeyOfTheMan on 2009-04-04
I'm sure it goes without saying to make sure and back up your important files.

Also, make sure you have your windows install disk handy. When I resized and moved my partitions around, windows didnt want to load and I had to do a repair with the install disk.

Dont forget a swap partition, just in case.

EDIT*

You also have to make sure you have the spare room to move and resize. If your windows partition uses more than 40gb, you have to make it smaller or it just going to end up needing a reformat and reinstall of windows.

---

