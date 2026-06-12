---
title: "Struugling with accessing the default directory of &quot;Foremost&quot;"
date: 2010-01-01
forum: New to Ubuntu
---

### Post by tennisdude818 on 2010-01-01
A program I was using apparantly crashed and I lost a ton of data that was xml (I think).  I used "Foremost" for the first time to recover any data that I could and it put all of the recovered data in "output" which I apparently need root privileges to access.  However, when I use "sudo i" in the terminal to give myself those privleges, it cannot find the directory anymore.  So I can either use my normal profile and be denied access or use root and simply not be able to find the directory.

---

### Post by cariboo on 2010-01-01
If the output directory is in your home directory, you just have to navigate to it, as when you run **sudo -i**, you start in root's home directory, the command you need would look something like this:

```
cd /home/<username>/output
```

substitute your user name for <username>.

You can also do it graphically, by pressing Alt-F2 and typing:

```
gksudo nautilus
```

The above command will start Nautilus in root mode, where you should be able to navigate to your home directory with a couple of clicks.

---

### Post by tennisdude818 on 2010-01-01
Thanks, I found it.  Of course the data I wanted was not there but I found the directory.

---

