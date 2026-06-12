---
title: "[SOLVED] Java SDK installation"
date: 2008-12-07
forum: New to Ubuntu
---

### Post by pradeepbp on 2008-12-07
I want to install java sdk on hardy. i downloaded the bin file from sun's site and extracted the files. now, i am unable to figure out how to make ubuntu choose this as my default java.

---

### Post by binbash on 2008-12-07
if you installed it, change it via 

sudo update-java-alternatives
(-l for the list -s select)

sample : 

sudo update-java-alternatives -s java-6-sun

---

### Post by lovelyvik293 on 2008-12-07
You don't have the extract the  .bin file.Just put the file in /opt folder or any other folder.Then by terminal go there and use these commands:-
```

chmod +x <name of the jdk>.bin
./<name of jdk>.bin

```

and to tell the ubuntu about the jdk.
Open the .bashrc file  and ad the path of the jdk bin folder to path variable 
```

gksudo gedit .bashrc

```

Add lines:-
```

PATH=$PATH:<Path to jdk>/bin

```

---

### Post by pradeepbp on 2008-12-07
> **binbash said:**
> if you installed it, change it via 

sudo update-java-alternatives
(-l for the list -s select)

sample : 

sudo update-java-alternatives -s java-6-sun

command: sudo update-java-alternatives -l, gives out the following error 

awk: cannot open /usr/lib/jvm/*.jinfo (No such file or directory)
jdk1.6.0_11 /usr/lib/jvm/jdk1.6.0_11


what's up ?

---

### Post by taurus on 2008-12-07
What happens when you run this command from a terminal?

```
sudo update-alternatives --config java
```

---

### Post by pradeepbp on 2008-12-09
[http://ubuntuforums.org/showpost.php?p=847269&postcount=1](http://ubuntuforums.org/showpost.php?p=847269&postcount=1)

the above link solved my problems. Anyway, thanx for all the guidance.

---

