---
title: "Problems installing Java"
date: 2010-06-19
forum: New to Ubuntu
---

### Post by adobrakic on 2010-06-19
I was trying to install JDownloader, and get the following error:

```
The following packages have unmet dependencies:
  jdownloader: Depends: sun-java6-bin but it is not installable
E: Broken packages

```

I understand what the error means, just not sure how to fix it. Any suggestions?

---

### Post by QIII on 2010-06-19
What version of Ubuntu are you using?  Lucid?

---

### Post by adobrakic on 2010-06-19
Yessir, I added some repos, but haven't edited or disabled any others, but I'm still assuming I messed something up doing that still.

---

### Post by Perfect Storm on 2010-06-19
Make sure to enable "partner" source in the repositories.

Java have moved to partner repositories in Ubuntu 10.04

---

### Post by QIII on 2010-06-19
As AI says, Java is in the Partner repo.

Have you installed Java in any form or fashion before this?


Edit:  I don't go by "Sir" any more.  I work for a living now.

---

### Post by adobrakic on 2010-06-19
Thank you guys very much, and QIII, I'm not sure what you're alluding to at all, but I apologize if you weren't being sarcastic. :p

---

### Post by QIII on 2010-06-19
Army Officers are addressed by their subordinates as "Sir".  Old inside military joke.  Just joshing.

The reason I ask if you have installed Java before is that I want to know whether we'll have to back out anything to cleanly install it from the repo.

---

### Post by adobrakic on 2010-06-19
Yeah I figured you were playing off a meaning of the word, I just wasn't sure which meaning that was :p But no I haven't, I just installed 10.04 a few days ago.

---

### Post by QIII on 2010-06-19
Good.

Just a bit of history first, so you know why I am asking you to do this.

Canonical is committed to open source software, and only wants open source applications in what you might call the "standard" repos.  Java is not open source.  But it is pervasive.

OpenJDK is the upcoming open source version of Java, but it hasn't quite arrived.  It's maybe 95%.  Added to that, some websites simply don't recognize it as Java.  Hopefully both things are remedied soon.

Anyway.

Because OpenJDK can conflict with Java, I'm going to ask you to make a choice between Java with the Java browser plugin and OpenJDK with the IcedTea browser plugin.  Some say they can coexist.  Others say not.

Full disclosure.

Tell me if that's OK with you.

---

### Post by adobrakic on 2010-06-19
I don't really have a problem with either, as long as it can run JDownloader, which needs JRE to run. I'm not sure if it'd be compatible with OpenJDK.

---

### Post by QIII on 2010-06-19
I have to get to bed.  Sick foster child is finally asleep and wife is yelling at me for playing with my 64 bit mistress.

Here's what I was going to ask you to do:

1.  Use Synaptic to remove OpenJDK and the IcedTea plugin.  Some say you don't need to do this.  Some do.  If you leave it, there is a step below to make sure you use Sun Java as the alternative.  And you can always reinstall OpenJDK and IcedTea.

2.  Go to System|Administration|Software Sources.  On the "Other Software" tab, make sure that the Partner repo is checked.  Close and let the sources update.

3.  Use Synaptic (you could do this from the terminal, but it is easier to look at the list in Synaptic) and search for "java6-sun".

4.  Select the following for installation:  sun-java6-jre, sun-java6-fonts, sun-java6-bin, sun-java6-plugin.  If you are ever interested in developing, you can also install sun-java6-jdk.

5.  Install them.

6.  After they are installed, the following will need to be run if you did not remove OpenJDK and IcedTea (and you can do it for practice anyway, which I would recommend).

```
sudo update-java-alternatives -s java-6-sun
```

Then, check to see that you are using Update 20 by issuing

```
java -version
```

Now.  It is possible to install Java in other ways, but they all leave you having to reinstall it every time a new Update comes out.  When you get done with this, you will have Update 20, which is the latest version.  Since Oracle/Sun has Java in the Partner repository, we hope that the Partner will keep that updated.  If so, as you do your normal periodic updates, Java will be updated as Oracle/Sun updates it.  No need to go reinstall it all the time.

---

### Post by anal_paul on 2010-06-19
PROCESSES OF INSTALLATION jdk1.5.0_01 IN LINUX UBUNTU 9.04(FOR 64.bit) 

        AND STEPS FOR EXECUTING A JAVA PROGRAM


mail me ....i will try my best to solve your problem......

---

### Post by Norm24 on 2010-06-19
Check out this link:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Found it very helpful.

---

### Post by immrlizard on 2010-06-19
QIII   Thanks for that.   I just installed 10.04 and it was just what I was looking for.   The company vpn will not work with the others.

---

### Post by QIII on 2010-06-19
> **anal_paul said:**
> PROCESSES OF INSTALLATION jdk1.5.0_01 IN LINUX UBUNTU 9.04(FOR 64.bit)

AND STEPS FOR EXECUTING A JAVA PROGRAM


mail me ....i will try my best to solve your problem......


Version 5 is very old.  It is not advisable to install it.  Version 6 Update 20 is the current one.  The Version 6 Update 20 jdk is in the repos.  Please don't take solutions outside the forum.  If you do, others cannot benefit.



> **Norm24 said:**
> Check out this link:
[http://sites.google.com/site/easylinuxtipsproject/java](http://sites.google.com/site/easylinuxtipsproject/java)

Found it very helpful.


That works perfectly for versions prior to Lucid.  However, the OP is using Lucid.  The current Java Update 20 is in the partner repo.  If installed from there, it will be updated as Java is updated without having to follow those directions to uninstall and reinstall.  Java should now be installed from the repos.



> **immrlizard said:**
> QIII Thanks for that. I just installed 10.04 and it was just what I was looking for. The company vpn will not work with the others.

Unfortunately, that is the state of things.  I want OpenJDK to become the standard because it is open source.  Unfortunately, it is not perfect yet and, as you say, it does not always work well with others.

---

### Post by anal_paul on 2010-08-26
ok friend....i help my best for you....


at first download jdk-1_5_0_01-linux-i586.bin from SUN JAVA site,then go through with this procedure..

PROCESSES OF INSTALLATION jdk1.5.0_01 IN LINUX UBUNTU 9.04(FOR 64.bit) 

		AND STEPS FOR EXECUTING A JAVA PROGRAM


step 1: paul@paul-laptop$ cd Desktop/

step 2: paul@paul-laptop:~/Desktop$ ls jdk-1_5_0_01-linux-i586.bin


step 3: paul@paul-laptop:~/Desktop$ sudo cp jdk-1_5_0_01-linux-i586.bin  /opt/


step 4: paul@paul-laptop:~/Desktop$ cd /opt/


step 5: paul@paul-laptop:/opt$ sudo chmod a+x jdk-1_5_0_01-linux-i586.bin


step 6: paul@paul-laptop:/opt$ sudo ./jdk-1_5_0_01-linux-i586.bin


step 7: it start auto exucation and wait till documentaion are not not shown on the terminal,if it comes on our screen then press enter till yes/no option coming, and then write yes under the last line for continue unpacking the java packages.


step 8: paul@paul-laptop:/opt$ sudo mkdir /usr/lib/jvmjava



step 9: paul@paul-laptop:/opt$ sudo mv jdk1.5.0_01 /usr/lib/jvmjava/


step 10: paul@paul-laptop:/opt$ cd ..


step 11: paul@paul-laptop$ cd /usr/lib/jvmjava/jdk1.5.0_01/bin



step 12: paul@paul-laptop:/usr/lib/jvmjava/jdk1.5.0_01/bin$ sudo chmod a+x javac


step 13: paul@paul-laptop:/usr/lib/jvmjava/jdk1.5.0_01/bin$ ./javac /home/paul/Desktop/me.java



step 14: paul@paul-laptop:/usr/lib/jvmjava/jdk1.5.0_01/bin$ cd /


step 14* : paul@paul-laptop:/$ cd Desktop\


step 15: paul@paul-laptop:/$ sudo mv me.class /usr/lib/jvmjava/jdk1.5.0_01/bin/

step 15*: paul@paul-laptop:~/Desktop$ cd \

step 16: paul@paul-laptop:/$ cd /usr/lib/jvmjava/jdk1.5.0_01/bin/




step 17: paul@paul-laptop:/usr/lib/jvmjava/jdk1.5.0_01/bin$ sudo chmod a+x java



step 18: paul@paul-laptop:/usr/lib/jvmjava/jdk1.5.0_01/bin$ sudo chmod a+x me.class


step 19: paul@paul-laptop:/usr/lib/jvmjava/jdk1.5.0_01/bin$ ./java me


step 20: Final output on your terminal


-----------------------------------*********----------------------
after installation java set the path for easy

special
***********
for step1>

paul@paul-laptop:/opt$ sudo update-alternatives --install "/usr/bin/java" "java" "/usr/lib/jvm2/jdk1.6.0_20/bin/java" 1

for step 2>

paul@paul-laptop:/opt$ sudo update-alternatives --set java /usr/lib/jvm2/jdk1.6.0_20/bin/java

---

### Post by anal_paul on 2010-08-26
you can try with JAVA 6..same command ..just change the name of java package..:popcorn:

---

