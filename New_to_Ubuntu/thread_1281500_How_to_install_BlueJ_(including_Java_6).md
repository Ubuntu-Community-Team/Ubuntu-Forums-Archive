---
title: "How to install BlueJ (including Java 6)"
date: 2009-10-03
forum: New to Ubuntu
---

### Post by underage17 on 2009-10-03
i recently installed ubuntu over windows, and i want to install bluej (along with java)
i d/l the latest bluej (2.5.2) ystrday and dwnloaded Java 6 today.
i expected a quick Next > Next > Finish dialogue..but it seems Ubuntu doesn't have one! :P
can anyone tell me how to go about doing this? thank u!

---

### Post by celticbhoy on 2009-10-03
Have you tried the installation guide from the bluej website?

Are getting an error?

---

### Post by underage17 on 2009-10-04
the website says:
> /path/to/jdk/bin/java -jar bluej-252.jar
i haven't tried it yet, because i dont have the java kit..
i download a 158 mb Java6SE but i don't know how to install it.
once i install that, then i might be able to install bluej..

---

### Post by The Cog on 2009-10-04
There's no need to download the SDK - just install the one in the Ubuntu repositories. Command: ```
sudo aptitude install jun-java6-jdk sun-java6-fonts sun-java6-plugin sun-java6-doc
```
Then download the bluej installer (I always go for the generic installer - the jar file) and run it as you said: ```
java -jar bluej-252.jar 
```

---

### Post by underage17 on 2009-10-04
nothing's happening when i type either of the codes in.
im totally new to this.. im assuming ur asking me to type in the run window (Alt F2?)
when i type the exact thing in and click Run, the run window disappears but nothing happens. 
btw, the file (the java file) is called java_ee_sdk-5_07-jkd-6u16-linux.bin and it is kept in my /home/username folder if this means anything to u.
how do u work out these codes anyway?
thank u

---

### Post by mick222 on 2009-10-04
NO open a terminal and type the commands in there it will ask for password.

---

### Post by The Cog on 2009-10-05
I've never looked at j2ee. So I don't know if it includes the j2se which includes the javac compiler that you will be needing.

If you really want j2ee then maybe you do need to run the installer that you downloaded from Sun. If so, open the terminal (Application->Accessories->Terminal) and run these commands which mark the installer as executable and then run it as root:
```
chmod +x java_ee_sdk-5_07-jkd-6u16-linux.bin
sudo ./java_ee_sdk-5_07-jkd-6u16-linux.bin
```
but unless you know you really want j2ee, I would suggest that you go with the normal j2se that comes in the repositories.

If you don't like the command line, you can install the j2se sdk graphically. Go for the menu System->Administration->Synaptic Package Manager and search for **sun-java**.

---

