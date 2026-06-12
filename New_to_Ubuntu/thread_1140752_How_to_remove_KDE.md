---
title: "How to remove KDE?"
date: 2009-04-27
forum: New to Ubuntu
---

### Post by doctorbighands on 2009-04-27
I originally installed Ubuntu on my laptop. Later, I installed KDE as an addition. I'd like to free up some hard drive space, but I don't know how to remove KDE and all of its components.

Any help is appreciated. Thank you!

---

### Post by llamabr on 2009-04-28
How about:

```
sudo apt-get remove kde
```

and then

```
sudo apt-get autoremove
```

and then

```
sudo apt-get clean
```

---

### Post by wizard10000 on 2009-04-28
danielrmt posted this a couple days ago and I thought it was pure gold.

[http://www.psychocats.net/ubuntu/puregnome](http://www.psychocats.net/ubuntu/puregnome)

If you've got Ubuntu and just want KDE removed you can remove the "&& sudo apt-get install ubuntu-desktop" from the end of that long apt line but it won't hurt anything if you leave it in there.

Hope this helps -

---

