---
title: "[SOLVED] change to java NOT on update-java-alternatives list"
date: 2008-12-17
forum: New to Ubuntu
---

### Post by ufis on 2008-12-17
I have had to install a jre other than sun's. (IBM jre) The only installation was from a .rpm

Everything is installed and working (semi) fine.
When I add
[PHP]export PATH=/opt/ibm/java-i386-60/jre/bin:$PATH[/PHP]
to my ~/.bashrc I can run those IBM jars fine.
```
java -version
```
shows the correct java version (IBM version)

But the applications that need to run those jars are running under different users. So when they run they use the sun java and not ibm java.

```
update-java-alternatives -l
```
shows only sun's java.


How do I update the whole system to use IBM's java by default if it does not show up on update-java-alternatives ?

---

### Post by The Cog on 2008-12-17
I always just put a symbolic link to the right java in /usr/local/bin/java, because this is in the path earlier than the one in /usr/bin so it takes precedence.
> cd /usr/local/bin
sudo ln -s /opt/ibm/java-i386-60/jre/bin/java java

---

### Post by lovelyvik293 on 2008-12-17
The PATH for the SUN java is in the Default path variable.
You can remove the SUN JAVA from the ADD/REMOVE.So that your application uses the IBM JAVA.

---

### Post by ufis on 2008-12-17
> **The Cog said:**
> I always just put a symbolic link to the right java in /usr/local/bin/java, because this is in the path earlier than the one in /usr/bin so it takes precedence.

This works fine from the command line, but not with my application.

I have meanwhile hard coded my application to use /opt/ibm/java-i386-60/jre/bin/java and not just "java". This will have to do while I find a solution.

PS. I have completely removed sun java from the box.

---

### Post by ufis on 2008-12-17
I have found [http://ubuntuforums.org/showthread.php?t=592934](http://ubuntuforums.org/showthread.php?t=592934) that solved my problem.

---

