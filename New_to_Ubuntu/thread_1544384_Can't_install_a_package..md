---
title: "Can't install a package."
date: 2010-08-02
forum: New to Ubuntu
---

### Post by wheelern on 2010-08-02
Ok, I'm trying to install davmail to use with Thunderbird. Everything has seem to have gone smoothly. I downloaded the .deb from sourceforge, which was easy enough. However, when I try to install the package, I get an error message that says some other software management tool is already running. The problem is, nothing is running, just chrome and the package installer. I even go into the system monitor to check if something is running in the background, but neither Synaptic, aptitude, or any other sort of software manager is running. Am I missing something in the system monitor? What can I do?

Thanks, in advance, for your help.

---

### Post by sahabcse on 2010-08-02
paste the o/p of 

#ps

---

### Post by wheelern on 2010-08-02
sorry... #ps?

---

### Post by TheNerdAL on 2010-08-02
> **wheelern said:**
> sorry... #ps?

Type that in the terminal and hit enter. :)

---

### Post by wheelern on 2010-08-02
PID TTY          TIME CMD
 1694 pts/0    00:00:00 bash
 2628 pts/0    00:00:00 ps

This what you're looking for?

---

### Post by kwacka on 2010-08-02
The command ```
ps -A
``` will give a fuller picture

---

### Post by sandyd on 2010-08-02
if your very sure nothings running...
run
```

sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock

```could have been a stale lock

---

### Post by linux18 on 2010-08-02
fix everything related to synaptic:

```

sudo killall synaptic
sudo killall aptitude
sudo killall mintinstall
sudo killall software-center
sudo rm /var/lib/dpkg/lock
sudo rm /var/cache/apt/archives/lock
sudo rm /var/lib/apt/lists/partial/* |
sudo rm /var/cache/apt/*.bin 
sudo dpkg --purge $(dpkg -l |grep  ^rc |awk '{print $2}' | tr '\012' ' ')
sudo apt-get -f install 
sudo apt-get clean 
sudo apt-get autoclean 
sudo apt-get autoremove 
sudo apt-get update 
sudo apt-get --fix-broken upgrade 

```

---

