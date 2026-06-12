---
title: "Java_path="
date: 2010-08-05
forum: New to Ubuntu
---

### Post by lumpie on 2010-08-05
I checked my java version - 

java version "1.6.0_18"
OpenJDK Runtime Environment (IcedTea6 1.8 ) (6b18-1.8-4ubuntu3)
OpenJDK Client VM (build 16.0-b13, mixed mode, sharing)

Can someone tell me exactly what the java path is? I tried 

JAVA_PATH=/usr/java/j2sdk1.6.0_18/bin

but apparently thats not right.

---

### Post by Res2216firestar on 2010-08-05
Try /usr/lib/jvm/java-6-openjdk/bin .

---

### Post by KdotJ on 2010-08-05
How come you need the path? How did you install your Java JDK?

---

### Post by lumpie on 2010-08-05
> **Res2216firestar said:**
> Try /usr/lib/jvm/java-6-openjdk/bin .

I got

bash: /usr/lib/jvm/java-6-openjdk/bin: is a directory




> **KdotJ said:**
> How come you need the path? How did you install your Java JDK?

Im trying to install netprobe. Seems like it doesnt like the Java path.

Desktop/netprobe$ sudo ./netprobe start eth0
[sudo] password  
Please edit the file netprobe and set the correct JAVA_PATH.

---

### Post by KdotJ on 2010-08-06
Ok, but how did you install java jdk? The one in the repos? did you download it from oracle?

---

### Post by lumpie on 2010-08-06
> **KdotJ said:**
> Ok, but how did you install java jdk? The one in the repos? did you download it from oracle?

**sudo apt-get install java** or something similar

repos, oracle? youre talkin to a linux dummy, Im just trying to get the dam netprobe to run ](*,)

---

### Post by lumpie on 2010-08-07
bump!

How about it guys? Nobody can help with this? :(

---

### Post by spyrule on 2010-08-07
Try typing at the command line:

```
whereis java
```

It should tell you. ;)

---

### Post by lumpie on 2010-08-07
> **Res2216firestar said:**
> Try /usr/lib/jvm/java-6-openjdk/bin .

That worked. Dont ask how I messed that up. Thanks a lot

---

