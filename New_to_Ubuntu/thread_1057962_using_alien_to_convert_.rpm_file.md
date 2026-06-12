---
title: "using alien to convert .rpm file"
date: 2009-02-02
forum: New to Ubuntu
---

### Post by hoosiergsp on 2009-02-02
I have tried to convert a .rpm file to .deb with no luck. I installed alien with no problem, but when I enter the command:
"sudo alien cnijfilter-ip2500series-2.70-1.i386.rpm"
The terminal tells me the "file not found". 
I have downloaded the file to my desktop. Is there a step or sequence that I am not doing correct?
I can usually solve my problems through the forum search but this one has me miffed. It has to simpler than this.
All help appreciated.

---

### Post by taurus on 2009-02-02
Did you remember to change to your ~/Desktop first before you ran that command?

```
cd ~/Desktop
sudo alien cnijfilter-ip2500series-2.70-1.i386.rpm
```

---

### Post by smothpocket on 2009-02-02
Are you sure that you are in the correct directory?

If not then type
cd ~/Desktop

and then run your command

---

### Post by hoosiergsp on 2009-02-02
That worked. Thanks very much.

---

