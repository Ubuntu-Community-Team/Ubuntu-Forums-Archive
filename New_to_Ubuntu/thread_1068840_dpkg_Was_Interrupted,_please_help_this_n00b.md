---
title: "dpkg Was Interrupted, please help this n00b"
date: 2009-02-13
forum: New to Ubuntu
---

### Post by sierrabravo on 2009-02-13
I was running Add Programs, dl'ing to install wine among others, and Lo and Behold, power was interrupted.  When it came back on, I tried to continue where I left off but I am getting this message: dpkg was interrupted, you  must manually run 'dpkg --configure -a' to correct the problem.  I am so new to Ubuntu that I'm not sure how to "manually" run this...  please help, I will be back on in a few hours.  Thanks!!:confused::confused:

---

### Post by howefield on 2009-02-13
Open a terminal (applications > accessories > terminal) and type

```
sudo dpkg --configure -a
```

Enter your password when asked. Then type

```
sudo apt-get update
```

---

### Post by sierrabravo on 2009-02-13
> **howefield said:**
> Open a terminal (applications > accessories > terminal) and type

```
sudo dpkg --configure -a
```

Enter your password when asked. Then type

```
sudo apt-get update
```

COOL!  its working, ya learn something n00b everyday!:lolflag:
Thank you so much!

---

### Post by howefield on 2009-02-13
Kinda thought it might, you're welcome. :P

---

