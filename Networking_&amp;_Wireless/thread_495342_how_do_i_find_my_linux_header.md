---
title: "how do i find my linux header"
date: 2007-07-07
forum: Networking &amp; Wireless
---

### Post by grandpa2390 on 2007-07-07
i need it for [http://ubuntuforums.org/showthread.php?t=31926](http://ubuntuforums.org/showthread.php?t=31926)

---

### Post by Vajra Vrtti on 2007-07-07
Enter this command in a terminal:
```
uname -r
```The answer is something like:
> 2.6.20-16-generic
Then the corresponding package for the headers is:
> linux-headers-**2.6.20-16-generic**

---

