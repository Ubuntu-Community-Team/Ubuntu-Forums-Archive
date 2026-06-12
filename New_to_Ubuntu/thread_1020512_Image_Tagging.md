---
title: "Image Tagging"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by harsh_ on 2008-12-24
Well, I want to tag my photos. F-Spot is the place. Now the only thing I am concerned of id, if I change my OS from Ubuntu 8.04 to Ubuntu 9.xx or some other version (BUT DEFINITELY UBUNTU) or I format my PC. After the backup and import process, will the tags still remain, or they will have to be tagged again??

---

### Post by CatKiller on 2008-12-24
If you dist-upgrade to some future version of Ubuntu (rather than re-installing) then nothing will change, and everything will still work.

If, instead, you re-install, then you'll potentially lose some of your tags. Tags for JPEGs are stored as meta-data in the files themselves, so they will remain intact. Other filetypes have their tags stored in F-Spot's database, which I'd imagine is stored in your Home folder. If your Home folder (and the database) are left intact by your installation process, then the tags will still work.

If you blow away your Home folder and re-import the images, you will only get to keep the tags for JPEGs.

---

