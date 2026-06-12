---
title: "Absolute Beginner"
date: 2011-08-14
forum: New to Ubuntu
---

### Post by n4z1 on 2011-08-14
Hi, I am new to UBuntu, and Linux as a whole, and I have dedicated myself to start learning Linux as a whole as it will come in handy when I start my job as a security engineer. 

I have Oracle VirtualBox, in which I am downloading UBuntu. I am going to install UBuntu into the Virtual Box first before starting to install it for dual booting, which I have a few questions with:

1) I read on a guide I have downloaded that I would have to repartition my hard drive to install UBuntu, which will then activate dual booting, where I can choose between either Vista (the OS I am on now) and UBuntu. Is this correct?

2) When I started learning UBuntu, somewhere along the lines it stated that Linux does not support .exe programs, so it cannot be downloaded and installed. Is this correct, and if so, is there a program that can convert a .exe to Linux compatibility?

Thanks for your time, guys.

-n4z1.

---

### Post by Elfy on 2011-08-14
You can install as a dual boot and repartition. You can install it inside windows with wubi. You can install it as you are doing in a vm.

If you do install as a dualboot as long as you do not mistakenly delete your windows install you will get the choice at boot time. Same with wubi. 

Linux is not windows - exe is windows, however you can use Wine to use some windows applications. 

[http://www.winehq.org/](http://www.winehq.org/)
[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://wiki.ubuntu.com/WubiGuide](https://wiki.ubuntu.com/WubiGuide)

Hope that helps some.

Also - please try and use descriptive titles :)

---

### Post by spiky001 on 2011-08-14
Hi yes you would have to resize the partition to make room for Ubuntu, This can be done with the vista disc.
There is a program that will let you run windows programs it,s called wine [here]("http://www.winehq.org/") It will also list programs that can be run under wine.
Hope this covers enough for now

---

### Post by babakott on 2011-08-14
There are several options for installing Ubuntu. You may want to read [this]("https://help.ubuntu.com/community/Installation") it has all the options available and information on partitioning if that is the way you choose to go.

Secondly, Ubuntu does not natively support .exe files. However, some windows programs can be ran with wine. You can read up on it [here]("http://www.winehq.org/")

Hope this helps.

---

### Post by Frogs Hair on 2011-08-14
1. You will be able select Vista or Ubuntu from the boot loader on a partitioned dual boot .

2. The program at the link will allow the use of _many_ Windows programs , but not all and there is a section on the forum specifically for Wine . It is available in the Ububtu software center along with some other emulators .  [http://www.winehq.org/about/](http://www.winehq.org/about/) If you dual boot you won't have a need for Wine .

---

### Post by Elfy on 2011-08-14
Long thread with lots of information - pick and choose - [http://ubuntuforums.org/showthread.php?t=801404](http://ubuntuforums.org/showthread.php?t=801404)

Short(ish) post that will likely prove useful - [http://ubuntuforums.org/showpost.php?p=8920811&postcount=1](http://ubuntuforums.org/showpost.php?p=8920811&postcount=1)

Lost of links to wine then :p

---

### Post by bug67 on 2011-08-14
> **Frogs Hair said:**
> If you dual boot you won't have a need for Wine .

This + 100

.

---

