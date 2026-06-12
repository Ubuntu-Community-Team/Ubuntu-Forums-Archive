---
title: "Clean ReInstall..."
date: 2009-03-13
forum: New to Ubuntu
---

### Post by Leo Dragonheart on 2009-03-13
How can I do a compleate wipe of my HD and start over with a clean install of Ubuntu 8.10? I would also like to install Mandriva alongside Ubuntu...I have both Live CD's...Thanx!!!

---

### Post by thane1 on 2009-03-13
Are you actually wanting to do a disc wipe before the reinstallation?  If so I understand the killdisk free utility will do that (dos based).  As a followup to that or instead (if you're not actually wanting to do a disk wipe), repartition the disk during the new installation, so that the old partition no longer exists and reinstall.  Cheers
[http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)

---

### Post by cariboo on 2009-03-13
If you just want to do a reinstall, when you get to the partitioning step, select manual and just partition the drive for what you need to install Ubuntu and leave the rest of the drive blank. When you are ready to install Mandriva, use it's partitioner to partition the rest of the drive.

Jim

---

### Post by Leo Dragonheart on 2009-03-13
I had ubuntu 8.10 installed and it ran great for 2 months. I was having problems connecting and staying connected to the net. I reinstalled ubuntu 8.10 just now. I did the manual steps and deleted all the partitions then I made sure that I did the guided install and used the entire drive. I loged in to ubuntu and could not connect to the net. I did not download and updates this time but yesterday when I did the reinstall I did do all 268 updates and still had same problems. I was able to  connect just fine for 2 months prior to this.

I booted up a Mandriva Live CD which I am on now and using to connect to the net with and it is running fine. Can someone please help me figure out what the problem might be?

Additional info: I connect to the net using a wireless usb addapter. The adapter is a linksys 2.4.GHz. Mandriva is using a rausbo driver I do believe. Could that be missing from ubuntu? If more info is needed please do not hesitate to ask. Thank you in advance for any assistance offered...

---

### Post by KayakJim on 2009-03-13
Can you plug an ethernet cable from your wireless router to your computer and then do the install?

I too connect through wireless and if I did not have the ethernet connection during installation, my system would act very strange and I would have options missing. When I installed with the ethernet connection my system acted great and nothing was missing.

Once the installation, "apt-get update", and "apt-get upgrade" was complete I would then work on getting my wireless working.

Just a suggestion that might work for you as well.

---

### Post by Leo Dragonheart on 2009-03-13
> **KayakJim said:**
> Can you plug an ethernet cable from your wireless router to your computer and then do the install?

I too connect through wireless and if I did not have the ethernet connection during installation, my system would act very strange and I would have options missing. When I installed with the ethernet connection my system acted great and nothing was missing.

Once the installation, "apt-get update", and "apt-get upgrade" was complete I would then work on getting my wireless working.

Just a suggestion that might work for you as well.

Thanx for the suggestion. I live in a housing situation where I can't do that. we all share a connection and the box is in the basement... Thank you for the tip though...

---

### Post by KayakJim on 2009-03-13
Okay, another idea is can you use an Ubuntu LiveCD to get Ubuntu running with your wireless connection and then do the install?

I'm not sure how or if this would work but I thought I would put it out there.

---

### Post by Leo Dragonheart on 2009-03-13
> **KayakJim said:**
> Okay, another idea is can you use an Ubuntu LiveCD to get Ubuntu running with your wireless connection and then do the install?

I'm not sure how or if this would work but I thought I would put it out there.

I hadn't thought of that but I will give it a try thanx...

---

### Post by Leo Dragonheart on 2009-03-13
> **cariboo907 said:**
> If you just want to do a reinstall, when you get to the partitioning step, select manual and just partition the drive for what you need to install Ubuntu and leave the rest of the drive blank. When you are ready to install Mandriva, use it's partitioner to partition the rest of the drive.

Jim

How do I know how much space each one needs?

---

### Post by ivanvajar on 2009-03-13
If you don't plan storing a lot of files on Linux partitions, 15GB will do the trick for each one of them. Of course, you'll set 1 swap partition. They say that it needs to be 1,5 to 2,5 times your RAM, but lot of us found that it's enough to make it equal to your RAM, or slightly bigger.

---

