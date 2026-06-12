---
title: "firefox trouble..."
date: 2010-12-19
forum: New to Ubuntu
---

### Post by napoleon3665 on 2010-12-19
hey guys, so i got a little bit of an issue here, i just recently reinstalled lucid, (via live cd, not wubi) and im having trouble with firefox. i can only go to some websites such as facebook, and ubuntu.com, but when i try to go to google, yahoo, aol, and some other sites...it tells me that there was a "problem loading this page". so, what do i do to fix this? thanks.

---

### Post by cariboo on 2010-12-19
Can you ping Google by name?

```
ping www.google.com
```

Can you ping Google by ip address?

```
ping 72.14.213.99
```

If you can ping by number and not by name, you may have a DNS problem, could you paste the output of:

```
cat /etc/resolv.conf
```

In your next post.

---

### Post by wojox on 2010-12-19
Also try looking at [Solution #5]("http://firefox-tutorials.blogspot.com/2010/05/common-issues-solutions.html")

---

