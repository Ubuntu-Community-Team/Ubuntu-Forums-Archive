---
title: "problem with jre"
date: 2011-07-07
forum: New to Ubuntu
---

### Post by samitrimal on 2011-07-07
hello  i install and my path detail are as follows
PATH="/usr/local/java/jdk1.6.0_26/bin/:/usr/local/java/jre1.6.0_26/bin/:local/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
JAVA_HOME="/usr/local/java/jdk1.6.0_26/";
CLASSPATH=".:/usr/local/java/jdk1.6.0_26/lib/"
is there any problem with my path i cannot open jedit and other java programs but i can compile using  javac command .
dont know what problem is it

---

### Post by mikejonesey on 2011-07-07
try running "jedit" (don't know this one but i use netbean and eclipse)... from comand line, if it can't find the jre it will tell you, if you need help configuring after this lemmie know...

ps also java_home usualy refers to a jre not a jdk, (the jre is stored within the jdk), eg;

export JAVA_HOME="/usr/local/java/jdk1.6.0_26/jre"

---

