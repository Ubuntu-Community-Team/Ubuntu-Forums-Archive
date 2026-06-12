---
title: "Help Softlink vs Directory"
date: 2011-02-14
forum: New to Ubuntu
---

### Post by lixianlee1988 on 2011-02-14
i know softlink or symbolic link is a file contains the data which is pathname of otherfiles
 
 well, i find an definition of directory 


"Now, the filename part of the file is stored in a special file of its own along with the filename parts of other files; this special file is called a directory. The directory, as a file, is just an array of filename parts of other files.     "

 so can we say that directory is just a special softlink which contains pathname of itself?

 and for the softlink, where do theirs' filename part store?

 then can a softlink contains the data which is pathname of another softlink?

 i am confusing...

 here is the reference:

[http://linuxgazette.net/105/pitcher.html](http://linuxgazette.net/105/pitcher.html)

---

### Post by vanadium on 2011-02-14
Any name of a file or a directory on a linux file system is a hardlink. A hardlink, referring to an inode number. The inode number is the main and unique identifier of the file or directory. It points to one specific data storage location on the partition. In that data storage location, user data is kept in case of a file, references to other files and directories are kept in case of a directory.

A softlink is a little file indeed that cross references to a file or directory in another location. The power of softlinks under linux is that from the user's point of view, they behave just like a real file or directory.

---

