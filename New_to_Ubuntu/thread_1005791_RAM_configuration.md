---
title: "RAM configuration"
date: 2008-12-08
forum: New to Ubuntu
---

### Post by ubername on 2008-12-08
Hi

I have 3Gb of RAM but it doesn't seem to be used. For example, I was compiling Pan and got this in my System monitor window. It looks like the RAM is somehow being being capped. Am I wrong? Is there a setting somewhere to undo this? Why is my Swap space being used when there are 2Gb of unused memory? TIA.

---

### Post by MarblePanther on 2008-12-08
Good Lord! Your cpu is running at 100% way too often! Something strange is goin on there.

What programs are you running?

---

### Post by cdmike2k8 on 2008-12-08
It appears that it is seeing 2.9GB ram, not 2.  Also it really isn't using the swap partition, only 5MB.

---

### Post by MarblePanther on 2008-12-08
There is nothing wrong with your ram detection as ^ mentioned.

It sees all of it and your swap is only 5mb as he said.

Your cpu on the other hand looks like a problem

---

### Post by m_duck on 2008-12-08
> **MarblePanther said:**
> Your cpu on the other hand looks like a problem
Unless it's folding or something...

---

### Post by ubername on 2008-12-08
> **MarblePanther said:**
> Good Lord! Your cpu is running at 100% way too often! Something strange is goin on there.

What programs are you running?

I was in the middle of compiling. (using 'make')

---

### Post by MarblePanther on 2008-12-08
You're good then

no problems there

---

### Post by ubername on 2008-12-08
> **MarblePanther said:**
> There is nothing wrong with your ram detection as ^ mentioned.

It sees all of it and your swap is only 5mb as he said.

Your cpu on the other hand looks like a problem

I know, I was just interested as to why it was using any at all, what with a Gig and some free.

---

### Post by MarblePanther on 2008-12-08
try here:

[http://ubuntuforums.org/archive/index.php/t-381336.html](http://ubuntuforums.org/archive/index.php/t-381336.html)

---

### Post by ubername on 2008-12-08
> **MarblePanther said:**
> try here:

[http://ubuntuforums.org/archive/index.php/t-381336.html](http://ubuntuforums.org/archive/index.php/t-381336.html)

Thanks, very interesting, it looks like other people are having problems using more than 1Gb RAM, or have I misunderstood the thread?

---

### Post by MarblePanther on 2008-12-08
No, you're not having a problem.  It is utilizing all it needs.  A small amount of swap used is normal.

Now, it wouldn't be a bad idea for you to install 64-bit if you want to install more RAM in the future.

You are *not* having any problems, that is normal.  Read the second post in that thread.

---

### Post by ubername on 2008-12-08
Hmm! using free it looks like I am using RAM  but System Monitor is not reporting it (or at least not all of it. I don't know what the 'buffers/cache' bit means)

joeSoap@Ubuntu:~$ free
             total       used       free     shared    buffers     cached
Mem:       3087360    2446700     640660          0      21460    1340440
-/+ buffers/cache:    1084800    2002560
Swap:       979956          0     979956

---

### Post by MarblePanther on 2008-12-08
mine:
             total       used       free     shared    buffers     cached
Mem:       1023776     759828     263948          0      30480     311684
-/+ buffers/cache:     417664     606112
Swap:      1485972          0    1485972







there's nothing wrong with your system afaik

---

### Post by ubername on 2008-12-08
> **MarblePanther said:**
> No, you're not having a problem.  It is utilizing all it needs.  A small amount of swap used is normal.

Now, it wouldn't be a bad idea for you to install 64-bit if you want to install more RAM in the future.

You are *not* having any problems, that is normal.  Read the second post in that thread.

Thanks, I am using 64-bit, but can't see any point in installing any more RAM if it isn't using what I currently have. Thanks for the help, I am just exploring, not having a problem per se. I was just intrigued because I have never seen my memory usage over 1Gb, and never seen my swap file used before (but I don't do a whole lot of demanding work - I just feel that the box doesn't quite perform to its spec. sometimes.)

---

### Post by MarblePanther on 2008-12-08
You have plenty of ram, no worries  :)

---

