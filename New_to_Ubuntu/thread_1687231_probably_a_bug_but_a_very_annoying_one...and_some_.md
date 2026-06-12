---
title: "probably a bug but a very annoying one...and some strange firefox behavior"
date: 2011-02-13
forum: New to Ubuntu
---

### Post by werty2010 on 2011-02-13
i was playing poker at facebook(zyn@) and between random time periods firefox just seemed to stop working and freezed.so i had to kill it from the system monitor.
in one of those moments while i was trying to kill firefox ,i pressed kill and the 2 firefox processes disappeared but the sounds from the game were still there.... which led me to realize that despite my efforts firefox wasnt killed.
could someone explain me why is this happening and if there is a way to fix it?

---

### Post by linuxsyst on 2011-02-13
Open the terminal write ```
ps -ax
```
look if a process is still there if it is
write ```
kill -9 (number of the process)
```
Good Luck

---

### Post by linuxsyst on 2011-02-13
Yes and it is because in Firefox was a bug that wasn't fixed and you killed it the wrong way you need to do it from the terminal

---

