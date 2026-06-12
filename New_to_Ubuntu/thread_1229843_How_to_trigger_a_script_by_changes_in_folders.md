---
title: "How to trigger a script by changes in folders"
date: 2009-08-02
forum: New to Ubuntu
---

### Post by gwaar on 2009-08-02
I just wrote a simple script to mirror my music onto another partition of my machine, and I was wondering if there is some way of monitoring those folders for changes, and triggering the script to run again. Excuse me if this has come up - this is one of the few times I couldn't find an answer searching. 

Thanks.

---

### Post by ratcheer on 2009-08-02
I would use the find command, possibly using the -newer option to see if some file was added or updated at a later time than some known file. Then, still on the find command, use the -exec option to start your script.

Tim

---

### Post by benj1 on 2009-08-02
to have it run automatically you will either need to write a daemon or have cron (or anacron) run a check automatically.
another option would be to run the script on shut down.

---

### Post by llamabr on 2009-08-02
I like the unison application for this.  Why reinvent the wheel?

```
unison - A file-synchronization tool for Unix and Windows
```

---

### Post by benj1 on 2009-08-02
> **llamabr said:**
>   Why reinvent the wheel?

well he already has but to answer your question

---

