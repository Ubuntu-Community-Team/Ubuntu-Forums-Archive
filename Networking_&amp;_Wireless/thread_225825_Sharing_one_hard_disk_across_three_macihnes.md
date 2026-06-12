---
title: "Sharing one hard disk across three macihnes"
date: 2006-07-30
forum: Networking &amp; Wireless
---

### Post by harisund on 2006-07-30
Here's my scenario. I have 3 machines, m1, m2 and m3. m1 has a 150 GB hard-disk and a 10 GB hard disk, while the other 2 are basically 10 GB hard disks. 

m1 is a relatively slow machine while m2 and m3 are faster( all have 256 MB of RAM, m1 is 500 Mhz, while m2 and m3 are 900 each). 

In m1, / is mounted on the 10 GB one and /home is mounted on the 150 GB harddisk. 

I have a lot of shell scripts, aliases and stuff for convenience, and naturally I want them replicated in all the 3 machines. 

The problem is, I don't have a network attached storage. So how do I share some folder in the 150 GB hard disk of m1 alongside all 3? 

I was thikning I would create a user in the m1 machine called convenience "misc" or something (so that a directory would be created in the /home 150 gb harddisk) and put all scripts there. 

How would I do this? Samba? NFS? Can somebody help me out?

---

