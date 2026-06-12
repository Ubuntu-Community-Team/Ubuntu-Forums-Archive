---
title: "slave HD added after install causes problem"
date: 2010-04-09
forum: New to Ubuntu
---

### Post by stevek123 on 2010-04-09
I've posted a cpl threads with my headaches installing Karmic onto a hand-me-down machine this week. Now I've a new one. I suspect its not a true ubuntu issue but I gotta ask...

I got Karmic installed onto a sata drive. After I did it, I added a std ide ribbon and added a std ata ide HD from an old cooked M$ machine. Its got ~ 40GB of my music and photos on it I'd like to access. The sata was set as master, the ata as a slave. Bios boot showed both recognized as that. BUT then it went to try and boot into the ata slave! There is no OS there and it just stalled. I checked the boot settings and it wont give me an option to boot onto the sata/master/karmic, just to either CD or the slave-but NOT the sata. 

Is there a solution to this? If I had had the slave ide present during the install, would gparted have let me thru to a proper setup? Can I boot with the karmic cd and use gparted there to identify the ata/slave as a folder? I'd assumed that Karmic would be able to read and access all the data there (FAT32) but maybe not???

---

### Post by iMisspell on 2010-04-09
Is the SATA onboard or a card ?

_

---

### Post by stevek123 on 2010-04-09
Onboard sata (4 sockets there - its in the first)

---

