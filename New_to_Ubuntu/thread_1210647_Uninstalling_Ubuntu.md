---
title: "Uninstalling Ubuntu"
date: 2009-07-11
forum: New to Ubuntu
---

### Post by jimbo md on 2009-07-11
Hey guys,

somebody else installed Ubuntu for me and I think the person invited the 32-bit version, although I have a 64-bit CPU.  I would like to deinstall the whole thing and reinstall the right version.  I do not have Windows on there so I do not exactly know how to tackle that problem.
Solutions would be greatly appreciated.

---

### Post by Revolutionary101 on 2009-07-11
I think you should just format the Ubuntu partition. Then install Ubuntu 64 bit. I think you could try to format it with  the Ubuntu live CD.

---

### Post by jimbo md on 2009-07-11
How do I format the Ubuntu partition?  I am a true nooby so please don't get frustrated ;)

---

### Post by drs86 on 2009-07-11
Boot from the Live CD (make sure it's the 64-bit version you want, of course), and select the option to install Ubuntu. During the installation process, it will ask you to format the disk. I use the 32-bit version, but I assume the process is similar with 64-bit. It will suggest a format table for you; you can use their suggestion or format it manually yourself.

If you do it manually (as I do), you can choose how much of your hard disk to use for the operating system and how much to use for swapping. (I'm a newbie too, so I don't exactly know what swapping is :lol:, but I think you have to use a little bit of space for swapping, not very much.) The default filesystem format for the operating system is ext3, so that's what I use. The format for swapping is linux-swap. If you also want to use files that are compatible with Windows, you might want to format part of your disk in a format that Windows understands (such as NTFS).

For each partition, select the check mark "Format partition"; this will erase all data in that area of the disk (including your old Ubuntu installation) and reformat it in preparation for the new installation.

Then finish the install process.

Good luck!

David

---

### Post by jimbo md on 2009-07-11
Thanks Dave.  I will give it a try.

---

### Post by cptrohn on 2009-07-11
You can just download the 64bit version, pop in the live CD and either select use the full HD or set yourself up with a swap file in the custom installation... I don't really use a swap file and haven't had any kind of performance problems with it.... I know with my puppy install on my older machine I have a swap file set up and they recommended it to be twice the size as the amount of RAM you have installed on your computer....  You will have to go back though and reinstall your restricted extras and that sort of thing though.

---

### Post by Fatal Toenail Infection on 2009-07-11
Just don't check "Format" on your Windows partition and it will be left untouched.  Double click the current Ubuntu partition and set the mount point as "/" and check "Format".  That should be it.

---

### Post by jimbo md on 2009-07-11
I do not have a Windows partition because I do not have Windows on my computer.
I guess I would like to know what the easiest way is to reinstall Ubuntu and get rid of the previous version.

---

### Post by LewRockwell on 2009-07-11
put LiveCD in
reboot machine
select install
follow prompts and answer questions
when it gets to the place about using the hard drive(partitioning) you'll select "use complete drive"
there will be a few more prompts depending on your particular install
then you'll reboot into your freshly installed Ubuntu

I like to have the LAN connected(if you're using wired internet) when I reboot and as long as the system connects to the internet it won't be long before Ubuntu is prompting you to install some updates(this is expected and normal)

that's about as simple as I can make it without doing it for you

keep us posted!

.

---

### Post by jimbo md on 2009-07-11
Alrighty thanks.  I will try that and I will keep you posted.  I do not have an ethernet cable, but I am connected wirelessly.  It shouldn't make a difference, right?
Thanks again.

---

### Post by lisati on 2009-07-11
As you might have gathered, there's often more than one answer that will let you get the job done.

Since you don't have Windows on your system, I'd bypass tinkering with the partitions before the installation, go for the "Guided - use entire disk" option when asked during installation. 

As for having a wireless connection instead of a wired connection, I don't anticipate any major problems, other than possibly being slightly slower than a wired connection. 

Feel free to continue asking questions if you need to.

---

### Post by jimbo md on 2009-07-12
Thanks lisati.  I really appreciate all your guys' advice.  Very very helpful.  
I also have another question:  When I had the 32-bit version installed, my CPU Frequency Scaling Monitor did not work.  Was that due to the 32-bit version, because I have a 64-bit AMD processor?!?  Ubuntu supports AMD as well as Intel processors I thought so I do not know what causes the frequency monitor not to work.

---

