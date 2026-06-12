---
title: "sort command"
date: 2010-11-19
forum: New to Ubuntu
---

### Post by ibizatunes on 2010-11-19
180k	/home/test
1G	/home/el
20k	/home/test2
18k      /home/te      
14k      /home/jo
4k       /home/dave

i want to sort on the home directory so that it alphabetical and has the disk usage next to it

cat /tmp/file_useage | sort -t +2n

for love nor money i cant see want the problem is (its friday)
can someone help

---

### Post by gmargo on 2010-11-19
```

sort -k 2

```

---

