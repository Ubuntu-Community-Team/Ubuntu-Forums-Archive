---
title: "how to move files, sudo command"
date: 2009-07-14
forum: New to Ubuntu
---

### Post by benh13 on 2009-07-14
I am trying to move a html file to var/www, but i don't have permission. does anyone know the sudo command I can use move files from on folder to another?
thanks

---

### Post by tarps87 on 2009-07-14
mv /*pathToFile*/*fileToMove */*pathToNewLocation*/

mv /*pathToFile*/*fileToMove */*pathToNewLocation*/*newFileName*

mv -r /*pathToFile*/*folderToMove */*pathToNewLocation*/

mv -r /*pathToFile*/*folderToMove */*pathToNewLocation*/*newFolderName*

Hope this helps

---

### Post by nothingspecial on 2009-07-14
```
sudo mv file/you/want/to/move.html /var/www/
```

---

### Post by benh13 on 2009-07-14
cheers, that worked well

---

### Post by 3rdalbum on 2009-07-14
Note that you can use "cp" to copy, rather than "mv" to move, if you want.

If you're using a GUI, you can open a file browser as root and then you'll have permissions to drag and drop files into that folder:

```
gksudo nautilus
```

---

