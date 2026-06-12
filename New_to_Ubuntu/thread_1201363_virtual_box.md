---
title: "virtual box"
date: 2009-07-01
forum: New to Ubuntu
---

### Post by sivasatish85 on 2009-07-01
hello , I am satish... could any one tell me which of the virtual box should I install on windows to install linux? Also let me know how to find it?

---

### Post by kpkeerthi on 2009-07-01
Use [VirtualBox 3.0.0 for Windows hosts]("http://download.virtualbox.org/virtualbox/3.0.0/VirtualBox-3.0.0-49315-Win.exe"). See [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

---

### Post by credobyte on 2009-07-01
If you want to run it on Windows, download Windows version ( for Windows "hosts", as said on their website ).

---

### Post by bodhi.zazen on 2009-07-01
download here : [http://www.virtualbox.org/wiki/Downloads](http://www.virtualbox.org/wiki/Downloads)

i386 = 32 bit windows

amd64 = 64 bit windows

---

### Post by sivasatish85 on 2009-07-01
Thank u, i will do that.. I will download it. I am a new user to this forum and could u please let me that to find any reply should I refresh the page every time or is there any other way...? Also once we create a new thread is there any option to close...

---

### Post by sivasatish85 on 2009-07-01
thank u.

---

### Post by credobyte on 2009-07-01
> **sivasatish85 said:**
> Thank u, i will do that.. I will download it. I am a new user to this forum and could u please let me that to find any reply should I refresh the page every time or is there any other way...? Also once we create a new thread is there any option to close...

You can subscribe to RSS feed ( for Firefox, at the end of url-box ) :)

---

### Post by sivasatish85 on 2009-07-01
I am not able to find RSS feed next to URL box ... could u please guide me through.. and also let me know the features when I subscribe RSS feed.

---

### Post by potatan on 2009-07-01
Or you can change your forum profile to notify you by email whenever anyone posts a reply to one of your threads.

---

### Post by sivasatish85 on 2009-07-01
hi i tried installing " puppy linux version 4 " using virtualbox... but it says that host has less memory.. I have 256MB RAM installed on my computer.  Error: Unable to allocate and lock memory?

---

### Post by sivasatish85 on 2009-07-01
hi i tried installing " puppy linux version 4 " using virtualbox... but it says that host has less memory.. I have 256MB RAM installed on my computer. Error: Unable to allocate and lock memory?
Could any tell me how to go further... can I install linux on my PC... if yes let me know..

---

### Post by carml on 2009-07-01
You can set the amount of memory for the virtual machine using the button Settings when the GUI of Virtualbox is active.

---

### Post by HotShotDJ on 2009-07-01
> **sivasatish85 said:**
> I have 256MB RAM installed on my computer. Error: Unable to allocate and lock memory?This will be a problem.  The 256 MB of physical RAM is just BARELY enough to run the host operating system (Windows, in your case), never mind running a virtualized operating system on top of it.  You may be able to install and run Puppy Linux, Damn Small Linux, or some other very light-weight distro of Linux in a Dual Boot set-up.

I recommend a MINIMUM of 1 GIG of installed physical RAM on a computer in order to use VirtualBox (or any virtualization software) -- and even then, performance will be dodgey. With your current RAM, it is out of the question.  You need to assign physical RAM to the running virtual machine, with the remainder retained by the host. 256 MB is just not enough to allow for this.

---

