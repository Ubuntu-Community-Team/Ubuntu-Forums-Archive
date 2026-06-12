---
title: "can i restore with remastersys"
date: 2010-02-04
forum: New to Ubuntu
---

### Post by DarinB on 2010-02-04
I am getting crashes upon crashes since i went to thunderbird 3.0 and now i have tried so many things to fix it i have no idea where i am at. 
I do have an iso distribution of my pc on dvd....it has thunderbird 2.0
my /home is on a second hdd.
can i write over my current os and replace it with the remastersys iso. and point to my /home and not lose anything????? or atleast go back to more stability in my life????

---

### Post by DarinB on 2010-02-04
help!!!!!
I feel like i am using windows with all the freezes and crashes!!!!

---

### Post by ibuclaw on 2010-02-04
If you've got a separate /home, it should be OK to reinstall, and setup it back up correctly.
To do this, use the "advanced" option in the installer partitioning stage.

If you have any custom repositories.
```

mkdir ~/backup
sudo cp -a /etc/apt ~/backup

```

To backup your installed package lists.
```
dpkg --get-selections  > ~/backup/saved-pkgs
```


Then after reinstalling:
```

sudo cp -a ~/backup/apt /etc
sudo dpkg --clear-selections
sudo dpkg --set-selections < ~/backup/saved-pkgs
sudo apt-get dselect-upgrade

```

Regards
Iain

---

