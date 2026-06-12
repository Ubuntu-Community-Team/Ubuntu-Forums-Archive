---
title: "clear cached memory scripting help"
date: 2009-02-21
forum: New to Ubuntu
---

### Post by rburkartjo on 2009-02-21
need some help and i know the following is wrong. i first need to switch to root either sudo su or sudo -i and then run the second line. see below
 sudo su                                                                   echo 3 > /proc/sys/vm/drop_caches

tks/cheesemaker

---

### Post by unutbu on 2009-02-22
Try```

echo 3 | sudo tee /proc/sys/vm/drop_caches
```

---

### Post by rburkartjo on 2009-02-24
tks un that did the trick/cheesemaker

---

