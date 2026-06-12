---
title: "How to limit my internet bandwidth usage"
date: 2006-10-10
forum: Networking &amp; Wireless
---

### Post by DjDarkman on 2006-10-10
I have a small home network here made of 3 computers ,and one has internet connection.Can someone suggest a good way or program to limit the internet bandwitdh usage?because when I download something my caulages internet becomes too slow.

---

### Post by Jussi Kukkonen on 2006-10-10
trickle is usable if you can start the downloads from the command line.

Something like 
```
trickle -d 20 wget http://url.org/file
```

---

### Post by mips on 2006-10-10
[http://www.linux.com/howtos/ADSL-Bandwidth-Management-HOWTO/index.shtml](http://www.linux.com/howtos/ADSL-Bandwidth-Management-HOWTO/index.shtml)
[http://www.linux.com/howtos/Bandwidth-Limiting-HOWTO/index.shtml](http://www.linux.com/howtos/Bandwidth-Limiting-HOWTO/index.shtml)

---

