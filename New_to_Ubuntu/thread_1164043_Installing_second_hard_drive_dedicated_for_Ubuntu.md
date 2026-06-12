---
title: "Installing second hard drive dedicated for Ubuntu"
date: 2009-05-19
forum: New to Ubuntu
---

### Post by robert_mc on 2009-05-19
Hi All,
 
[COLOR=black][FONT=Verdana]Looks like a great forum and I'm glad I found it. I searched around a bit and found some phenomenal tutorials for installing a dual boot environment with vista and Ubuntu, but the ones I found were about creating a partition on a single drive and taking it from there. I think what I want to do is easier than that, but I'm still a little unsure of some things. Specifically, I'll be installing a second hard drive that will be completely dedicated for Ubuntu. I don't have any questions about how to physically install the hard drive in the computer, but will vista immediately recognize and claim that drive when I boot up? If so, how do I get vista to release it? Once I do that, will the Ubuntu install process just recognize that new drive and give me the option of installing everything there?[/FONT][/COLOR]
 
Much Thanks :)
Robert

---

### Post by taurus on 2009-05-19
Just go through the installing process and when you get to the partition part, Step 4 of 7, tell the installer to use the second harddrive, usually denote as /dev/sdb.

---

### Post by robert_mc on 2009-05-19
okay, should I need to do anything in vista to free up that 2nd drive partion before starting the ubuntu install process?

---

### Post by mapes12 on 2009-05-19
> okay, should I need to do anything in vista to free up that 2nd drive partion before starting the ubuntu install process?

If you are creating a dual boot installation then the answer is no because you would be booting from your CD drive into the Ubu installer which will then prompt you where you want to install Ubu. During this process windoze is not controlling your PC. The Ubu installation CD is controlling everything.

Your fist HDD will be called sda and your 2nd HDD will be called sdb. Ubu does not "see" drives like windoze and names them with letters. It only sees devices and, more importantly, file structures.

If you want to install Ubu inside windoze using [wubi]("http://www.ubuntu.com/getubuntu/downloadmirrors#wubi") then the normal letter naming policy for windoze applies.

---

### Post by Sidewinder1 on 2009-05-19
First of all, ***Welcome robert_mc*** to Ubuntu forums!
You're setting up your system the same as I did, windoze on original (C:\) drive and ubuntu on 2nd internal drive (sdb). As stated above just let the ubuntu installer handle everything. It'll probably make sdb1 the ext3 (linux) partition and sdb2 partition linux swap (if it asks you for the size of the swap, make it, about one and a half times the size of you RAM). Just let it do it's thing and hopefully all will work great.
Side

---

### Post by Celauran on 2009-05-19
You may also want to consider creating separate partitions for / and /home. Not mandatory, but it can save you some headaches down the road.

---

### Post by robert_mc on 2009-05-19
Thanks for the great replies - I really appreciate it. 
 
> **Celauran said:**
> You may also want to consider creating separate partitions for / and /home. Not mandatory, but it can save you some headaches down the road.
 
Thanks for the advice.  Is this an option during the Ubuntu install process, something I should do before I start the install, or something I do after?
 
Also, I'm just curious why this could help me out in the future.  Is it because it will be easier to update linux in the future by separating OS files from personal files?  
 
Thanks Again!
Robert

---

### Post by Celauran on 2009-05-19
> **robert_mc said:**
> 
Thanks for the advice.  Is this an option during the Ubuntu install process, something I should do before I start the install, or something I do after?
You'll need to create partitions manually when you get to that stage of the install process.
 
> **robert_mc said:**
> Also, I'm just curious why this could help me out in the future.  Is it because it will be easier to update linux in the future by separating OS files from personal files?
That's exactly right.

---

### Post by mapes12 on 2009-05-19
> You'll need to create partitions manually when you get to that stage of the install process.

Yep! Make yourself a GParted LiveCD and use it to boot your machine. You will then have an easy to use GUI to setup your partitions. About 12GB for your /(root system OS files) then the rest for /home except for a small partition at the end the size of 2x your RAM for the swap partition.

Seperating / and /home makes upgrading your system and backing up your files and personal settings much easier and safer.

If all this is a bit confusing then just install the whole lot onto sdb using the default options then visit this link to separate things later: [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by robert_mc on 2009-05-19
It is a pretty big hard drive (250 GB).  Any suggestions on how big to make the OS partition?
 
Thanks Again

---

### Post by Celauran on 2009-05-19
Depends how you'll be using the machine, how big your /var will get, etc. For a typical desktop, 15Gb should be more than enough for / and then plunk the rest in /home

---

### Post by robert_mc on 2009-05-19
I am in the install process now and at the manual "Prepare Partions" (Step 4 of 7) in the install process. So /dev/sda has my windows stuff on it and I am leaving it alone, and my new second hard drive is listed as /dev/sdb with 250059 MB of free space. So I am thinking about creating 3 new partition but have some questions. I am completely new to this but feeling brave. Anyway, this is what I am thinking
 
1st: Primary Partition 18000 MB, located at Beginning, use as Ext3, and Mount point of '/'
 
2nd: Logical Partition, 224059 MB, located at Middle, use as Ext3, and Mount point of '/home'
 
3rd: Logical Partition, 8000 MB, located at End, use as Swap (too big or too small? - I have 8GB of Ram)
 
How does that look? Is it correct to make the first partition "primary"? Will that impact my windows install at all?
 
Thank You Very Much,
Robert

---

### Post by robert_mc on 2009-05-19
Everything installed great and both Ubuntu and vista are working perfectly.  Lots more to learn but at least I am on my way.  Thanks to all the developers who made this such an easy distribution to install, and to the countless people on this board who helped me in this thread and on the archived threads.
 
Muchas Gracias,
Robert

---

### Post by Miljet on 2009-05-19
Welcome to the wonderful world of Ubuntu!

If you haven't found it yet, I highly recommend reading the following before you go much further:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Would have save me several mistakes if I had read it when I first began.

---

