---
title: "delete locked directory"
date: 2009-02-14
forum: New to Ubuntu
---

### Post by jtmedin on 2009-02-14
I have a  locked directory  on my desktop.         Unable to   delete that directory & it sub directories & their contents. Whats the secret? TIA

---

### Post by kestrel1 on 2009-02-14
You need to do this in a terminal:
```
cd Desktop
```
Then type:```
sudo rm -r 'directoryname'
```

---

### Post by hyperyoda on 2009-02-14
> **jtmedin said:**
> I have a  locked directory  on my desktop.         Unable to   delete that directory & it sub directories & their contents. Whats the secret? TIA

Please post the command you are typing and the exact error message you receive.

Thanks.

Zach

---

### Post by geirha on 2009-02-14
If you want to delete it using the GUI, then hit Alt+F2 to get the run-dialog, and run « gksu nautilus ». An easier way is to install the package [nautilus-gksu](apt:nautilus-gksu), which will give you a new entry on the right-click menu of nautilus; go Places -> Home folder, right click the Desktop-folder and choose «open as administrator» ...

---

