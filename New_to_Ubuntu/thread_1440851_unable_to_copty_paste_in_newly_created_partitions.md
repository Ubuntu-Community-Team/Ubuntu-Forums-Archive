---
title: "unable to copty paste in newly created partitions"
date: 2010-03-28
forum: New to Ubuntu
---

### Post by jainsr on 2010-03-28
Hi, 

i just installed Ubuntu in my laptop and had made 4 partitions  but the problem is that am not able to do any cut copy or past. it shows an error" the folder cannot copied bcaz u dont have permissions to create it in the destinatiion" pls help me wat to do...

---

### Post by s_ø on 2010-03-28
Hi. You need to change permissions.
See this documentation for general introduction to filepermissions [https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions).
For a tutorial on mounting your partitions and setting permissions [http://psychocats.net/ubuntu/mountlinux](http://psychocats.net/ubuntu/mountlinux)

---

### Post by Paqman on 2010-03-28
By default you'll have permission to create new folders within your home folder, but not anywhere else on the system. This is an important security feature.

So if you just want to create a folder for storing files for your own use, create it inside your home folder and it'll work perfectly.

---

