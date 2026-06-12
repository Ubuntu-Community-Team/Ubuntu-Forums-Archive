---
title: "How to install a .sh file?"
date: 2009-04-20
forum: New to Ubuntu
---

### Post by yeehi on 2009-04-20
I would like to use a recent version of BOINC in order to use CUDA to help the hunt for aliens.

I have downloaded this file, but package manager doesn´t kick into life when I double click:

boinc_6.6.20_x86_64-pc-linux-gnu.sh

What should I do?

---

### Post by steve101101 on 2009-04-20
sh ./filename.sh

---

### Post by Sef on 2009-04-20
Read [How to Install Anything in Ubuntu]("http://amitech.50webs.com/installing/index.php.html").

---

### Post by yeehi on 2009-04-20
```
sh ./boinc_6.6.20_x86_64-pc-linux-gnu.sh
sh: Can't open ./boinc_6.6.20_x86_64-pc-linux-gnu.sh

```

```

cd /home/yeehi
sh ./boinc_6.6.20_x86_64-pc-linux-gnu.sh
use /home/neil/Downloads/BOINC/run_manager to start BOINC

```

Thank you for that idea, but it didn´t go... but it did ask me to run_manager...

---

### Post by steve101101 on 2009-04-20
> **yeehi said:**
> ```
sh ./boinc_6.6.20_x86_64-pc-linux-gnu.sh
sh: Can't open ./boinc_6.6.20_x86_64-pc-linux-gnu.sh

```

Thank you for that idea, but it didn´t go...

are you in the correct directory

---

### Post by steve101101 on 2009-04-20
for example if the sh file is on the desktop:

```

sh /home/username/Desktop/FILENAME.sh

```

---

### Post by yeehi on 2009-04-20
Oh, sorry, you were too quick. I changed directory, as you suggested.

I have now downloaded the BOINC Manager from [here]("http://packages.debian.org/sid/amd64/boinc-manager/download").

It installed well, but it doesn´t find the BOINC client, I think, which is the file I am trying to get going...

Instructions on how to install BOINC are here.

(The simplest way is to just add it from synaptic, but I want to use CUDA, so want more recent code.)

---

### Post by steve101101 on 2009-04-20
glad i could help.

---

