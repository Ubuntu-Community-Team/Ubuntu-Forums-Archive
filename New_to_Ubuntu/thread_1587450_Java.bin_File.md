---
title: "Java.bin File"
date: 2010-10-03
forum: New to Ubuntu
---

### Post by Benup on 2010-10-03
Just downloaded java 6 and the file name is.

JDK-6u21-Linux-i586.bin

So i went to the terminal and put

./JDK-6u21-Linux-i586.bin and then tried it with Sudo infront but still get the same problem command not found or no such file or directory.

Anyone know how to sort this as i need it to make another program run

---

### Post by TeoBigusGeekus on 2010-10-03
You have to make the file executable first
```
chmod +x JDK-6u21-Linux-i586.bin
```

---

### Post by Benup on 2010-10-03
> **TeoBigusGeekus said:**
> You have to make the file executable first
```
chmod +x JDK-6u21-Linux-i586.bin
```

so i would put into the terminal

chmod +x JDK-6u21-Linux-i586.bin
./JDK-6u21-Linux-i586.bin

Edit: Tried that but is still saying no such file or directory

---

### Post by TeoBigusGeekus on 2010-10-03
> **Benup said:**
> so i would put into the terminal

chmod +x JDK-6u21-Linux-i586.bin
./JDK-6u21-Linux-i586.bin
```
chmod +x JDK-6u21-Linux-i586.bin
```
enter and then
```
./JDK-6u21-Linux-i586.bin
```

---

### Post by Benup on 2010-10-03
> **TeoBigusGeekus said:**
> ```
chmod +x JDK-6u21-Linux-i586.bin
```
enter and then
```
./JDK-6u21-Linux-i586.bin
```

Still not working, maybe im missing something?? just says no such file or directory

---

### Post by johanbove on 2010-10-03
All the help you can imagine on changing JAVA on ubuntu can be found here:
[http://sites.google.com/site/easylinuxtipsproject/java#TOC-Inform-the-system-and-make-the-new-](http://sites.google.com/site/easylinuxtipsproject/java#TOC-Inform-the-system-and-make-the-new-)

---

### Post by Dustin2128 on 2010-10-03
doesn't chmod 755 make it executable as well?

---

### Post by TeoBigusGeekus on 2010-10-03
Are you sure you're in the correct directory?

---

### Post by gandaran on 2010-10-03
install sun-java from the system repositories, it's easier!
enable the archive.canonical partner repository in software sources then update the package list, now you will be able to find sun-java in synaptic or software center.
or install using apt-get
```
sudo apt-get install sun-java6-plugin
```

---

### Post by Benup on 2010-10-03
> **gandaran said:**
> install sun-java from the system repositories, it's easier!
enable the archive.canonical partner repository in software sources then update the package list, now you will be able to find sun-java in synaptic or software center.
or install using apt-get
```
sudo apt-get install sun-java6-plugin
```

Thanks man that answer helped me. Also thanks all who posted sorry if it was a stupid question but im new to Ubuntu.

~Ben

---

### Post by Dustin2128 on 2010-10-03
> **gandaran said:**
> 
```
sudo apt-get install sun-java6-plugin
```
*facepalm*

---

