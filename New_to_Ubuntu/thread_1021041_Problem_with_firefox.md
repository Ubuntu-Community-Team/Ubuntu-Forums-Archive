---
title: "Problem with firefox"
date: 2008-12-24
forum: New to Ubuntu
---

### Post by midgetwithamatch on 2008-12-24
I was recently ran out of room on my hard drive on my laptop and started encountering this problem when I start Firefox. When ever I start Firefox it complains about 

"Could not initialize the browser's security component. The most likely cause is problems with files in your browser's profile directory. Please check that this directory has no read/write restrictions and your hard disc is not full or close to full. It is recommended that you exit the browser and fix the problem. If you continue to use this browser session, you might see incorrect browser behaviour when accessing security features."

I have made sufficient room on my computer now with some ten gigs free at the moment and made sure the /home/user/.mozilla/ has 777  permissions. Whenever I access a https website Firefox crashes with no error message. Any help is appreciated. Oh and I've also done sudo apt-get purge  firefox then reinstalled and still comes up with the same thing.

---

### Post by taurus on 2008-12-24
Can you post the output of this command from a terminal?

```
df -h
```

---

### Post by midgetwithamatch on 2008-12-24
```
/dev/sda1              26G  3.5G   21G  15% /
tmpfs                 235M     0  235M   0% /lib/init/rw
varrun                235M  116K  235M   1% /var/run
varlock               235M     0  235M   0% /var/lock
udev                  235M  2.7M  233M   2% /dev
tmpfs                 235M  408K  235M   1% /dev/shm
lrm                   235M  2.0M  233M   1% /lib/modules/2.6.27-9-generic/volatile
/dev/sda3              47G   30G   15G  67% /home
```

---

### Post by taurus on 2008-12-24
What does your ~/.mozilla/firefox/profiles.ini look like?

```
cat ~/.mozilla/firefox/profiles.ini
```

---

### Post by midgetwithamatch on 2008-12-24
```
[General]
StartWithLastProfile=1

[Profile0]
Name=default
IsRelative=1
Path=0kudhiu9.default

[Profile1]
Name=Jeromy
IsRelative=1
Path=1ezanlzv.Jeromy
Default=1

```

---

