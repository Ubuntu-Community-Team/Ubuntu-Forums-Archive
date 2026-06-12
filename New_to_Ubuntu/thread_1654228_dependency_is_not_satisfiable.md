---
title: "dependency is not satisfiable"
date: 2010-12-28
forum: New to Ubuntu
---

### Post by mynameisntjonas on 2010-12-28
I'm trying to install skype on my dell mini using an older version of ubuntu. I bought i 2 christmases ago. When i get to the package installer it says dependency is not satisfiable. What should i do?

---

### Post by karthick87 on 2010-12-28
Welcome to ubuntuforums :)

Run the following in your terminal,
```
sudo apt-get install -f
``````
sudo dpkg --configure -a
``````
sudo apt-get update && sudo apt-get upgrade
```

Also look at the following link for skype installation,
[https://help.ubuntu.com/community/Skype](https://help.ubuntu.com/community/Skype)

---

### Post by mynameisntjonas on 2010-12-28
umm it says

error: dependency is not satisfiable: libasound2

---

### Post by karthick87 on 2010-12-28
Try,
```
sudo apt-get install libasound2
```

---

### Post by mynameisntjonas on 2010-12-28
it still says dependency is not satisfiable for the same thing

---

### Post by karthick87 on 2010-12-28
What version of ubuntu you are using?

---

### Post by karthick87 on 2010-12-28
If you are using ubuntu 10.10,then edit sources.list
 ```
sudo gedit /etc/apt/sources.list
```Uncomment the following
> 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner[B]
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) maverick partner[/B]Now run the following in terminal,
```
sudo apt-get update 
``````
sudo apt-get install skype
```

---

### Post by theozzlives on 2010-12-28
Your version of Ubuntu may be to old. If it's 9.04 or earlier it is to old.

---

### Post by Joe of loath on 2010-12-28
IIRC the dell minis came with 8.04, which doesn't work with skype.

---

