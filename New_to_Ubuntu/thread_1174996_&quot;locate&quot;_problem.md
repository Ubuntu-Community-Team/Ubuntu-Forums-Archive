---
title: "&quot;locate&quot; problem"
date: 2009-05-31
forum: New to Ubuntu
---

### Post by PGScooter on 2009-05-31
Hi,

This is quite frustrating for me. I created a database file for my external hard drive using updatedb. I am quite sure that the database was created correctly.

I then unmounted and disconnected my hard drive, and tried to search my database file for music files using the command:

```

sudo locate -d extwd -i *.mp3

```

Nothing showed up. I then connected the hard drive and mounted it and ran the command again. This time, a billion files showed up (as they should). I opened the database file in vim and searched for .mp3 and found a million as well.

Could the -e option be turned on by default for some reason?

Thank you!

---

### Post by nhasian on 2009-05-31
do you need to input the full path of the database?  like ~/extwd instead of just extwd?  also why do you need sudo?  I only use sudo to update the database with the command:

```
sudo updatedb
```

---

### Post by PGScooter on 2009-06-01
hi nhasian, thanks for the reply. I use sudo because of file permissions on the database file. I tried changing the file permission and getting rid of sudo, but that did not change anything. I also tried the full path with no success.

The strange thing, as I described above, is that the command works perfectly when the drive is mounted! That is what makes me thing that it is a problem with the options of the locate command.

---

### Post by PGScooter on 2009-06-01
I posted a bug report here:

[https://bugs.launchpad.net/ubuntu/+source/mlocate/+bug/382330](https://bugs.launchpad.net/ubuntu/+source/mlocate/+bug/382330)

---

