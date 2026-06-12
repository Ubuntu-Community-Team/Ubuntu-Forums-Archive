---
title: "[SOLVED] HELP ME How do I upgrade my Ubuntu to a i686!"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by friyia@hotmail.com on 2008-12-19
Hello Experianced Ubuntu users,

I just got my 8.10 version and I am supremely Noob at using it. I tried to put some programs on and realized they would not open. After doing hours of Reserch I realized I needed an i686. How do I upgrade my Ubuntu to a i686?

---

### Post by ichbinesderelch on 2008-12-19
all i386 programms should run on an i686 machine, i guess this shoudlnt be the error that causes your programms not to run!

---

### Post by friyia@hotmail.com on 2008-12-19
> **ichbinesderelch said:**
> all i386 programms should run on an i686 machine, i guess this shoudlnt be the error that causes your programms not to run!

No I have a i386 Machine and I need to Upgrade to a i686 I need to know How

---

### Post by pablolie on 2008-12-19
> **friyia@hotmail.com said:**
> Hello Experianced Ubuntu users,

I just got my 8.10 version and I am supremely Noob at using it. I tried to put some programs on and realized they would not open. After doing hours of Reserch I realized I needed an i686. How do I upgrade my Ubuntu to a i686?

your message seems to imply that ubuntu installed correctly. what are the programs that don't run? do you mean the 32 versus the 64 bit installation?

---

### Post by friyia@hotmail.com on 2008-12-19
> **pablolie said:**
> your message seems to imply that ubuntu installed correctly. what are the programs that don't run? do you mean the 32 versus the 64 bit installation?

Man I don't even know LIke I went to install frostwire.. and I realized there was this i586 thing at the end of it and I did reserch and realized it had to do with MY OS I am at a i386 right now from what I know about Ubuntu 8.10 like that's all I really know. Liek I'll click Frostwire and It won't run at all

---

### Post by ichbinesderelch on 2008-12-19
i386 are your hardware specs more the less, so i guess your computer is rather old?

---

### Post by friyia@hotmail.com on 2008-12-19
> **ichbinesderelch said:**
> i386 are your hardware specs more the less, so i guess your computer is rather old?

Liek there Okay I used to have XP till it CRASHED like Incompitant windows does :P I have a pentium 4 processor and 512 MB of Ram

---

### Post by ichbinesderelch on 2008-12-19
i586 and i686 should afaik run on a pentium4, so i really guess its some different problem, packages compile for i586 or i686 are running on ubuntu optimized for i386

---

### Post by friyia@hotmail.com on 2008-12-19
> **ichbinesderelch said:**
> i586 and i686 should afaik run on a pentium4, so i really guess its some different problem

I need to know How to take an i386 and Convert is to a i586 or i686 cause even like Mercury Messanger,and programs in My Add/Remove Programs will not work without a i586 package

---

### Post by ichbinesderelch on 2008-12-19
the i386 and i686 only means that they are optimized towards i386 machines, you could migrate packages by setting the correct serverflags and compiling the packages by hand, but that is loads of work and really shouldn't be necesarry

---

### Post by friyia@hotmail.com on 2008-12-19
> **ichbinesderelch said:**
> the i386 and i686 only means that they are optimized towards i386 machines, you could migrate packages by setting the correct serverflags and compiling the packages by hand, but that is loads of work and really shouldn't be necesarry

SO like ... what do I do to get it so I can run i586 programs?

---

### Post by SunnyRabbiera on 2008-12-19
really weird, you should be able to use the applications you need as P4's are i386 compatible, I have one myself.
and it should work with i586 packages too, I use them.
I wonder why you are getting this issue, if you select a x86 package it should work no matter what.
The package should install, no matter the number it says unless its marked x64.
Do you have java installed?
Frostwire needs java to work

---

### Post by friyia@hotmail.com on 2008-12-19
> **SunnyRabbiera said:**
> really weird, you should be able to use the applications you need as P4's are i386 compatible, I have one myself.
and it should work with i586 packages too, I use them.
I wonder why you are getting this issue, if you select a x86 package it should work no matter what.
The package should install, no matter the number it says unless its marked x64.
Do you have java installed?
Frostwire needs java to work

I am pretty sure how do I know if I do or don't have Java Installed???

---

### Post by dmizer on 2008-12-19
I believe frostwire is in the repositories. You should be able to install it through synaptic package manager. You may have to enable the non-free repositories.

Windows way = search online, find software, hope it's okay, start install wizard.
Linux way = open synaptic package manager, search for what you want, install without worry.

More information here: [http://ubuntuforums.org/showthread.php?t=995529](http://ubuntuforums.org/showthread.php?t=995529)

Despite the fact that your kernel says i386, it will work just fine on any other hardware. More information here: [http://ubuntuforums.org/showthread.php?t=121248](http://ubuntuforums.org/showthread.php?t=121248)

---

### Post by ichbinesderelch on 2008-12-19
check if you have the default-jre package installed, this should be the java package if i'm not wrong, maybe i am :P

---

### Post by SunnyRabbiera on 2008-12-19
> **friyia@hotmail.com said:**
> I am pretty sure how do I know if I do or don't have Java Installed???

Well lucky for you there is a easy solution here, up in your menu under system and administration there is something called synaptic package manager.
In here go to "settings"
and then to "repositories"
here make sure all your sources are checked off as you need to ensure the java repo is on (java 6 is semi free so it cant be installed by default on ubuntu at this time)
after making sure all boxes in the first and second tabs are checked off except the source code repos, you hit "refresh"
then search for java runtime
also make sure to remove the packages marked open jdk, open jdk is the open source version of java but its not that good (yet)
anyhow install the sun-java6-jre sun-java6-bin and sun-java6-plugin packages
this should help

Now did you try other packages marked i586?
I assure you anything with the x86 mark should work on your system, only x64 packages wont work.

---

### Post by friyia@hotmail.com on 2008-12-19
> **dmizer said:**
> I believe frostwire is in the repositories. You should be able to install it through synaptic package manager. You may have to enable the non-free repositories.

Windows way = search online, find software, hope it's okay, start install wizard.
Linux way = open synaptic package manager, search for what you want, install without worry.

More information here: [http://ubuntuforums.org/showthread.php?t=995529](http://ubuntuforums.org/showthread.php?t=995529)

Despite the fact that your kernel says i386, it will work just fine on any other hardware. More information here: [http://ubuntuforums.org/showthread.php?t=121248](http://ubuntuforums.org/showthread.php?t=121248)
SO far so Good with the Java Download if nothing else it is the first thing that's showed Potential in 4 hours of trying to get this to work

Okay Now ALl I need is to know how to puch okay In th Terminall !!

---

### Post by friyia@hotmail.com on 2008-12-19
> **SunnyRabbiera said:**
> Well lucky for you there is a easy solution here, up in your menu under system and administration there is something called synaptic package manager.
In here go to "settings"
and then to "repositories"
here make sure all your sources are checked off as you need to ensure the java repo is on (java 6 is semi free so it cant be installed by default on ubuntu at this time)
after making sure all boxes in the first and second tabs are checked off except the source code repos, you hit "refresh"
then search for java runtime
also make sure to remove the packages marked open jdk, open jdk is the open source version of java but its not that good (yet)
anyhow install the sun-java6-jre sun-java6-bin and sun-java6-plugin packages
this should help

Now did you try other packages marked i586?
I assure you anything with the x86 mark should work on your system, only x64 packages wont work.


I can't find this SYnaptec thing everyone talks about even under system :(

---

### Post by SunnyRabbiera on 2008-12-19
> **friyia@hotmail.com said:**
> SO far so Good with the Java Download if nothing else it is the first thing that's showed Potential in 4 hours of trying to get this to work

Patience is a virtue, remember even windows takes a learning curve.
But we are here to help, a linux community is among the best out there for computer issues :D

> **friyia@hotmail.com said:**
> I can't find this SYnaptec thing everyone talks about even under system :(


It should be under the administration submenu, under system.
it should say "synaptic package manager"

---

### Post by friyia@hotmail.com on 2008-12-19
> **SunnyRabbiera said:**
> Patience is a virtue, remember even windows takes a learning curve.
But we are here to help, a linux community is among the best out there for computer issues :D




It should be under the administration menu, under system.
it should say "synaptic package manager"

Thanks Man ... I can't wait to figure this whole thing out... Like So far Ubuntu is way faster than like Windows was I am pumped to see what else this can do

---

### Post by SunnyRabbiera on 2008-12-19
> **friyia@hotmail.com said:**
> Thanks Man ... I can't wait to figure this whole thing out... Like So far Ubuntu is way faster than like Windows was I am pumped to see what else this can do

trust me Ubuntu is one of the easiest linux distros out there to learn, perhaps not the easiest linux but it is pretty easy none the less.

---

### Post by HotShotDJ on 2008-12-19
> **dmizer said:**
> I believe frostwire is in the repositories.I just double checked (you got me excited there!).  Alas, Frostwire is not in the repositories.

---

### Post by friyia@hotmail.com on 2008-12-19
> **HotShotDJ said:**
> I just double checked (you got me excited there!).  Alas, Frostwire is not in the repositories.

WHat's that meann?

---

### Post by Tomatz on 2008-12-19
Open a terminal and type:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-686 linux-restricted-modules-686 
```


Reboot, done!


It will run better than the i386 kernel (due to utilising more instructions) and is fully backwards compatible.

---

### Post by SunnyRabbiera on 2008-12-19
> **friyia@hotmail.com said:**
> WHat's that meann?

In Ubuntu we use a central repository of packages, as someone once explained in a previous post.
Instead of going to website a and website b for software Ubuntu has everything in one big library.
Just because a package isnt int the repos doesnt mean it wont work though, some software isnt on the repos so sometimes you do have to go out of the repositories to get them.
Repo is short for repositories so you know :D

> **Tomatz said:**
> Open a terminal and type:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-686 linux-restricted-modules-686 
```


Reboot, done!


It will run better than the i386 kernel (due to utilising more instructions) and is fully backwards compatible.

Nahh I would not do that to him just yet, let him get his feet wet first.
To the original poster: ignore those commands please... for now.

---

### Post by friyia@hotmail.com on 2008-12-19
> **Tomatz said:**
> Open a terminal and type:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get install linux-image-686 linux-restricted-modules-686 
```


Reboot, done!


It will run better than the i386 kernel (due to utilising more instructions) and is fully backwards compatible.

Thanks Man !!!!!!

---

### Post by SunnyRabbiera on 2008-12-19
> **friyia@hotmail.com said:**
> Thanks Man !!!!!!

I just hope it will work, I would not have insisted on those commands considering you are new.

---

### Post by friyia@hotmail.com on 2008-12-19
> **SunnyRabbiera said:**
> I just hope it will work, I would not have insisted on those commands considering you are new.

i hvae another Quick question

How do I push okay in the terminal???

---

### Post by Partyboi2 on 2008-12-19
try pressing "tab", when "ok" is highlighted press "enter"

---

### Post by friyia@hotmail.com on 2008-12-19
> **partyboi2 said:**
> try pressing "tab" when "ok" is highlighted press "enter"

thanks so much everyone that helped me here you are all really really really awesome and i look forward to learning more about the ubuntu system because of all of you !!

---

### Post by dmizer on 2008-12-21
> **HotShotDJ said:**
> I just double checked (you got me excited there!).  Alas, Frostwire is not in the repositories.

I know that there IS a third party repository with Frostwire in it, but since I do not use Frostwire (I prefer transmission because it has a web client) I have not put any effort into finding it. Downloading Frostwire from a recognized 3rd party repository (medibuntu?) is probably the OP's easiest and most preferable solution.

Compiling from source will only make things work until the next kernel update, then you'll have to reinstall. Installing from source should only be used as an absolute last resort.

---

