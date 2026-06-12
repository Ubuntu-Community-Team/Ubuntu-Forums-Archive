---
title: "Unable to install anything"
date: 2009-12-14
forum: New to Ubuntu
---

### Post by Janitor06 on 2009-12-14
I just installed Ubuntu 9.10 a few days ago, and I'm a total linux beginner. I'm working out understanding the OS and how it runs, but I am having a problem, and since I know nothing about Ubuntu, I am unable to fix it on my own.

The problem: I am unable to upgrade or install anything.

Every time I try it comes up saying "Could not find package". It has done this with any program in the software center, and when trying to get the media suite. What can I do?

---

### Post by arochester on 2009-12-14
Open a Terminal. 
Connect to the Internet.
Input the commands: 
sudo apt-get update
sudo apt-get upgrade

What is the result?
Copy and paste the outcome here.

---

### Post by Troll_the_Great on 2009-12-14
> **Janitor06 said:**
> I just installed Ubuntu 9.10 a few days ago, and I'm a total linux beginner. I'm working out understanding the OS and how it runs, but I am having a problem, and since I know nothing about Ubuntu, I am unable to fix it on my own.

The problem: I am unable to upgrade or install anything.

Every time I try it comes up saying "Could not find package". It has done this with any program in the software center, and when trying to get the media suite. What can I do?

First of all, are you connected to the internet? Most of the packages require an active internet connection for installation.
Here are a couple of useful links for a beginner:
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)
Cheers!

---

### Post by k3lt01 on 2009-12-14
Have you made sure your repositories are enabled? If not open your software sources and make sure Universe and Multiverse are enabled.

I would also suggest you take a look at this [free pdf book]("http://ubuntuforums.org/showthread.php?t=1052065"). It may help you with many questions.

---

### Post by Janitor06 on 2009-12-14
> **arochester said:**
> Open a Terminal. 
Connect to the Internet.
Input the commands: 
sudo apt-get update
sudo apt-get upgrade

What is the result?
Copy and paste the outcome here.

It downloaded a bunch of stuff, way more than worth pasting in here. It didn't work before, but I must have mistyped. I got the update, working on the upgrade now.

---

### Post by Janitor06 on 2009-12-14
> **Troll_the_Great said:**
> First of all, are you connected to the internet? Most of the packages require an active internet connection for installation.
Here are a couple of useful links for a beginner:
[http://amitech.50webs.com/installing/index.php.html](http://amitech.50webs.com/installing/index.php.html)
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/64958-how-install-software-linux.html)
Cheers!

I am connected to the internet, yes (using it now!)

---

### Post by Janitor06 on 2009-12-14
> **k3lt01 said:**
> Have you made sure your repositories are enabled? If not open your software sources and make sure Universe and Multiverse are enabled.

I would also suggest you take a look at this [free pdf book]("http://ubuntuforums.org/showthread.php?t=1052065"). It may help you with many questions.

They are all enabled. I did download the pdf earlier, and will peruse it when I have the time. It did not address this specific issue however, and it is slightly behind on some things, since I'm using 9.10

---

### Post by Janitor06 on 2009-12-14
> **arochester said:**
> Open a Terminal. 
Connect to the Internet.
Input the commands: 
sudo apt-get update
sudo apt-get upgrade

What is the result?
Copy and paste the outcome here.

It worked!:D

Thanks for the help...to help with my understanding, why didn't it work before? Was my version just not up to date?

---

### Post by lotharmat on 2009-12-14
To be honest, If I get any issues with the gui; I just revert to command line. It may have just been the gui throwing a dicky fit. It sounds like crap but I regularly have issues updating from System-->Admin-->Update manager

but sudo apt-get update never seems to miss a beat!

---

