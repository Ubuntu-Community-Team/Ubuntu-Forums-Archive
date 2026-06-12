---
title: "partition problem...(less free space than it should) ?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by iKonaK on 2009-03-04
...aparently i should have more free space, i attached a screenshot to show what's all about.....please enlighten me on this issue :(

---

### Post by Bachstelze on 2009-03-04
The missing 5 GB are diskspace thet is reserver for root (5% of the total space on the partition). The space is there, you just can't use it with your normal user accound (only root can).

Since this is not your system partition, you can safely change it to 1%, or even disable it altogether. This is done by using the [font="monospace"]tune2fs command[/font], or example:

```
sudo tune2fs -m 1 /dev/sdb1
```

---

### Post by iKonaK on 2009-03-04
Thanks, that did the job :)

---

