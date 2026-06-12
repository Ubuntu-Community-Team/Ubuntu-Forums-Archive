---
title: "What is the best way to set global environment variables in one place?"
date: 2010-10-17
forum: New to Ubuntu
---

### Post by egervari on 2010-10-17
What is the best way to set global environment variables in one place, preferably in my home directory?

I've tried /etc/environment, but I don't think it works 100%. While applications like IDEA can find the jdk when they start up, other applications that run inside of Idea (sbt) cannot find the command "java", which IS included in the path.

I've read [https://help.ubuntu.com/community/EnvironmentVariables](https://help.ubuntu.com/community/EnvironmentVariables), but I'm actually more confused by it because it doesn't recommend all of the options I've tried. LOL. It also comments that the solution I may have liked (~/.pam_environment) will not work on 10.04. I'm running on 10.10, but I suspect it really means 10.x because the documentation may be out of date?

```

JDK_HOME="/opt/jdk1.6.0_22"
JAVA_HOME="/opt/jdk1.6.0_22"
M2_HOME="/opt/apache-maven-3.0"
MAVEN_HOME="/opt/apache-maven-3.0"
ANDROID_SDK_HOME="/home/egervari/Programs/android-sdk-linux_x86"
SCALA_HOME="/opt/scala-2.8.0.final"

PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:$M2_HOME/bin:$JAVA_HOME/bin:$SCALA_HOME/bin:$ANDROID_SDK_HOME"

```It is rather odd, because if I do not include separate environment variables in my .bashrc for example, the shell cannot recognize "java", even though IDEA does.

Is there a way I can set all of these in 1 and only 1 place while still being able to have my desktop applications and my shells access them 100% of the time?

---

### Post by egervari on 2010-10-17
Okay, I've tried everything from "export" before each line to not having any quotes - nothing works as far as /etc/environment is concerned.

I can see that these environment variables are set, but the path just isn't being used. It's so annoying/infuriating. Typing in "java", "javac" or "mvn" will not execute the files. All the shell does is recommend packages to install... but they are totally there!

Duplicating all of these in .bashrc makes them accessible in the shell at least, but then they are duplicated /etc/environment as well... not to mention, commands like "java" are still not found if a shell is not used.

Help please?

---

