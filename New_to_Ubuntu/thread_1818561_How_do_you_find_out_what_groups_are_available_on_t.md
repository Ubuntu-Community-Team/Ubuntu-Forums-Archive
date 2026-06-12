---
title: "How do you find out what groups are available on the server?"
date: 2011-08-04
forum: New to Ubuntu
---

### Post by 007casper on 2011-08-04
How do you find out what groups are available on the server?

---

### Post by Wim Sturkenboom on 2011-08-05
```

cat /etc/group

```

---

### Post by bodhi.zazen on 2011-08-05
Or if you wish to get fancy 

```
awk 'BEGIN {FS=":"}; {print $1}' | sort | less
```

less is nice as the output may otherwise scroll off your console (on a server).

alternately you can pipe it to a file, but, why bother ? 

```
less /etc/group
```

press q to exit less, use the arrow keys to scroll up and down in the file.

---

