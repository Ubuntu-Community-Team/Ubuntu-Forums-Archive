---
title: "Installing Dr. Java"
date: 2009-09-02
forum: New to Ubuntu
---

### Post by WriteGirl on 2009-09-02
Hi!

I'm taking a computer science class and we're using Dr. Java in it. The professor said that it worked with Linux but I can figure out how to install it. I downloaded the JDK first and then Dr. Java, but Dr. Java won't load. I put 

```
 java -jar drjava-stable-20040326.jar
```

based on a website I found, and I checked that it was the number, but it didn't work. 

Thanks!

---

### Post by scorp123 on 2009-09-02
> **WriteGirl said:**
> but it didn't work. "Didn't work" is not informative enough.

Please give us the _exact_ error message.

---

### Post by falconindy on 2009-09-02
Did you download the same version as the file you read on the website? If you're trying to run it from the command line, tab completion is your friend. In other words
```
java -jar drjava<tab>
```
And the rest will be filled in for you. There's no installation -- it runs on its own.

---

### Post by WriteGirl on 2009-09-02
When I put in ```
java -jar drjava<tab>
```, I got ```
bash: syntax error near unexpected token `newline'
```

When I put in ```
java -jar drjava-stable-20040326.jar
```, I got ```
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

### Post by falconindy on 2009-09-02
So you don't have a JRE installed.
```
sudo apt-get install sun-java6-jre
```

---

### Post by scorp123 on 2009-09-02
> **WriteGirl said:**
> When I put in ```
java -jar drjava-stable-20040326.jar
```, I got ```
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
``` You don't have Java installed.

Go into ...
[INDENT]System > Administration > Software Sources[/INDENT]

You will be asked for your password. Once this new program window is open, go to the tab that says "Ubuntu Software" (it should be the first tab anyway). Please activate these options:

[LIST]
[*]Canonical supported Open Source software (main)
[*]Community maintained Open Source software (universe)
[*]Proprietary drivers (restricted)
[*]Software restricted by copyright (multiverse)
[*]Source code
[/LIST]

Hit the "Close" button. When the program complains that the package list is out-of-date, let it refresh itself.

Now, go back to the terminal and type this code:

```
sudo apt-get install sun-java6-bin sun-java6-fonts sun-java6-jre sun-java6-plugin
``` You will probably asked again for your password. The password is _NOT_ echoed back when you type it, there won't be stars, dots, or anything. Just type it in blindly and hit enter.

The command I gave you above should then proceed to download Sun's Java runtime environment for you. After that you will have Java installed and Java programs should be able to run.

---

### Post by WriteGirl on 2009-09-02
falconindy - I'm installing the JRE now. Once that's installed, will the code you gave me before work?

---

### Post by scorp123 on 2009-09-02
> **WriteGirl said:**
> falconindy - I'm installing the JRE now. Once that's installed, will the code you gave me before work? The code you've used before should work

---

### Post by scorp123 on 2009-09-02
> **WriteGirl said:**
> When I put in ```
java -jar drjava<tab>
``` You're not supposed to type "<tab>" into the command :D

You're supposed to hit the ***TAB*** key. So you type:
```
java -jar drjava*<press the TAB key>*
```

The command line shell should auto-fillout the rest (that's what the TAB key is for).

---

### Post by WriteGirl on 2009-09-03
I believe I installed Java, but I still haven't figured out how to open the Dr. Java program.  When I put ```
java -jar drjava-stable-20040326.jar
``` in, I only got ```
Unable to access jarfile drjava-stable-20040326.jar


```

I downloaded to Dr. Java to the Desktop, could that be the problem?

Thanks!

Never mind, I figured it out. Thanks!

---

### Post by JustDutch on 2013-03-17
Hey guys,

Sorry to reopen this thread, but I encountered the same problem as WriteGirl and made the same steps she did.
I end up with the same final problem where I get the error message "Unable to access jarfile XXX.jar"
I pm-ed WriteGirl about this, but she seems to have been inactive after this last post, so now I' m asking you guys.
Does any one of you know what WriteGirl might have done to solve this?

Thanks,
JustDutch


Edit: link to the [original thread]("http://ubuntuforums.org/showthread.php?t=1256676&p=7894509#post7894509")

---

### Post by oldos2er on 2013-03-17
Please start a new thread.

---

