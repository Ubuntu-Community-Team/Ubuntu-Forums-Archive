---
title: "Upgrade using CD"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by santy_kushwaha on 2008-12-13
hi,

i want to upgrade my desktop from 8.04 to 8.10 using a CD......bcoz my internet is slow

please advice me how to do so? tried some options of the internet but seems like notworking for me

help me 
thnks

---

### Post by taurus on 2008-12-13
Look at the last part of this page about upgrading using the alternate CD.

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

---

### Post by santy_kushwaha on 2008-12-13
i read that article b4 posting and that suggestion don't work as it said use gksu "sh /cdrom/cdromupgrade" in the run window and i used it......but when i press run it goes away and nothing comes

---

### Post by Michael.Godawski on 2008-12-13
See here

[LIST]
[*][https://help.ubuntu.com/community/IntrepidUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD](https://help.ubuntu.com/community/IntrepidUpgrades#Upgrading%20Using%20the%20Alternate%20CD/DVD)
[/LIST]
I guess it should be 
```

gksudo sh /cdrom/cdromupgrade
```

---

### Post by santy_kushwaha on 2008-12-13
it is the same link as above same instructions and i tried gksudo sh /cdrom/cdromupgrade that don't work either 

anyother suggestions please

---

### Post by Michaelg14 on 2008-12-13
An alternative is to use a live CD and install without formating your home partition.  It is not recommended by the experts but since I am not an expert it has worked for me in the past.  Not as good as a clean install but it will work... Usually...

---

### Post by agathian on 2008-12-13
well, did you check if the that file is indeed there?

#ls -l /cdrom/cdromupgrade

may be the cdrom is mounted somewhere else? like /media/cdrom?

---

### Post by logos34 on 2008-12-13
can't you get the popup dialog box to appear when you insert the cd?

[http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html](http://ptcbus.blogspot.com/2008/04/upgrading-from-ubuntu-710-gutsy-gibbon.html)

Either that or do like michaelg14 suggests, but you'd have to move your /home dir to a separate partition first (see link my signature) or back up your files.

[https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion](https://help.ubuntu.com/community/Installation/UpgradeFromOldVersion)
(->'Clean install')

---

### Post by santy_kushwaha on 2008-12-13
i dont get the pop out thats the problem otherwise i would not had a problem and its the orginal CD....i got from ubuntu by order

---

### Post by logos34 on 2008-12-13
> **santy_kushwaha said:**
> and its the orginal CD....i got from ubuntu by order

i think that's your problem right there--the shipit is a live cd, but you can't upgrade from it.  You need to use the text-mode **alternate-install cd.**

---

### Post by Michael.Godawski on 2008-12-13
As posted in my previous post. The upgrade works with the alternate CD.
[http://www.ubuntu.com/getubuntu/downloadmirrors#alternate](http://www.ubuntu.com/getubuntu/downloadmirrors#alternate)

---

