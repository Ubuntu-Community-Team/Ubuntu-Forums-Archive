---
title: "dd"
date: 2011-01-01
forum: New to Ubuntu
---

### Post by 29732 on 2011-01-01
Uhm..... >.<

I am using dd on a live CD to make an image of /dev/sda5 and insert it into /dev/sdb2

Right now I typed in this: sudo dd if=/dev/sda5 of=/dev/sdb2 bs=1024

NOTE: Oops, I forgot I needed to press ctrl-shift-c but at first I pressed the same combo without the shift and now it is showing me this:



```
^C2200058+0 records in
2200057+0 records out
2252858368 bytes (2.3 GB) copied, 372.618 s, 6.0 MB/s

```
Ack
Help?
And how do I do it completely without any mistakes?

---

### Post by solar george on 2011-01-01
While you're in a terminal Ctrl+c ends the current program.
From that output it looks like you'll be there for some time waiting for the copy to complete, dd is a old-style *nix tool and won't print a progress bar or anything unless theres a error or you send it a USR1 signal.
```

sudo pkill -USR1 dd

```

---

