---
title: "[SOLVED] Windows Share With Space In Name"
date: 2008-05-15
forum: Networking &amp; Wireless
---

### Post by eeboy on 2008-05-15
I am trying to mount a windows share with a space in the share name. I tried quotes and that doesn't work. Here's what I have added to /etc/fstab:

```
"//Server01/shared files" /mnt/win cifs exec,credentials=/etc/cifspw 0 0
```

Further complicating things my username has a space in it as well so I made my credentials file as follows:

```
username="user name"
password=pass
```

/mnt/win does exist as well.

Any suggestions?

---

### Post by dmizer on 2008-05-15
use \040 for your space:
```
//Server01/shared\040files /mnt/win cifs exec,credentials=/etc/cifspw 0 0
```

as for the space in your user name, there's no way around it that i'm aware of.  best bet is to change it to a username without a space. if this is not an option, you may not be able to use a credentials file.

---

### Post by eeboy on 2008-05-15
'\040' works in the /etc/fstab file
'\ ' works on the command line

Changing the username was easy enough and so that's what I did.

---

