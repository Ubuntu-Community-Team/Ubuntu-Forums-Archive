---
title: "Ubuntu software Center not working"
date: 2009-11-27
forum: New to Ubuntu
---

### Post by vamper on 2009-11-27
I have Ubuntu  9.10 installed on 2 computers in my home, one is a acer ASPIRE 5100 laptop, and recently when I try to choose the software center option under the applications tab it tries to start up but then stops, I have checked my authorizations in case something changed after my last update, but all appears as it should, am I missing something else.

*It is not the notebook version installed on the laptop just the standard version, with a SE plugin added on for apperances.

TIA

---

### Post by themusicalduck on 2009-11-27
Try typing ```
software-center
``` into a terminal and see if it gives any error messages.

---

### Post by vamper on 2009-11-27
Well this is the result


```
hell@hell-laptop:~$ software-center
Traceback (most recent call last):
  File "/usr/bin/software-center", line 25, in <module>
    import pygtk
ImportError: No module named pygtk
```

---

### Post by Virtual Liberty on 2009-11-27
Looks like you are missing some of the Python modules.

```
sudo apt-get install python-gtk2

```

---

### Post by vamper on 2009-11-27
Ok tried that and this is what I am getting now

```
hell@hell-laptop:~$ sudo apt-get install python-gtk2
[sudo] password for hell: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
python-gtk2 is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
hell@hell-laptop:~$ 
```

---

### Post by wilee-nilee on 2009-11-27
A mod posted a couple of days ago about it being a bit of a problem. Personally I just install from the terminal or synaptic. The software center is nice for a preview of possibilities within categories but I never use it or the previous add remove.

---

### Post by vamper on 2009-12-06
I reverted back to 9.04 jaunty jackalope, and all is fine, I'll stay with this version for now till the bugs get worked out of the 9.10 64 bit version.

---

