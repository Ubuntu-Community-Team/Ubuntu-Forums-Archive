---
title: "Timestamp"
date: 2011-01-13
forum: New to Ubuntu
---

### Post by geohei on 2011-01-13
Hi.

I was sure to find an answer with Google, or man pages ... but no joy (strange)!

I need to get the timestamp out of the date command.

How can I do this?

By timestamp, I mean this here: 1294909373
This would be 13.01.2011 @ 03:02:53

Thanks!

---

### Post by sisco311 on 2011-01-13
The [Unix time]("http://en.wikipedia.org/wiki/Unix_time") (a.k.a timestamp or POSIX time) is the number of seconds since 1970-01-01 00:00:00 UTC.

```
date +'%s'
```
```
date -d '2011-01-13 09:02:53Z' +'%s'
```

See: ```
man date | less +/'%s'
```

---

### Post by geohei on 2011-01-13
Incredibly simple ... if you know it :)

Thanks a lot !!!

---

### Post by sisco311 on 2011-01-13
You're welcome!

Don't forget to mark the thread as [SOLVED].

---

