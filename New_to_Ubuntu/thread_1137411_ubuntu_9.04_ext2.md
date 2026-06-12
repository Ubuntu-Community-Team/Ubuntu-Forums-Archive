---
title: "ubuntu 9.04 ext2"
date: 2009-04-25
forum: New to Ubuntu
---

### Post by Jack Shankle on 2009-04-25
I am running a triple boot system. Ubuntu 9.04 is on a separate sata drive.
When I UPGRADED from Ubuntu 8.10 to 9.04 I noticed I had filesystem ext2.
I wanted ext3. So how do I change this without destroying all
my data in Firefox and Thunderbird?
Please make it simple as I am an Ubuntu Novice.
Thanks

---

### Post by Sef on 2009-04-25
1) **Back up** all your data before attempting this.   There is no guarantee of 100% success.

2) Read [this thread]("http://ubuntuforums.org/showthread.php?t=193103").

---

### Post by unutbu on 2009-04-25
Open a terminal (Applications>Accessories>Terminal). 
If the device name of the partition is /dev/sdc3, then type
```

sudo tune2fs -j /dev/sdc3
```

The sdc3 partition now has a journal, which, by definition, makes it an ext3 partition.

---

### Post by Jack Shankle on 2009-04-25
Thank you Unutbu.
The sudo command worked like a charm.
It sure helps to know what you are doing.

---

