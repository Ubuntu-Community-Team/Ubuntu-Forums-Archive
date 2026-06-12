---
title: "securely reformatting a usb HD"
date: 2009-01-12
forum: New to Ubuntu
---

### Post by Dave B on 2009-01-12
i am looking for a way to reformat a external USB hd so that the data that was previously o it can not be retrieved.

I have tried SHRED but that seems to be for specific FILES and file types.

can someone please make suggestions

thanks 

Dave

---

### Post by boof1988 on 2009-01-13
If you use...

```
sudo shred -v /dev/sdb # "/dev/sdb" or whatever device it is
# the -v is for verbose
```

Doesn't that overwrite each bit (default of 25 times) with a random number?  And with option -z it will write a final zero to each bit if you like.

When I have used it (with only one write cycle of zeroes):

```
sudo shred -v -n 0 -z /dev/sdb
```

it took an hour or so IIRC for a 40GB HDD.

Does this help any?

EDIT:

You may also find [Darik's Boot and Nuke (DBAN)](http://www.dban.org/) of interest.

---

### Post by boof1988 on 2009-01-15
<Bump>

I'm interested in other input.

Thanks...

---

