---
title: "SlowMP3"
date: 2011-08-09
forum: New to Ubuntu
---

### Post by chuning on 2011-08-09
Hello - 

I've been using a programme called SlowMP3 in Windows for a while,  which is extremely useful for transcribing music - however, all my other  music software is in Linux, so I wanted SlowMP3 for Linux (Ubuntu  10.10) as well.

I have found it and downloaded the .jar file, but I cannot fathom out how to install it or use it.

can anyone help?

Many thanks

Chris

---

### Post by androssofer on 2011-08-09
> **chuning said:**
> Hello - 

I've been using a programme called SlowMP3 in Windows for a while,  which is extremely useful for transcribing music - however, all my other  music software is in Linux, so I wanted SlowMP3 for Linux (Ubuntu  10.10) as well.

I have found it and downloaded the .jar file, but I cannot fathom out how to install it or use it.

can anyone help?

Many thanks

Chris this help:

open terminal, go to where the file is. 

```
cd /filePath/toJarFile
```

change its permissions so it can run:

```
chmod +x SlowMP3.jar
``` 

then assuming u have java installed properly:

```
java -jar SlowMP3.jar
``` 

and tht should run it for ya. (assuming SlowMP3.jar is the name of the jar file).

then you could create a desktop shortcut (or launcher as i think its called now) then in the 'command' part put:

```
cd /filePath/toJarFile && java -jar SlowMP3.jar
```

and then you should be able to run it from ur desktop :-)

---

### Post by whitethorn on 2011-08-09
Well first you need java, once you have it it should be simple enough to run the program. I think you should probably need to install the Sun Java version, it's all explained in the following article.

[https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java)

Here's the code to start the .jar program, if this works then you can create an alias in your bashrc, or a small launcher.
```

jave -jar /path/to/programn.jar

```

---

### Post by davdo2004 on 2011-08-09
Right click on the jar file and go to properties, Permissions and put a check in the Execute box. Then when you want to run it right click and open with sun java 6 or go to properties and associate jar files with java.

---

### Post by chuning on 2011-08-09
Fantastic!  Got it working

Thanks so much 

Chris

---

