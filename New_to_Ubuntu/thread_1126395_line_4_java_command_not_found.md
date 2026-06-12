---
title: "line 4: java: command not found"
date: 2009-04-15
forum: New to Ubuntu
---

### Post by tadcan on 2009-04-15
I have tried to install storybook in 9.04 beta. The instructions are simple

[http://storybook.intertec.ch/joomla/index.php/installation](http://storybook.intertec.ch/joomla/index.php/installation)

and I had it installed in 8.10 without any problems. Now in 9.04 I have this error.

```
tadcan@Quad:~$ ./storybook.sh
starting ...
./storybook.sh: line 4: java: command not found
done.
```

Any ideas?

---

### Post by Simian Man on 2009-04-15
Install java?

---

### Post by tadcan on 2009-04-15
I did that and tried again, didn't work. I'll restart the computer to see if that works.

---

### Post by tadcan on 2009-04-15
Computer restart doesn't have any effect.

---

### Post by taurus on 2009-04-15
Which java did you install and how did you install it?

What's the output of this command from a terminal?

```
java -version
```

---

### Post by James_Lochhead on 2009-04-15
If you get a version out from the above command. Type this in a terminal:

```

sudo update-alternatives --config java

```

And choose the OpenJRE or SunJRE (the one you have installed). Do this by picking the correct number, typing it and then pressing enter.

---

### Post by tadcan on 2009-04-15
I installed from here so I should have an up to date java. I installed as per the instructions in the /home/tadcan dir

[http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80](http://www.java.com/en/download/linux_manual.jsp?locale=en&host=www.java.com:80)

```
tadcan@Quad:~$ java -version
The program 'java' can be found in the following packages:
 * gij-4.3
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.2
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
bash: java: command not found

```

---

### Post by Copernicus1234 on 2009-04-15
Always install from repositories if you are new to Linux and you really want it to "just work".

On the other hand, its always nice to learn how to get stuff work that isnt in the repositories as well. You just need a bit more time and patience, but the reward in knowledge is so worth it.

---

### Post by taurus on 2009-04-15
```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```
When you get to the licensing screen, press the Tab key to highlight the <OK> and Return to accept it.

---

### Post by Simian Man on 2009-04-15
> **tadcan said:**
> 
```
tadcan@Quad:~$ java -version
The program 'java' can be found in the following packages:
 * gij-4.3
 * java-gcj-compat-headless
 * openjdk-6-jre-headless
 * cacao
 * gij-4.2
 * jamvm
 * kaffe
Try: sudo apt-get install <selected package>
bash: **java: command not found**

```

So you still don't have java installed.  Follow taurus' directions.

---

### Post by tadcan on 2009-04-15
Thanks that worked. I mustn't have installed it the first time. Now I know how to check.

---

### Post by dskjustforme on 2009-11-19
> **tadcan said:**
> Thanks that worked. I mustn't have installed it the first time. Now I know how to check.
so i can't install the older version of java

---

### Post by StrungOut101 on 2010-08-26
> **taurus said:**
> ```
sudo apt-get update
sudo apt-get install sun-java6-bin sun-java6-jre sun-java6-plugin
```When you get to the licensing screen, press the Tab key to highlight the <OK> and Return to accept it.

thanks I'll give that a try and report back

---

### Post by StrungOut101 on 2010-08-26
> **StrungOut101 said:**
> thanks I'll give that a try and report back

worked
thx u

---

### Post by intertec on 2010-11-06
Storybook should work with the current OpenJDK now. Read this instructions how to install Java (OpenJDK) on Ubuntu:
[http://storybook.intertec.ch/joomla/index.php/component/content/article/35-installation/129-install-java-under-ubuntu-or-kubuntu](http://storybook.intertec.ch/joomla/index.php/component/content/article/35-installation/129-install-java-under-ubuntu-or-kubuntu)

---

