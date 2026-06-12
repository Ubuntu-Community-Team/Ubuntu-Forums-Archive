---
title: "trouble with synch files..."
date: 2007-07-23
forum: Networking &amp; Wireless
---

### Post by bar8080 on 2007-07-23
can somebody pls give the command line to extract the synch files to /etc/eciadsl the file format is: filename.tar.tar 
Thanks.

---

### Post by Mr. C. on 2007-07-24
I have no idea what you mean by "the synch files".

The command to extract files from a tar archive is:

```
tar -xvf *filename.tar*
```

This will extract all the files in the archive. Before you do that, you should examine the tar archive contents with:

```
tar -tvf *filename.tar*
```

This will list the contents - you can extract any files you want.  You may need to place them in the directory you desire after extraction.  It is too complicated to explain briefly here how you extract the contents of any random tar file into the directory you want.

Perhaps more specific information will help...
MrC

---

