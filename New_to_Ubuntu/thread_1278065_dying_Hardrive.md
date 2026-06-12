---
title: "dying Hardrive"
date: 2009-09-29
forum: New to Ubuntu
---

### Post by vlad1975 on 2009-09-29
Hi guys 

Just an advice if possible. The HDD that my using which has the UBUNTU installed and all the little bitties are about to die. can anyone suggest a way that i can perhaps completely copy the hard drive to another Hard Drive so when i swap it runs as normal?

---

### Post by MelDJ on 2009-09-29
maybe backup your whole hard drive to an .iso using remastersys: [http://www.geekconnection.org/remastersys/remastersystool.html](http://www.geekconnection.org/remastersys/remastersystool.html). then move it to a new disk

---

### Post by Maxxtsch on 2009-09-29
Get a new S-ATA HD, install Ubantu, Drag and drop all your files.

---

### Post by Grenage on 2009-09-29
Or just use dd to clone the whole drive:

dd if=/dev/sda (ubuntu install) of=/dev/sdb (blank drive)

You can then resize partitions using gparted or the like (assuming it's a bigger disk). You can also clone partitions instead of whole drives.

---

### Post by vlad1975 on 2009-09-29
cool. awesome advise i will try them all see which one will work the best

---

