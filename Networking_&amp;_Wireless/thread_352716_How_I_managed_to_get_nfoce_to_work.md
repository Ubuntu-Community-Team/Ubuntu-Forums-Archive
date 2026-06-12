---
title: "How I managed to get nfoce to work"
date: 2007-02-03
forum: Networking &amp; Wireless
---

### Post by rnodal on 2007-02-03
First of all, this may not work for everyone. I have an ASUS P5N32-E mother board and it worked.

```

sudo vim /etc/modprobe.d/options

```

Add this to the file:
```

options forcedeth msi=0 msix=0

```

then save the file. And type the command:
```

sudo modprobe -r forcedeth

```

after that type the command:
```

sudo modprobe forcedeth

```

and finally type:
```

sudo /etc/init.d/networking restart

```

I hope it works.


-r

---

