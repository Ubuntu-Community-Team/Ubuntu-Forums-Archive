---
title: "command needed"
date: 2009-04-22
forum: New to Ubuntu
---

### Post by sazan on 2009-04-22
can anyone tell me a command to list the last file created by me.. 

I have created millions file 4-5 days back and then the inode table got filled, i want to see at what time the last file got created in that day.

was going for 'find' command , couldn't get proper filtering for it.

---

### Post by kpkeerthi on 2009-04-22
To find the files in your home directory that were created/modified within the past five days:
```

find ~ -mtime -5 -daystart 

```

To find the files that were created/modified from four to five days ago:
```

find ~ -mtime 4 -mtime -5 -daystart 

```

You might as well use -atime instead of -mtime but may not work if noatime mount option is specified in /etc/fstab

The below command should print the details of the file found (permissions, exact modification timestamp, etc)
```

find ~ -mtime -5 -daystart -exec ls -l '{}' ';'

```

---

### Post by sazan on 2009-04-22
Hi thanks a lot.. 
i also found this... [http://www.linux.ie/newusers/beginners-linux-guide/find.php](http://www.linux.ie/newusers/beginners-linux-guide/find.php)


The one i liked was the one below..

$ touch -d "13 may 2001 17:54:19" date_marker
$ find . -newer date_marker

---

### Post by kpkeerthi on 2009-04-22
> **sazan said:**
> 
$ touch -d "13 may 2001 17:54:19" date_marker
$ find . -newer date_marker
That's a nice trick.

---

