---
title: "Error when opening synaptic pacakge manager?"
date: 2010-09-01
forum: New to Ubuntu
---

### Post by ColdVerge on 2010-09-01
Sorry if I posted this in the wrong forum or whatever...

OK when I open synaptic package manager, it says:

An error occured

E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What does this mean and how can I fix it? Thanks :D

---

### Post by Smart Viking on 2010-09-01
I don't know exactly what the error means, but it do suggest you to run a command.

Open the terminal(Applications->accessories->terminal) and paste the following command and press enter, write the password when prompted and report back here what happens.

```
sudo dpkg --configure -a
```

:)

---

### Post by ColdVerge on 2010-09-01
Hi and thanks for your help. It said:

dpkg: dependency problems prevent configuration of tzdata-java:
 tzdata-java depends on tzdata (= 2010l-0ubuntu0.9.10); however:
  Package tzdata is not installed.
dpkg: error processing tzdata-java (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata-java

---

### Post by oldos2er on 2010-09-01
Try ```
sudo apt-get update && sudo apt-get install tzdata && sudo dpkg --configure -a
```

---

### Post by ColdVerge on 2010-09-02
Thanks a lot :)

---

