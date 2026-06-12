---
title: "Installing 10.10 aside Windows 7 64bit"
date: 2010-10-18
forum: New to Ubuntu
---

### Post by stat30fbliss on 2010-10-18
So I am right now downloading Ubuntu 10.10 32bit and getting ready to attempt a dual install scenario on my Acer laptop.  

Does anyone have any suggestions or any potential pitfalls I should be wary of.  I haven't had any Linux installed on my PC since Vista, and I have heard of potential compatability issues.

Any comments are greatly appreciated

---

### Post by oregonbob on 2010-10-18
I have a desktop and a laptop both running Windows 7/64 and Ubuntu 10.04. One Ubuntu is 64bit, the other is 32bit. I have no problems with either. I very rarely use Windows 7 any more. I only use it for occasional Netflix and a rare Windows application.

Interestingly the biggest reason I don't use WIndows 7 is performance. Ubuntu seems so much faster, more of everything except viruses and malware, something I can do without.

---

### Post by stat30fbliss on 2010-10-18
Yeah I used to use Ubuntu 8.04 With Vista and I got totally hooked on it.  Then that laptop crashed and I remembered running into issues installing 8.04 on my Windows 7 Laptop.  

I saw a couple of articles too saying that Windows tried to '****-block' people from dual booting with Windows 7.

---

### Post by rUFFn3k on 2010-10-18
I havent had any problems either running Win7/10.10 dual boot. I would actually have no reason to ever use windows if all the games worked in linux.

---

### Post by stat30fbliss on 2010-10-18
Just to have you know I am responding to you on my brand new Ubuntu 10.10!  I am so friggin excited.  Its been a while since I have customized my brand new linux desktop.
Excited!

---

### Post by oldfred on 2010-10-19
Use windows management console to shrink the win7 partition. How many partitions are used. Often all 4 primary partitions are used as windows uses 2 - hidden boot & main, vendor uses 2, one 'recovery' which is just a image of your drive and a misc utility. If all four are used you need to delete one. If you can write the image to a DVD you should do that. You may not need image ever again as it will erase everything on your drive and make it just as you purchased it. Will you ever want to do that? You can also back up the utilities partition as it is often small.

You need to have a windows repairCD.
If your PC did not come with a complete Vista or Win7 installation CD, you can download a Recovery Disc at the following links:
Windows Vista/7 Recovery Disc - for repairs only
[http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Vista will not repair XP (they create the boot sectors differently) but can run chkdsk.
[http://support.microsoft.com/kb/927392](http://support.microsoft.com/kb/927392)

You will be able to use the Ubuntu liveCD as a repair for Ubuntu if needed but I always download one or two more like a separate gparted or parted magic liveCD and system rescueCD just in case.

Resize windows partition info:
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

Dual Boot Win7 & Ubuntu
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

[http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml](http://news.softpedia.com/news/Installing-Ubuntu-10-10-160966.shtml)
Maverick partition by hand to use free space:
[http://sites.google.com/site/easylinuxtipsproject/partitioning](http://sites.google.com/site/easylinuxtipsproject/partitioning)

I also suggest a separate NTFS shared partition for any data you may want from either system. I have firefox & thunderbird profiles in my NTFS shared partition.

---

### Post by stat30fbliss on 2010-10-19
That is a very healthy well of knowledge.  Thank you so much!

---

