---
title: "Is AntiVirus necessary for Dual Boot PC?"
date: 2009-03-04
forum: New to Ubuntu
---

### Post by atulbamne on 2009-03-04
Dear all in Ubuntu Community,

I have developed interest in Ubuntu before a month and I ended up installing Ubuntu on my PC before 15 days from official Ubuntu CD.  

I have installed Ubuntu on separate Hard Drive which was procured by me especially for installing Ubuntu.  I booted by PC with the CD and installed Ubuntu by giving Option to install it on my new hard drive. The installation was successful and I am happy using this OS.The OS is updated by the way of internet updates.

I had Windows XP before this installation. Now, I can use both the OS without any problems. I can access my windows drive from ubuntu OS but I cannot access ubuntu drive from my windows. I have no problem for this also.

My question is that : I have antivirus program running in my windows. However, as I access windows drive from Ubuntu there is possibility that the windows viruses may enter my Linux hard drive. So, Should I install antivirus for linux also? That is available by avast home edition for linux.

Should I install it or not? Is there any necessity fo Ubuntu for Antivirus software especially when I am accessing windows drive from Linux? 

Please help. :D

---

### Post by skymera on 2009-03-04
Windows CANNOT get a virus from Ubuntu UNLESS you move it there.

If you're planning on transferring files, yes, install a virus scanner to make sure they're clean

---

### Post by itisbasi on 2009-03-04
One of the many advantages of ubuntu is...that you don't have to worry about viruses....

---

### Post by atulbamne on 2009-03-04
I am worried about my Linux, not windows. My question is Should I install program for Linux so that my windows viruses my not enter into Linux............

---

### Post by skymera on 2009-03-04
Linux isn't affected by Windows viruses.

Don't worry

---

### Post by atulbamne on 2009-03-04
Thanks Man.

Thanks a lot !

However, can you tell me reason behind it?

pls

---

### Post by konqueror7 on 2009-03-04
just install an AVP just in case, you still using windows, and anything that gets downloaded in ubuntu will not affect it, but windows will...

---

### Post by Thelasko on 2009-03-04
> **atulbamne said:**
> Thanks Man.

Thanks a lot !

However, can you tell me reason behind it?

pls

I would compare it to putting diesel fuel into a car that runs on gasoline.  You can put diesel into the tank, but it won't run.

You can put a virus on your Ubuntu hard drive, but it won't do anything.  This is because, like diesel and gasoline engines, Ubuntu and Windows work differently.

---

### Post by mcduck on 2009-03-04
> **atulbamne said:**
> Thanks Man.

Thanks a lot !

However, can you tell me reason behind it?

pls

At basic level it's the same reason why you can't run Windows programs in Linux or OS X, they are different operating systems, work differently, and have different types of program files.

---

### Post by achase79 on 2009-03-04
A virus scanner would also be advisable if you are planning to use wine, but the viruses will only affect the wine files and not your entire system.

---

### Post by billgoldberg on 2009-03-04
> **atulbamne said:**
> Dear all in Ubuntu Community,

I have developed interest in Ubuntu before a month and I ended up installing Ubuntu on my PC before 15 days from official Ubuntu CD.  

I have installed Ubuntu on separate Hard Drive which was procured by me especially for installing Ubuntu.  I booted by PC with the CD and installed Ubuntu by giving Option to install it on my new hard drive. The installation was successful and I am happy using this OS.The OS is updated by the way of internet updates.

I had Windows XP before this installation. Now, I can use both the OS without any problems. I can access my windows drive from ubuntu OS but I cannot access ubuntu drive from my windows. I have no problem for this also.

My question is that : I have antivirus program running in my windows. However, as I access windows drive from Ubuntu there is possibility that the windows viruses may enter my Linux hard drive. So, Should I install antivirus for linux also? That is available by avast home edition for linux.

Should I install it or not? Is there any necessity fo Ubuntu for Antivirus software especially when I am accessing windows drive from Linux? 

Please help. :D

You don't need anything.

---

### Post by atulbamne on 2009-03-04
Thanks a lot !

---

### Post by atulbamne on 2009-03-04
Thanks a lot for the useful advice !

---

### Post by atulbamne on 2009-03-04
Thanks a lot for the useful advice ! Thanks ....

---

### Post by tarps87 on 2009-03-04
If you share file with windows machines or email people who use windows you can install one to help protect them. I have a Ubuntu server which share between GNU/Linux OS's, windows and a Risc os machine so I have calmav which seems to work. It is also in the Ubuntu repositories

> **Thelasko said:**
> I would compare it to putting diesel fuel into a car that runs on gasoline.  You can put diesel into the tank, but it won't run.

You can put a virus on your Ubuntu hard drive, but it won't do anything.  This is because, like diesel and gasoline engines, Ubuntu and Windows work differently.

Just to be a pain. :)
There is a small flaw in this a some older diesel cars can run on petrol(gasoline), which would mean some GUN/Linux viruses would run on windows. (I don't suggest putting petrol in a diesel engine)

---

### Post by Thelasko on 2009-03-04
> **tarps87 said:**
> Just to be a pain. :)
There is a small flaw in this a some older diesel cars can run on petrol(gasoline), which would mean some GUN/Linux viruses would run on windows. (I don't suggest putting petrol in a diesel engine)

Okay, so turn it around, it's like putting diesel in a car that runs on gasoline.

I forgot about how some diesels will run on anything that burns.

P.S. If you want to nit pick, I ignored the fact that the diesel and gasoline nozzles are incompatible.

---

### Post by theozzlives on 2009-03-04
I'd install clamav just incase a Windows virus prevents Windows from booting, you can scan your Windows drive from within Linux.

---

### Post by tarps87 on 2009-03-04
> **Thelasko said:**
> Okay, so turn it around, it's like putting diesel in a car that runs on gasoline.

I forgot about how some diesels will run on anything that burns.

P.S. If you want to nit pick, I ignored the fact that the diesel and gasoline nozzles are incompatible.

Now that depends on how hard to hit it :)
but then there is cygwin for windows
(not intentionally nit picking, meant as a joke :))

---

### Post by stchman on 2009-03-04
This topic has been beaten into the ground.

Linux is a different animal than Windows.  Therefore the viruses that work on Windows have no effect on Linux.

Now a virus can affect Linux if you use a WUBI install.  WUBI installs the OS in the NTFS file system.  If you are running Windows and download some malicious program it can do damage to the files under control of Windows.  On a dual boot Windows viruses have no affect on EXT3 file system.

Now Linux can transmit a virus through infected emails.  Even though the email viruses have no affect on your Linux machine, they can be sent to your Windows friends and spread.

This does not say that if you give your personal bank information to some overseas scammer that they cannot drain your bank account.  I do recommend good web surfing practices.

---

### Post by Arthur Millar on 2009-03-04
> **Thelasko said:**
> I would compare it to putting diesel fuel into a car that runs on gasoline.  You can put diesel into the tank, but it won't run.

You can put a virus on your Ubuntu hard drive, but it won't do anything.  This is because, like diesel and gasoline engines, Ubuntu and Windows work differently.

hehe i have a friend who burned down a bmw workshop because someones wife filled his diesel motor with gas 
its always good to be cautious

---

