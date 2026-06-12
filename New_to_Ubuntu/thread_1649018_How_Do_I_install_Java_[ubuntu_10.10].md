---
title: "How Do I install Java??? [ubuntu 10.10]"
date: 2010-12-19
forum: New to Ubuntu
---

### Post by sKRiBEL on 2010-12-19
ok well i went to the Java website, and i downloaded the "_Linux (self extracting file)_" version of Java, i continued to the instructions page afterward and followed the instructions, but i'm not able to install it. It tells me to enter this: ```
chmod a+x jre-6u<version>-linux-i586.bin
``` ...into the terminal, i did but no luck i get this message : ```
bash: version: No such file or directory
``` Is there anyone that can help me with this? Any help would be greatly appreciated :]

---

### Post by Verbeck on 2010-12-19
place the file in your home folder and try again

or change the working directory to where it is
eg,
```

cd ~/Downloads
chmod a+x jre-6u<version>-linux-i586.bin

```

---

### Post by howefield on 2010-12-19
I have followed these instructions in the past, they work well and describe several methods of installing java, including using OpenJDK and the icedtea plugin, installing Oracle Java from the Ubuntu repository and also installing from the file that you have downloaded..

[https://sites.google.com/site/easylinuxtipsproject/java](https://sites.google.com/site/easylinuxtipsproject/java)

---

### Post by sKRiBEL on 2010-12-19
@Verbeck Hey thanks it worked :]

---

