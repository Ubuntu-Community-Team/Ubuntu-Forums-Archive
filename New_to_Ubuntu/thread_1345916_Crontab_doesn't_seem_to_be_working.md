---
title: "Crontab doesn't seem to be working"
date: 2009-12-04
forum: New to Ubuntu
---

### Post by henriquelm on 2009-12-04
Hello there, I setup a few commands on "crontab -e" to be executed at a certain day and time, but it doesn't seem to be executing the commands at all.

What should I do to solve this?

Thanks

---

### Post by fatality_uk on 2009-12-04
> **henriquelm said:**
> Hello there, I setup a few commands on "crontab -e" to be executed at a certain day and time, but it doesn't seem to be executing the commands at all.

What should I do to solve this?

Thanks

What are the commands? Easy thing to try is simply have an entry that creates a new file in your home/desktop directory. if that works then cron is working

---

### Post by bodhi.zazen on 2009-12-04
IMO the most common problem people have with crontab is that it (corntab) runs in a minimal shell (sh) with a minimal of environmental variables.

Use the full path to commands, for example, use /bin/cp rather then cp ...

Also, simply stating that it is not working makes it difficult for anyone to help your. What is it you are wanting to do ? What entry did you add in crontab ? are you getting an error message ?

---

