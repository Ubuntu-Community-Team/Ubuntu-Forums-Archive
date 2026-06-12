---
title: "Synaptic package manager dpkg error"
date: 2009-01-26
forum: New to Ubuntu
---

### Post by lonewolf1222 on 2009-01-26
I think something is wrong.If I try to open Synaptic package manager I get an error message saying
[I]
E:dpkg was interrupted, you must manually run 'dpkg --configure -a' to
correct the problem
E:_cache->open()failed,please report.
[/I]
Also I was trying to download limewire and every time I ran the package manager it said it was busy and could only run one task at a time, but I was not doing anything else. I have rebooted my computer and it satill says the same things

---

### Post by Tim Sharitt on 2009-01-26
Open a terminal and run
```
sudo dpkg --configure -a
```

---

### Post by cdtech on 2009-01-26
Try this then run the update manager:
```
kill -9 `pgrep update`
```
**UPDATED::.**
If you still get the error, use this command to list running processes:
```
ps -ax
```
If you find some update process running in the background use this command
to kill the process:
```
sudo kill <process number>
```
If you kill all update processes then try running:
```
sudo dpkg --configure -a && sudo apt-get -f install
```
Hope this helps ya.......

---

### Post by lonewolf1222 on 2009-01-26
Thanks guys!

---

