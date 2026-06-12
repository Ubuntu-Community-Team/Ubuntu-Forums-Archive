---
title: "File System running out of space"
date: 2010-07-01
forum: New to Ubuntu
---

### Post by Shinigamy91 on 2010-07-01
First of all, im a a nooblet to Ubuntu (you guessed ha!?) and i got some problem to be fixed... Maybe its just me, maybe its common, idk, but its gettin me freakin' crazy from hour to hour :) Ok, first im goin to post my configuration:

Pentium (r) Dual - Core CPU E5300 @ 2.60ghz
Ram: 2 GB Hyper X
Motherboard: P5Q SE/C/Si
HD: 300 gb (3 partition's) 
Graphics: GeForce 9600 Gt 1gb

C:20 gb (where i store my windows xp in case Ubuntu fail O.o),

D: 200 GB (usual everyday storespace), 

and G: 80gb (Ubuntu 10. 04 space). (pay atention to this one)


Here's the problem... 

When ever i try installing some application, i got error tellin' me that i dont have any space left in File System? I got like 20mb free in file system... Cant install any app's or do anything right :/ in my host i got like 70GB free... So i was wondering, is there any solution, for example, to change path of app installing to host or something (where i have more space)... Its gettin' realy anoying, i dont want to go back to window's, cuz im freakin' amazed by ubuntu :) Just like everyone else :KS. 

O and, about installation. I installed from Windows Xp sp2, clean copy of Ubuntu from scratch, on separate partition (as you see in above posted). Dont know where i got wrong, i dont want to reinstall it again :(

---

### Post by Shinigamy91 on 2010-07-01
Bump! Anyone! Pls help, im getting desperate :/

---

### Post by bumanie on 2010-07-01
Type in terminal and copy/paste the output here. Applications --> Accessories --> Terminal > sudo fdisk -lThis will show how your partitions are set up after that > df -h /

---

### Post by Jest3r on 2010-07-01
[QUOTE=Shinigamy91;9535067

C:20 gb (where i store my windows xp in case Ubuntu fail O.o),

D: 200 GB (usual everyday storespace), 

and G: 80gb (Ubuntu 10. 04 space). (pay atention to this one)

[/QUOTE]

I am operating of the following assumptions:

   C: and D: are both NTFS
   D: is full of visual media
   G: is EXT3 ( ubuntu is installed here)
   drive C: and D: are mounted in ubuntu.

Few options:

  1. Get more space
   
   If you not using all of D: then repartition it to 100Gb NTFS, 100GB EXT3 
  
  2. Reduce your harddrive footprint
   
   Delete things you no longer needed, or if you have media move it to the D: from the G:

   Below is a quick visual way of find large files and directories ( folders ) 

   accessories -> Disk usage analyser
   Then click the 2nd icon ( Scan filesystem )

---

### Post by Miljet on 2010-07-01
Before everyone goes crazy trying to second guess this installation, consider the possibility that Ubuntu is installed under WUBI. Otherwise, it is up to the OP to furnish requested information.

---

### Post by Miljet on 2010-07-03
> Bump! Anyone! Pls help, im getting desperate :/

Must not have been too desperate.

---

