---
title: "fusesmb owned me hard"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by boast on 2007-03-16
Not knowing how to get fusesmb working, I did some sort of mout thing on /media/network . Well, I couldn't open the directory, so I try deleting it. After doing 'rm -rf /media/network' I had to learn the hard way that it would in turn delete everything I had on my media server. And now attempting to recover those files, I still don't know how to remove /media/network. thanks for any help. (/rant too lol)

---

### Post by revertex on 2007-07-10
better later than never...

```
killall fusesmb
```

---

### Post by reset3x on 2007-07-19
> **boast said:**
> Not knowing how to get fusesmb working, I did some sort of mout thing on /media/network . Well, I couldn't open the directory, so I try deleting it. After doing 'rm -rf /media/network' I had to learn the hard way that it would in turn delete everything I had on my media server. And now attempting to recover those files, I still don't know how to remove /media/network. thanks for any help. (/rant too lol)

Disconect from your network then:

```
sudo rm -r /media/network
```

Good fusesmb tutorial here:

[http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu](http://ubuntuforums.org/showthread.php?t=304131&highlight=xubuntu)

---

