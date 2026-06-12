---
title: "Permissions"
date: 2010-05-03
forum: New to Ubuntu
---

### Post by joeman225 on 2010-05-03
I want to make certain files/folders/programs only accessible by me, and I was wondering - if I right click on a file, go to "Properties" and to the "Permissions" tab and set "Access" for "Group" and Other" to "None", will this do the trick in terms of protecting and securing these files?

What happens if I do the same to a program like Firefox?

Thanks in advance for your help.

---

### Post by Drenriza on 2010-05-03
Try look here.
 
It should answer your question.
If you still have problems, i will gladly help.
 
[http://ubuntuforums.org/showthread.php?t=1453342&page=2](http://ubuntuforums.org/showthread.php?t=1453342&page=2)
 
page 1 permissions
page 2 command to change permissions

---

### Post by joeman225 on 2010-05-03
Thanks for your answer, unfortunately, I don't think that helps me in answering my question. I would just like to know if the specific steps I took explained in my first post were enough to secure my files and programs.

---

### Post by Drenriza on 2010-05-03
For directory.
 
go to a terminal, go to the path of the folder you want to secure.
 
```
chmod 744 (filename)
```
example
```
chmod 744 /test.directory
```
 
others can see the directory but cannot access them, because they dont have the
execute option.
 
for files, such as txt files
```
chmod 644 (filename)
```
example
```
chmod 644 test.txt
```
 
groups and others can then read the files, but cannot change them.
 
Does this solve your issue?

---

### Post by lovinglinux on 2010-05-03
I wouldn't change permission of Firefox profile folder (~/.mozilla/firefox), since Firefox needs full access to your home. I'm not sure about the "None" option tho. If you want to protect Firefox and other applications from accessing your home directory, use AppArmor.

Anyway, if you want to play with such permissions, I would experiment on a Virtual Machine, because if you screw up you can just reset the VM to a previous snapshot or discard it entirely without affecting your system. Once your comfortable enough that the setup you want won't cause any problems, then apply to your system.

---

