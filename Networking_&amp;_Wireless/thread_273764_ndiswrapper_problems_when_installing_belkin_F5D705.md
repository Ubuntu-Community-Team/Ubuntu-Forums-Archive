---
title: "ndiswrapper problems when installing belkin F5D7050 wireless USB  driver"
date: 2006-10-08
forum: Networking &amp; Wireless
---

### Post by bithika_mookherjee on 2006-10-08
Hi there,

I'm new to Ubuntu and am trying to get my machine up and running with a Belkin Wireless USB (F5D7050).

Its been suggested on various sites that I need to install the driver using ndiswrapper. I'm using the ndiswrapper that came on the liveCD (the version is 1.8 I believe). 

at the command prompt I entered:
```

dandelion@dandelion-desktop$sudo ndiswrapper -i BLKWGU.inf
```

but when listing the drivers with
```

dandelion@dandelion-desktop$sudo ndiswrapper -l
```

I get

```

Installed ndis drivers:
blkwgu  invalid driver! 
```

I read on another site, that I needed the latest ndiswrapper - I tried to build this from source, but get a "can't find kernel build files" error. 

Does anyone have any ideas?

Cheers
Bithika

---

### Post by wieman01 on 2006-10-08
Fairly common problem I think. When you deploy *.INF please ensure that all other driver files (*.CAB, *.BLABLA) are in the same directory as *.INF. Usually there are 3 or 4 files that come along with it. 

Once you have done that the error message should disappear. Seen it many time before.

---

### Post by bithika_mookherjee on 2006-10-09
Hi wieman01, and thanks for your quick reply.

The .CAB files definitely weren't in the same directory as the .INF - so that may well be the problem.

I'll give it a whirl tonight when I get home and let you know if it works.

Thanks and Best Wishes
Bithika

---

### Post by wieman01 on 2006-10-09
> **bithika_mookherjee said:**
> Hi wieman01, and thanks for your quick reply.

The .CAB files definitely weren't in the same directory as the .INF - so that may well be the problem.
That's possible. To be on the safe side, simply put every driver file there is in the same folder as *.INF. That should do. If not, you know where you can find help. :-)

---

### Post by bithika_mookherjee on 2006-10-09
Thanks - that worked, the driver is now installed correctly! :)

I just copied the entire folder containing the .INF file, plus all the other files, over to my desktop and ran ndiswrapper on that.

Fantastic! 

Best wishes
Bithika

---

