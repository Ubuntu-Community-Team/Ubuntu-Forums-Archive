---
title: "Tasks start but end without really starting"
date: 2010-05-31
forum: New to Ubuntu
---

### Post by Ken Wynne on 2010-05-31
I'm a beginner. Ubuntu 9.10. Installed from a CD I created from download. 

My problem is tasks or apps appear to start as I can see hem along the bottom but they just end without an error message or the task actually starting. Examples include Ubuntu Software Center, System > Admin> Printing and Apturl. At the very bottom of the screen it says Starting Printing or Starting Ubuntu Software but then it ends and no pane or window opens.

Ideas? Please and thanks !!

---

### Post by Ozymandias_117 on 2010-06-01
Open a terminal and try to start them from there, then it should give off error messages.

Printing is ```
system-config-printer
```

Ubuntu Software Center is ```
/usr/bin/software-center
```

---

### Post by Ken Wynne on 2010-06-01
Thank you for responding. I ran each command and here is what it returned. Looks like I'm missing modules...wonder how that happened and how many more are missing.

super@super-laptop:~$ system-config-printer
Traceback (most recent call last):
  File "/usr/share/system-config-printer/system-config-printer.py", line 30, in <module>
    from timedops import *
  File "/usr/share/system-config-printer/timedops.py", line 20, in <module>
    import gobject
ImportError: No module named gobject

super@super-laptop:~$ /usr/bin/software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 25, in <module>
    import pygtk
ImportError: No module named pygtk

---

### Post by Ozymandias_117 on 2010-06-01
Try ```
sudo aptitude install python-gobject python-gtk2
``` and see if that is what you need

---

### Post by Ken Wynne on 2010-06-01
Ran the code line. Everything ran okay, no errors.

Ran system-config-printer in a terminal. Exact same error messages.

Would a fresh install with 10.04 be an idea? I now its extreme...but I nothing really on the system.

Thank you

---

### Post by Ozymandias_117 on 2010-06-02
You can try this one, or reinstall. It sounds like something weird happened, so that may make sense, it's up to you.

```
sudo aptitude install libpolkit-gobject-1-0 libdevkit-power-gobject1
```

---

### Post by Vishal Agarwal on 2010-06-02
if you are planning to installing again, check the CD for defects, before you start install.

---

### Post by Ken Wynne on 2010-06-02
Okay, I loaded 10.04 and everything appears to be working. I can start printers, software centre etc.

Thank you for the help......

Given my experience I'll be back. Thanks again

---

