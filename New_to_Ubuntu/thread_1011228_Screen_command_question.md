---
title: "Screen command question"
date: 2008-12-14
forum: New to Ubuntu
---

### Post by DBrocks on 2008-12-14
Hi,

I'm sure this has a simple answer, but how can I make screen start something on a certain PID. I want to run rtorrent via screen with a PID of 30405. How can I do that? Thanks in advance!

---

### Post by stephanvaningen on 2008-12-14
Why would you want a process to run with a specifically pre-defined PID? (*By the way, AFAIK, a PID is a sequential number assigned to a new process starting in the system.*)

---

### Post by DBrocks on 2008-12-14
Because I want to start rtorrent at night and then kill it before i wake up, from a Bash script. I could probably use AWK to seperate the PID from ps -ef | grep rtorrent and then kill it.

---

### Post by taurus on 2008-12-14
You can kill a process with the name too.

```
killall rtorrent
```

---

### Post by DBrocks on 2008-12-14
Thanks! killall worked.

---

### Post by scorp123 on 2008-12-14
> **taurus said:**
> You can kill a process with the name too.

```
killall rtorrent
``` "pkill" works the same way and can work with wildcards too ... ```
pkill torrent
```  ... that should kill anything that has the sequence "...torrent..." in its name.

---

