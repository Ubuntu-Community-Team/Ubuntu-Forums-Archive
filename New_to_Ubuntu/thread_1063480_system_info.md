---
title: "system info"
date: 2009-02-07
forum: New to Ubuntu
---

### Post by downinit_xyz on 2009-02-07
Is there any specific location in Kubuntu where I can go to view the computer profile, as in the installed RAM, processor speed, hard drive space, etc.  This info is easy to find in windows and osx, but I cannot seem to locate it in Kubuntu.
Thank you

---

### Post by taurus on 2009-02-07
From a terminal, type

```
sudo lshw
```
If you get command not found, install it--lshw.

---

### Post by hyper_ch on 2009-02-08
I prefer
```

sudo lshw -html > ~/Desktop/hardware.html

```

---

### Post by HavocXphere on 2009-02-08
There is a hardware info tool under Applications->System.

Can't tell you the name cause I've got 2 installed and can't remember which one was installed by default and which one I installed myself.:shock:

---

### Post by carml on 2009-02-08
I suppose that under Xubuntu there's too,go on System->Administration->System monitor. :)

---

### Post by mkvnmtr on 2009-02-08
There is a program in the package manager you can download. Sysinfo. It seems to give me the most accurate info and in a form that is easy to understand.

---

### Post by houstonbofh on 2009-02-08
I really like lshw-gtk as it is lean, and easy to navigate.  I install it on all my systems.  'sudo apt-get install lshw-gtk'  You can also use it from the command line as it depends on lshw.

---

