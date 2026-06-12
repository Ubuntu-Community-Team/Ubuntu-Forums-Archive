---
title: "Java programming?"
date: 2008-12-22
forum: New to Ubuntu
---

### Post by Eldar11 on 2008-12-22
I would like to be able to program with java on my computer and I was wondering which packages  need to install to be able to do that.  if anyone has any tips or hints also that would be aprecated.

---

### Post by igknighted on 2008-12-22
> **Eldar11 said:**
> I would like to be able to program with java on my computer and I was wondering which packages  need to install to be able to do that.  if anyone has any tips or hints also that would be aprecated.

Probably you want the sun java package, there are still a few quirks with iced-tea/gcj.  Try installing sun-java6-jdk.  Then you can write your java programs in any editor you want, and compile with the javac command.

If you want an IDE (I wouldn't recommend this, editor + cli compile lets you understand what is happening better IMHO), NetBeans and Eclipse should both be in the repositories.

---

### Post by Eldar11 on 2008-12-22
k thanks! I'll be using javac in terminal so it shouldn't be a problem.

---

### Post by Eldar11 on 2008-12-22
I downloaded and installed it, but I don't know how to enable it.  The Sun website hasn't given clear instructions on how to enable on a linux system.

---

### Post by igknighted on 2008-12-22
> **Eldar11 said:**
> I downloaded and installed it, but I don't know how to enable it.  The Sun website hasn't given clear instructions on how to enable on a linux system.

What do you mean, enable it?  They are libraries, they are just there.

---

### Post by Eldar11 on 2008-12-22
ah well I tried a simple program to see if it worked, but it said that it couldn't use javac.

---

### Post by igknighted on 2008-12-22
> **Eldar11 said:**
> ah well I tried a simple program to see if it worked, but it said that it couldn't use javac.

Can you post the error?  And the command that you issued?

---

### Post by mali2297 on 2008-12-22
> **Eldar11 said:**
> I downloaded and installed it, but I don't know how to enable it.  The Sun website hasn't given clear instructions on how to enable on a linux system.

javac is in the package [sun-java6-jdk](http://packages.ubuntu.com/intrepid/i386/sun-java6-jdk/filelist). Did you install it using the package manager?

---

### Post by Eldar11 on 2008-12-22
yes, I would have done that first, but I was working with two computers.  I was posting from a different computer than the one I was performing commands on.

here is the error:

ryan@ubuntu:~$ javac java.java
The program 'javac' can be found in the following packages:
 * gcj-4.1 (You will have to enable component called 'universe')
 * jikes-sun (You will have to enable component called 'multiverse')
 * jikes-sablevm (You will have to enable component called 'universe')
 * gcj-4.2
 * kaffe (You will have to enable component called 'universe')
 * sun-java6-jdk (You will have to enable component called 'multiverse')
 * jikes-classpath (You will have to enable component called 'universe')
 * openjdk-6-jdk (You will have to enable component called 'universe')
 * ecj
 * j2sdk1.4 (You will have to enable component called 'multiverse')
 * jikes-gij (You will have to enable component called 'universe')
 * jikes-kaffe (You will have to enable component called 'universe')
 * sun-java5-jdk (You will have to enable component called 'multiverse')
 * java-gcj-compat-dev
Try: sudo apt-get install <selected package>
bash: javac: command not found

all the program has is a println command for a one liner.

---

### Post by igknighted on 2008-12-22
Eldar:

Between this and your .bin thread, I think you may be missing out on one of the most powerful tools on linux... the package manager.  See this link for more info: [http://psychocats.net/ubuntu/installingsoftware](http://psychocats.net/ubuntu/installingsoftware)

Almost never should you go to a manufacturers website to get a program, all these programs are pre-packaged and stored in a central repository.  Installing from here is almost always preferred.

---

### Post by Eldar11 on 2008-12-22
The thing is that these things don't show up in the package manager so I'm pretty confused.

---

### Post by mali2297 on 2008-12-22
> **Eldar11 said:**
> The thing is that these things don't show up in the package manager so I'm pretty confused.

You need to enable the *multiverse* repository. In Synaptic, check under Settings -> Repositories.

---

### Post by igknighted on 2008-12-22
> **Eldar11 said:**
> The thing is that these things don't show up in the package manager so I'm pretty confused.

Can you post the output of the command 'cat /etc/apt/sources.list'?

---

### Post by Eldar11 on 2008-12-22
This problem was solved in the other thread; I didn't have access to other things in the package manager because my repository wasn't set to look for them. Thanks so much!

---

### Post by Eldar11 on 2008-12-22
mali, 

That package I've been looking for and I can't find it under the package manager.  I haven enabled mulitverse repositorys, but i still cant find it.  hmmmm now that I think about I didn't reload it after I clicked that option.  Though some of the Sun packages did show up.  I'm still confused....

---

### Post by Eldar11 on 2008-12-22
Yeah, that was the key, I had to reload it.  It should work now.

---

### Post by igknighted on 2008-12-22
sun-java5-jdk would work too.  What version of Ubuntu are you using?

---

### Post by Eldar11 on 2008-12-22
8.04 LTS on an older computer, so you're right I don't need java6, but if it works then all the better

---

