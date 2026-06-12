---
title: "Software Install &amp; Running"
date: 2009-04-26
forum: New to Ubuntu
---

### Post by fafayacity on 2009-04-26
Hello,

I am new with Ubuntu and I love its interface and have been thinking about moving away from Windows. I have been surprised how different it works from Windows and I am in for a steep learning curve. I have a problem I have not been able to solve yet:

The synaptic Package Manager had a program (Predict-2.2.3. under Amateur Radio) listed in it. I was under the impression that if I installed it from there, the program would be available to me to run. It may be but I cannot see it. When I go to the Terminal window and type "predict" on the command line, I get the initial screen asking me to put my coordinates in. At the end of that, when I hit Enter, I get the command line again, meaning I am where I started before instead of the program going to the main menu.

Given this, I downloaded the program from the Internet and tried to install it from the Terminal Window. I saved the program on my desktop and accessed it using cd Desktop/predict2.2.3. And then I ran the command sudo ./configure but I get the following message:"One moment please...installer.c:16:20: error: curses.h: No such file or directory".

This is the problem I am running into right now and I am getting frustrated with this. I guess I have been on Windows logic too much and need to start thinking fresh.

Thanks for the help.

PS: I had posted another help request before and members helped me get the run command. I thought I got it but I was wrong.

---

### Post by zvacet on 2009-04-26
I don´t use that package but I saw in synaptic when you right click on it you will see suggested packages for install.Maybe they will give you front-end for your package.

---

### Post by Mark Phelps on 2009-04-27
The error you're getting trying to compile the source indicates that a header file is missing.  You can start by installing build-essential through Synaptic.  That will install a bunch of libraries and header files.

If that doesn't solve your problem, you could be in for a LOT of work.  I recently decided to upgrade an app from source because it hadn't been packaged in over a year -- and ended up having to install over 100 additional packages to finally cover all the source and library dependencies.

There's typically a configure script you run that will search your system for all the dependencies and fail when it finds one missing.  There is also generally a log file that script produces when it runs.  But, you will have to resort to Googling to find the libraries containing the source code and header files.

---

### Post by fafayacity on 2009-04-27
Thanks for all the replies. I am not sure what I am doing wrong and it does not seem to me that this is something I will be able to fix. I have been looking for friends here in Knoxville who are familiar with Ubuntu to help me install it. If not, I may have to find someone on the forum willing to remote into my computer and help me install it.

Thank you

> **Mark Phelps said:**
> The error you're getting trying to compile the source indicates that a header file is missing.  You can start by installing build-essential through Synaptic.  That will install a bunch of libraries and header files.

If that doesn't solve your problem, you could be in for a LOT of work.  I recently decided to upgrade an app from source because it hadn't been packaged in over a year -- and ended up having to install over 100 additional packages to finally cover all the source and library dependencies.

There's typically a configure script you run that will search your system for all the dependencies and fail when it finds one missing.  There is also generally a log file that script produces when it runs.  But, you will have to resort to Googling to find the libraries containing the source code and header files.

---

