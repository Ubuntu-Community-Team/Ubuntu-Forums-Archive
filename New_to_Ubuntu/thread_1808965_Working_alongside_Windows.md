---
title: "Working alongside Windows?"
date: 2011-07-21
forum: New to Ubuntu
---

### Post by RadhikaM on 2011-07-21
Hello everyone,

First of all, I'd like to say I'm brand new to Ubuntu - which is why I believed it'd be alright to post it here! I've been thinking about getting Ubuntu for a while, but this is a family computer and I'm not sure if I'd be able to completely switch over to Linux (as tempting as it seems to get away from the Windows monopoly) without telling them.

I just started to install the Wubi, and what does that do? Does it work alongside Windows? How much space does it take? How does it work against Windows? Do you choose whether to use Ubuntu or Windows at startup, or is it a run-on application? 

Also, with Ubuntu as the entire processor, can you download external softwares and run them (that are not compatible with ubuntu, I suppose I should call it that)? How much space does Ubuntu take in comparison to Vista? 

Thanks for the help! Anything else you'd like to add would be appreciated!

---

### Post by renaldocreative on 2011-07-21
Hello and welcome to the Ubuntu community. When you install Wubi you will get a full version of Ubuntu. When you login you can select Ubuntu or Vista. This can be confusing for your family so talk to your family before you install Wubi. You alway can run Ubuntu on a live CD. Just download the ISO file from [http://www.ubuntu.com/download](http://www.ubuntu.com/download) and click Download and Install. Choose your 32bit or 64bit and click Start Download. Once it finish downloading Burn the ISO file to disc. Restart you computer and let it boot into Ubuntu. A menu will show up when it boot click "Try Ubuntu". 

You can use Ubuntu with just 10GB of hard drive space but I recommend at least 15GB. 

If you don't like Wubi you can un-install it like other Windows software.

---

### Post by tommpogg on 2011-07-21
> **RadhikaM said:**
> 
Also, with Ubuntu as the entire processor, can you download external softwares and run them (that are not compatible with ubuntu, I suppose I should call it that)?


You cannot run software which is not compatible with Ubuntu on Ubuntu.
Nevertheless, sometimes you can find a workaround: for instance you can install some windows application by using WINE (an open source software for running Windows applications on other operating systems).
Linux applications not supported for Ubuntu sometimes can run on it.

Anyway for almost any Windows application there is an equivalent Linux application that you can install. And most of the times it is better. Moreover, finding and installing applications on Ubuntu is really easy if you use the Synaptic Package Manager.

---

### Post by renaldocreative on 2011-07-21
> **tommpogg said:**
> Anyway for almost any Windows application there is an equivalent Linux application that you can install. And most of the times it is better. Moreover, finding and installing applications on Ubuntu is really easy if you use the Synaptic Package Manager.

Great point you can find Open Source Alternatives at [http://osalt.com](http://osalt.com). Also the Wine HQ project is amazing [http://winehq.com](http://winehq.com) as tommpogg mention.

---

### Post by RadhikaM on 2011-07-21
I installed Ubuntu, and I am impressed with the smooth movements of the new software. I hope to convert the entire family to Ubuntu instead of slow Vista. 

I've set up my email, Facebook, and am getting my IRC chat installed, but I had a question:

Do the files not collaborate from Windows to Ubuntu? Are they entirely different from each other? Is there no way to access the files from your Windows files? 

Thank you. 
(This thread may continue to have questions from me as I discover new things, my apologies in advance.)

---

### Post by tommpogg on 2011-07-21
> **RadhikaM said:**
> 
Do the files not collaborate from Windows to Ubuntu? Are they entirely different from each other? Is there no way to access the files from your Windows files?


I don't understand exactly what you mean. If you are asking about differences between Windows and Ubuntu, well, they are completely different.
If you have installed both of them in two (or more) different partitions, it is still possible to share files. Remember that under Windows you will not be able to see or read files on the "Ubuntu partition".
Under Ubuntu you can access every partition, including the one containing Windows. Be aware: do not touch or move Windows system files, you could harm the Windows system.
Probably the best choice is to have a third NTFS partition containing the files you want to share (actually, this is my current setting). But there could be other solutions that I don't know.

> (This thread may continue to have questions from me as I discover new things, my apologies in advance.)
Don't worry, answering questions is one of the purposes of this forum

---

### Post by RadhikaM on 2011-07-21
What I'm trying to say is the files that you have as a user on the Windows operating system, can you access them - and if you can, how do you access them through Ubuntu? (ex; my old downloads on my Vista account)

---

### Post by mastablasta on 2011-07-21
> **RadhikaM said:**
>  
Do the files not collaborate from Windows to Ubuntu? Are they entirely different from each other? Is there no way to access the files from your Windows files? 

 
Files work as long as there is a programme that recognises them. for example all txt files work. if you save emial in thunderbird in linux you can also open it in windows. same goes for open office files.
 
windows files can be accessed from Ubuntu but Ubutnu files can not be accessed from windows unless you install special tools. windows partition is usually shown by it's name (label) in Ubuntu. so if you go to places and see a strangely named disk there this is windows partition. 
 
also Wubi is ment for trying out. it still has some unnusual issues, which can be solved, but take a bit of effort. What wubi does is it creates a large virtual file within windows (disk) and then sticks all OS to it. so if that file gets corrupted you could loose it all.
 
a much safer way is to use side by side dual boot. a bit more harder to set up but also a bit safer as you really split the disk in parts and reserve one part for linux. so if that part or system gets corrupted you can always boto into the other one.
 
but since it's a familly mashcine - you'd better ask for permission to do this or at least make sure ot back up all data first and have a Windows CD/DVD ready just in case something goes wrong. mostly all works ok but there is always that 2% chance... :-)
 
Edit: as suggested before it is really good to have a separate partition for Data even if you use Vista only. if somethign goes wrong with the OS you can easilly reainstall the os leaving data intact.

---

### Post by tommpogg on 2011-07-21
You can access the Windows partition by mounting it.
To do that click Places and select the partition (take a look [here]("http://www.psychocats.net/ubuntu/mountwindows")).

---

### Post by lawrencejohny on 2011-07-21
The best thing for you to keep files accessible is to have a third NTFS partitions as tommpogg pointed out. You could mount this NTFS partition by default in fstab, so that it shows up every time your computer boots up. 
 
It would be best to keep windows system files untouched by Ubuntu. However, you could keep your personal files such as word documents, excel sheets, pdfs, images, movies etc. on the NTFS partition, so you can access it using both Windows as well as Ubuntu.

---

### Post by lawrencejohny on 2011-07-21
> **RadhikaM said:**
> What I'm trying to say is the files that you have as a user on the Windows operating system, can you access them - and if you can, how do you access them through Ubuntu? (ex; my old downloads on my Vista account)
 
The best thing for you to keep files accessible is to have a third NTFS partitions as tommpogg pointed out. You could mount this NTFS partition by default in fstab, so that it shows up every time your computer boots up. 

It would be best to keep windows system files untouched by Ubuntu. However, you could keep your personal files such as word documents, excel sheets, pdfs, images, movies etc. on the NTFS partition, so you can access it using both Windows as well as Ubuntu.

---

### Post by RadhikaM on 2011-07-21
Thanks so far everyone.

What is the difference between Linux and Ubuntu? Does everything Linux compatible work with Ubuntu?

---

### Post by tommpogg on 2011-07-22
Linux is a family of Operative Systems derived from UNIX.
Ubuntu is a member of this family, i.e. a particukar distribution of Linux.

---

### Post by mastablasta on 2011-07-22
> **RadhikaM said:**
>  
What is the difference between Linux and Ubuntu? Does everything Linux compatible work with Ubuntu?
 
Linux is only Kernel (core). Like NT is kernel from Windows these days.
 
Linux programms (the ones you see as source code) can be run on ubuntu if you compile them.

---

