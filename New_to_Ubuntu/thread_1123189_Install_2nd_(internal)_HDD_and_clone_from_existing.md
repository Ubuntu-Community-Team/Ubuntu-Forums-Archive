---
title: "Install 2nd (internal) HDD and clone from existing hard drive"
date: 2009-04-11
forum: New to Ubuntu
---

### Post by akelsall on 2009-04-11
Can someone give me some guidance on how I can install a second drive so that I can make an exact copy of my existing drive? Here's the details:

I have an existing 500Gb HDD that I want to clone (attached to SATA1 on my MOBO).

I've installed a second 500Gb HDD and attached it to SATA2 on my MOOB.

When I get the intial boot messages, I see the following:

   Primary Master ...WDC....  Calbe and Status OK
   Primary Slave  ...WDC....  Calbe and Status OK

When I get back to my desktop, I don't see the second drive. When I go into Partition Editor, I can select it (as /dev/sdb) and it shows all space unallocated (as I'd expect). When I click on New to format it, I'm not give the option to use the ext3 filesystem. 

So, what two big questions here:

1. I'm pretty certain I need to format this drive before I attemp to   
   clone. How can I format it as ext3? Do I need to boot to a LiveCD and 
   actually install Ubuntu first?

2. What's the easiest way to clone a drive (I want to make an [COLOR="Blue"]**exact**[/COLOR] copy of my existing drive.

Thanks,

Andy

---

### Post by mikewhatever on 2009-04-12
What operating system are you currently running? It's implied in your post that no kind of linux is installed, is that correct? If you only have a Windows OS version, I don't suppose they support ext3. You don't need to install Ubuntu for formatting, just run it from the cd. I'd try Clonezilla or Partimage for the task.
[http://www.clonezilla.org/](http://www.clonezilla.org/)
[http://www.partimage.org/](http://www.partimage.org/)

---

### Post by akelsall on 2009-04-12
I'm currently running Ubuntu 8.10 on my primary (and only) hard drive. THat's the drive I want to clone. The drive I'm trying to use as the backup drive is a brand new (virgin) drive. 

Are you saying that if I boot from LiveCD, I can format this drive as ext3 without installing Ubuntu? Or, can I just use one of the utilities you mentioned without having to format the drive?

Thanks,

Andy

---

### Post by mikewhatever on 2009-04-12
You should be able to format the new drive both from the live cd and Ubuntu installation. I'm not sure what's the deal with no option for ext3. What options do you get?
You obviously need to create a file system before cloning.

---

### Post by akelsall on 2009-04-15
Well, I ended up booting a LiveCD and formatting it as ext3 from there. After doing, I set up my PC to boot from my DVD (which had Clonezilla in it) and it worked like a champ!!

I was a bit hesitant doing the cloning, but it was VERY easy. If you read the directions on their website first, then step through the menus (using all the defaults), you will not have a problem. Just make sure you TRIPLE-CHECK which drive is source and which drive is the target, and watch the instructions when it asks which disk to use as source or target. Other than that, it was a breeze. It took 1 hr. 15 minutes to clone my 500 Gig drive.....BUT, it actually only backed up 105 Gig of data. Still, not too shabby, considering I have 15 partitions. 

Andy

---

