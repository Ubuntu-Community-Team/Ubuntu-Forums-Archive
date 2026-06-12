---
title: "Deleting files and folders"
date: 2010-12-16
forum: New to Ubuntu
---

### Post by cf0531 on 2010-12-16
How do you delete files and folders using the command line?

---

### Post by Old_Grey_Wolf on 2010-12-16
Type this in the terminal and read it carefully.
```
man rm
```
Be careful with the rm command. People have done major damage to their file system with it.

Edit: I also found this link [http://manpages.ubuntu.com/manpages/lucid/man1/rm.1.html](http://manpages.ubuntu.com/manpages/lucid/man1/rm.1.html).

---

### Post by seawolf167 on 2010-12-16
Like Old_Gray_Wolf said, be careful with the remove commands! I suggest reading the man pages and learning the switches carefully before going out and rming everything.

Remove

```
rm
```

Remove (empty) directory

```
rmdir
```

---

### Post by Cha0sBG on 2010-12-16
Quick and easy remove of a directory full of files:
```
sudo rm -rf
```

---

### Post by Spyderkid on 2010-12-16
[SIZE="5"]If you want to securely remove the file use this....
[/SIZE]
cd to the directory which the file is in

```

shred --remove -n 10 -v FILE NAME

```

[SIZE="3"]REPLACE 'FILE NAME' WITH THE FILES NAME.[/SIZE]




[COLOR="Red"]If it says there's no such file rename the file and replace spaces with [COLOR="Blue"]-[/COLOR][/COLOR]

---

### Post by karthick87 on 2010-12-16
Removes file
```
rm <filename>
```
Removes folder
```
rmdir /path/to/folder
```
Removes recursive folders
```
rmdir -R /path/to/folder
```

---

