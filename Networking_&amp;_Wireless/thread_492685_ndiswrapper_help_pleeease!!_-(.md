---
title: "ndiswrapper help pleeease!! :-("
date: 2007-07-05
forum: Networking &amp; Wireless
---

### Post by oodlesOfmoodles on 2007-07-05
hi. i am a linux n00b. as soon as i can get my wireless working im going to take an online (free) course about linux basics. but first i need to get my internet working 

 pretty please can i have a step-by-step (like, realllly simple that even my parents could follow along) walkthrough that takes me from 
downloading ndiswrapper-1.47.tar.gz till 

i can type in the console:

**ndiswrapper -i mydriver.inf' **

and it doesnt say 'the program 'ndiswrapper' is currently not installed.

thank you sooo much i am getting really frustrated and i really want this to work because linux is cool

---

### Post by sj3fk3 on 2007-07-05
> **oodlesOfmoodles said:**
> hi. i am a linux n00b. as soon as i can get my wireless working im going to take an online (free) course about linux basics. but first i need to get my internet working 

 pretty please can i have a step-by-step (like, realllly simple that even my parents could follow along) walkthrough that takes me from 
downloading ndiswrapper-1.47.tar.gz till 

i can type in the console:

**ndiswrapper -i mydriver.inf' **

and it doesnt say 'the program 'ndiswrapper' is currently not installed.

thank you sooo much i am getting really frustrated and i really want this to work because linux is cool

First of all you should not be installing ndiswrapper from source but simply use the package management that comes with Ubuntu either use the GUI interface or apt or aptitude to install stuff. If you don't know what I am talking about read up at [https://help.ubuntu.com/7.04/add-applications/C/index.html](https://help.ubuntu.com/7.04/add-applications/C/index.html)

---

### Post by bsawler on 2007-07-05
Why not use:

System > Administration > Synaptic Package Manager 

to install ndiswrapper

---

### Post by fredj on 2007-07-05
Do not install ndiswrapper by using the synaptic package installer. If you do you will end up with a version
that does not work. They put the wrong version in the repositories and now it can't be corrected. The only way 
to get a good version is to download the latest source fom the ndiswrapper site and compile it.

---

### Post by j_dog on 2007-07-05
Well.............That explains the root of my last problem !  Many thanks go to*** sj3fk3 *** for helping me fix it !

---

### Post by fredj on 2007-07-05
To start with open a terminal and type ndiswrapper -v and post the message you get here so that we can be
sure that you have got a non working version.

2. Download the source file from the ndiswrapper site and put it in a suitable subdirectory (make one yourself)
off your home directory.

Then I will give you full instructions for compiling even though your parents won't understand them.

---

