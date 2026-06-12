---
title: "server bandwidth spikes"
date: 2008-10-16
forum: Networking &amp; Wireless
---

### Post by prem1er on 2008-10-16
I'm using gkrellm to monitor my home server.  Over the past week or so I have been noticing spikes in bandwidth on the server and a terrible lag over the command line.  What can I use to monitor individual processes to determine what is actually causing the problem?

---

### Post by prem1er on 2008-10-16
Ok I found my own answer to that.  Anyone interested use a lightweight program called nethogs (its in the repos).  Now here is my problem.  I'm looking at the out put for nethogs and it is showing me me that every time there is a spike this is the output for the program causing it.

```

PID = 0
Program = Unknown
User = root

```

Any ideas?  Thanks.

---

### Post by prem1er on 2008-10-17
bump

---

### Post by prem1er on 2008-10-21
bump

---

