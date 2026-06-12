---
title: "wireless internet setup"
date: 2007-11-03
forum: Networking &amp; Wireless
---

### Post by jeremy119 on 2007-11-03
i am using this to set up wireless internet  **[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)**
and i have gotten to a point were it says 

**media change: insert the disk labeled 'ubuntu 7.10 _gutsy gibbon_ - release i386 (20071016)'  in the drive    '/cdrom/' and press [enter]**


i dont have that disk and i dont know were to get it from 

someone please help

---

### Post by magickangaroo on 2007-11-03
Hi Jeremy.
This is happening as in your /etc/atp/sources.list thre is an entry for your cd rom as a source.

to fix this, 

```

sudo nano /etc/apt/sources.list

```

find the one beginning ```
deb cdrom:[
``` and put a hash in front of it.  This will comment it out so that it wont be used.  if you then do an 

```

sudo apt-get update

```

to load in the changes.  you should now be able to use just the internet repositiories.

if nano isn't installed try using vi instead


hope that helps

mgk

---

