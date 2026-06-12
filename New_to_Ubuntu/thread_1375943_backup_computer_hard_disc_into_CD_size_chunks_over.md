---
title: "backup computer hard disc into CD size chunks over network"
date: 2010-01-08
forum: New to Ubuntu
---

### Post by benfindlay on 2010-01-08
Hi all. I've been racking my brains trying to remember how to do this with no luck!

What I want to do is back up the hard disc of 1 machine (using a live cd) with dd and send it over the network with nc, but I also need to split the files into CD sized chunks (say 660 MB). I've used commands such as: > dd if=/dev/sda1 | nc 192.168.1.5 9000on the machine I am backing up, and > nc -l -p 9000 | split -d -b 660m image.dd.on the machine I am backing up onto. I have tried various combinations of these commands on both machines, but can't quite seem to get the syntax right. Can anyone point me in the right direction?

Cheers

Ben

---

### Post by gsmanners on 2010-01-08
I think you may just be missing the INPUT parameter for the split command (I assume image.dd. is your PREFIX):

```
nc -l -p 9000 | split -d -b 660m - image.dd.
```

---

