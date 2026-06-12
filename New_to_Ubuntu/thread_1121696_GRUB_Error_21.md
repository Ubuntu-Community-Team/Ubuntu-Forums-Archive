---
title: "GRUB Error 21"
date: 2009-04-10
forum: New to Ubuntu
---

### Post by Desert Sailor on 2009-04-10
I know just enough to really screw things up, so I am posting here before I trash my system.  Here is the background.  I am setting up a new system for my Daughter.  The Micro-ATX mother board only has one (1) IDE connection, so because of cable restraints, I have set the CD-ROM as Master, and the Hard Drive as Slave.  I believe that during install, GRUB has tried to locate the boot strap on the CD ROM, and now gives Grub Error 21 when trying to boot to the new install. 

Question:  If I boot with the install CD and use the terminal window to force GRUB to the slave hard drive, will that solve the problem.  (I am at work and can't try out my theory and wanted to check with you experts before I spend hours going in circles.)   

Thanks in advance.

---

### Post by LowSky on 2009-04-10
I bet you didn't realize this but on an IDE cable the connector in the middle is the master, the one on the end the slave


like this

```


|----------------|--------|
Main board     Master   Slave


```

so just make the CD-ROM Slave, and the hard drive master and all will work

---

### Post by Desert Sailor on 2009-04-10
If that's correct then all I have to do is swap the jumpers.  I didn't know that the center plug was Master.  THANKS!

---

### Post by LowSky on 2009-04-10
It's common mistake. They put the slave on the end so a user could add a new drive easily in the future.

---

### Post by Desert Sailor on 2009-04-10
OK...so here's a new twist on the same question.  Could I swap the cable end for end and hook it like this....

CD-ROM            Hard Drive  Mother Board
Slave               Master      System
  |-------------------|------------|

---

