---
title: "Dvd drives not mounting"
date: 2010-06-03
forum: New to Ubuntu
---

### Post by gannons on 2010-06-03
Hello!

      When I insert a dvd into my dvd drive, it wont let me mount it. It detects it and labels it (in this case a Sims 3 disk) but when I mount it i get this error

Error mounting: mount: block device /dev/sr0 is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/sr0,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so

When i run Dmesg | tail i get
[ 1527.179320] UDF-fs: No anchor found
[ 1527.179324] UDF-fs: No partition found (1)
[ 1616.454031] UDF-fs: No anchor found
[ 1616.454036] UDF-fs: No partition found (1)
[ 1815.730778] UDF-fs: No anchor found
[ 1815.730782] UDF-fs: No partition found (1)
[ 1894.706702] UDF-fs: No anchor found
[ 1894.706707] UDF-fs: No partition found (1)
[ 2538.746203] UDF-fs: No anchor found
[ 2538.746208] UDF-fs: No partition found (1)


 On another note, I have two dvd drives but the other one won't open/isnt detect.

---

### Post by gannons on 2010-06-04
bump!

---

### Post by ashwinhgtx on 2010-06-04
Are you sure the discs are not corrupted? Do the drives work fine with any other OSes?

---

### Post by gannons on 2010-06-04
When I had windows xp on it everything worked alright. both drives did

---

### Post by gannons on 2010-06-04
Just tried putting a random new disk in there and it worked (war hammer disk). So i though maby my sims disk was damaged. however it seams none of my other disks (cod 4, civ 4) work in the drive. could it just be from damaged disks?

---

### Post by ashwinhgtx on 2010-06-06
Try a random data disc instead of those old game discs. See if it makes any difference.

---

