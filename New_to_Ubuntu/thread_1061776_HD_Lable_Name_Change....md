---
title: "HD Lable Name Change..."
date: 2009-02-06
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-02-06
How can I change the Hard Drive Lable name of my secondary HD?

---

### Post by konqueror7 on 2009-02-06
yes, you can change the label of a hardrive...just type the following code...
```
sudo gedit /etc/fstab
```

..you will be asked for your root password, then a file would open similar to this...
```
/dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec,utf8 0 0
/dev/sda6 /media/Development ntfs-3g defaults,locale=en_PH.UTF-8 0 0
/dev/sda5 /media/Stuff ntfs-3g defaults,locale=en_PH.UTF-8 0 0
```

..just replace the "/media/Stuff" with the folder you created, for example "/media/MyLabel"...

---

### Post by Leo Dragonheart on 2009-02-06
Than you....:-)

---

