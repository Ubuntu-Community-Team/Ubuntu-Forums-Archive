---
title: "List of the last programs installed"
date: 2010-10-21
forum: New to Ubuntu
---

### Post by A_M_S on 2010-10-21
Hello

Anybody know how to get a list of the last programs installed on Ubuntu? (like the last 10 programs installed )

Note that i'm NOT asking for a list of ALL programs installed (dpkg -l)

Thanks

---

### Post by godspeedmav on 2010-10-21
I'm also a learner but this is what I could find, although I may be wrong from what you are seeking;

```
ls -lt /var/cache/apt/archives/ | tail
```

---

### Post by jmszr on 2010-10-22
A_M_S,

Try Synaptic Package Manager > File > History.

---

### Post by A_M_S on 2010-10-22
Thanks for the replies :)

Anybody know if there is a list of the applications installed by dpkg or compiled by source? 

Thank you

---

### Post by drs305 on 2010-10-22
For dpkg (the list also lists packages installed by Synaptic), look at System, Administration, Log File Viewer, dpkg.log or run:
```
grep " installed" /var/log/dpkg.log | tail
```

---

### Post by Crazedpsyc on 2010-10-22
You could check the bash history for a list of the commands entered if it was compiled recently and from bash.
```
history
```

---

### Post by Crazedpsyc on 2010-10-22
You could check the bash history for a list of the commands entered if it was compiled recently and from bash.
```
history
```

Ooops, double post! please remove!

---

### Post by A_M_S on 2010-10-22
Tnx again for the replies!

---

