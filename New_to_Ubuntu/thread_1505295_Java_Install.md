---
title: "Java Install"
date: 2010-06-09
forum: New to Ubuntu
---

### Post by Kirkland14 on 2010-06-09
So i'm trying to get java installed but seem to keep running into problems.  I download the program from java and followed their instructions and when I went to change the permissions using their code:

```
chmod a+x  jre-6u<version>-linux-i586.bin
```I got this:

```
kevin@ubuntu:~$ chmod a+x jre-6u<version>-linux-i586.bin
bash: version: No such file or directory
```Any help?  I searched the forums but theirs alot of threads concerning installing Java

Thanks

Kevin

---

### Post by QIII on 2010-06-09
I would stop now and do it the best way.

(What you are doing, by the way, won't work because "<version>" should be replaced by the version designation.  It should not be typed verbatim.)

Go to System | Administration | Software Sources.

In the "Other software" tab, check Lucid Partner (and Source, if you  want).

When your sources are updated, use Synaptic to install the sun-java6 packages.

When those have been installed, go to the terminal and issue the following 

```
sudo update-java-alternatives -s java-6-sun
```When that has completed, check to see that you have the current Sun Java installed by issuing

```
java -version
```Using the Partner repo is desirable because as Java is updated it will be placed in the repos and your normal update processes will keep up with the latest version.  That way,  you don't have to keep updating it manually every time Sun updates the version.

---

### Post by Kirkland14 on 2010-06-09
Thanks alot for the help! worked no problem.  I can't wait for the day when I learn how to do all this on my own.  I know exactly what I just did there.  Thanks again

Kevin

---

### Post by Miljet on 2010-06-09
Write it down, you probably won't remember it six months from now when you need it again!

---

### Post by Kirkland14 on 2010-06-10
> Write it down, you probably won't remember it six months from now when  you need it again!thanks.  thats a good idea

---

### Post by FybrOptx on 2010-10-09
Wow!  This worked great!  Thanks.  Now even Minecraft works as well as the various Pogo stuff (which is a good test).

---

