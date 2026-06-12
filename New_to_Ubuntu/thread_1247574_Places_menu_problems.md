---
title: "Places menu problems"
date: 2009-08-23
forum: New to Ubuntu
---

### Post by petegreenhorn on 2009-08-23
(SOLVED) Hi I' have problem (well a few that are probably related)after trying to get bluetooth to work on my box , without success . i uninstalled the packages i had install. Now some items i.e computer are missing from " places " and when i try to open my home folder or any other folder on that menu i get a error saying " Could not open "pete" Archive type not supported " . After searching and googling , didn't get much help only to say that i am lead to beleive that it could be a problem with "nautilus ", though not sure . I'm not very hot with the technical side of computing , Any assisstance gratefully received

---

### Post by Liolikas on 2009-08-23
Try simply to create other user maybe you have mess in settings now.


Other way is to remove some settings directories from home. They start with . and because of this are hidden. You can see them somehow or with:
```

ls -a

```
And remove with:
```

rm -r .name

```
But in this way you can create even bigger mess.

---

### Post by _Purple_ on 2009-08-23
Right click on any directory, Properties > Open with > Add > Open Folder.

---

### Post by petegreenhorn on 2009-08-23
thanks for replies guys but "liolikas " not up for deleting anything just yet and "purple " the right click just gets me to the same error

---

### Post by HiImTye on 2009-08-23
open nautilus in a terminal
to do so go to accessories > terminal and type in
```
nautilus
```
this will post any useful error messages out to the terminal which you can use to post in here

---

### Post by petegreenhorn on 2009-08-23
well just thanks to "HiImTye" the terminal showed me the reason and the answer , some how i had uninstalled nautilus by mistake . Just needed to reinstall to fix the problem. thanks guys

---

