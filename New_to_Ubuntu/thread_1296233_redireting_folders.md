---
title: "redireting folders"
date: 2009-10-20
forum: New to Ubuntu
---

### Post by patchido on 2009-10-20
ok, i want to do something but i dont know if it is possible, i have a partition where i keep my files, by now i was able to automount it with fstab, and knwo i want to know if it is possible to redirect the folder of documents pics, etc... so if i go to places documents ill go to the other partition's documents

---

### Post by Sarmacid on 2009-10-20
You can create a symbolic link with the following syntax```
ln -s /folder/with/files /home/user/files
```

---

### Post by patchido on 2009-10-20
yes, but that way if i click on documents in the places menu, ill go to the documents in my home, and this folder will have a folder to redirect me isnt it true?? isnt there a way to make the documents inside documents to be the link?

---

### Post by Sarmacid on 2009-10-20
Drag and drop the directory you want to your sidepane, it's as easy as that.

---

