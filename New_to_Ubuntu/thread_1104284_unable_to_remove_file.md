---
title: "unable to remove file"
date: 2009-03-23
forum: New to Ubuntu
---

### Post by hellomoto on 2009-03-23
In my fiddling with my ubuntu install. i have some how managed to create a file which I am unable to remove.

in the directory i want to a deleat there is a hidden recreating file named:

  .fuse_hidden0000ade500000027

when ever i try to deleat this file ubuntu recreates another one in its place. I am therefore unable to remove the directory it resides in because I get the error: 

   Error removing file: Directory not empty

I have even gone as far to try and remove the directory with the following command.
                     
         sudo rm -rf /directory_name/
but even this returns the same error.

any idea?

---

### Post by kanikilu on 2009-03-23
[http://ubuntuforums.org/showthread.php?t=550145](http://ubuntuforums.org/showthread.php?t=550145)

---

### Post by hellomoto on 2009-03-23
thank you for your feedback 

i restarted my pc so my hard disk unmounted then remounted and i was then able to deleat the directory.

sorry if this was a pointless thread!

---

