---
title: "cannot access my trash"
date: 2009-10-24
forum: New to Ubuntu
---

### Post by fitgene on 2009-10-24
i cannot move any files to the trash. when i try it says cannot move to trash delete the file permanently. plz help me guys. wats the problem??????

---

### Post by mapes12 on 2009-10-24
[http://ubuntuforums.org/showthread.php?t=898573](http://ubuntuforums.org/showthread.php?t=898573)

---

### Post by fitgene on 2009-10-24
problem not yet solved. when i delete it doesnt go to the trash. why is it?

---

### Post by OpenGuard on 2009-10-24
```
sudo apt-get reinstall nautilus

```

Have had this problem twice ..

---

### Post by bluefrog on 2009-11-01
I have the same problem.

nautilus doesn't want me to move things to the trash if it not in my user's folder.

everything in /home/user is moved to the trash correctly.

Now if I create a folder in /home and give my user rwx rights, then I create a file in the folder and I am unable to move it to the trash. Nautilus tells me it can only delete it totally.

can someone confirm so I may open a bug report.

sudo mkdir /home/test
sudo chown $USER.$USER /home/test
touch /home/test/test-file

try removing test-file with nautilus (move to trash)

---

