---
title: "Suggestions on the Ideal Setup?"
date: 2010-10-13
forum: New to Ubuntu
---

### Post by groover on 2010-10-13
Hey Guys! I just downloaded Ubuntu for the first time and I'm pretty stoked about it. I downloaded it as the option to keep it as an application inside windows. I'm toying with the idea of keeping this as my main operating system and working within Ubuntu. Is this the optimum way to do this? Say, one day I want to delete the Windows and just use Ubuntu, am I going to have problems with the operating system? 


Thanks!!

---

### Post by mikewhatever on 2010-10-13
Installing inside Windows is a good way to try Ubuntu, but not more then that. Regardless of whether you remove Windows or not, it's advisable to install Ubuntu properly, in case you plan on keep using it.

---

### Post by jjex22 on 2010-10-13
It really does depend on your needs. Ideally you will already be using a separate hdd partition for your data (my documents, etc) this means that if you need to reinstall windows or any OS, your data stays where you left it.

In my experience most of us started out with the idea of continuing to use windows and now can't remember the last time we did!

If you plan to stick to windows and use this from time to time then it's defiantly a safe and reliable option. If you plan to use it often, or you have limited RAM, then it isn't really ideal.

If you want to put it on your HDD and dual boot between the two (always best to keep windows on there if you really have to use ms office instead of open office and especially if you need itunes - wine progress is getting there but you can't rely on it!) then the best thing to do is use Gparted to set up your HDD. 

[http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)

you can use the ubuntu installer but it's always best to use gparted to get the HDD how you want it rather than let ubuntu decide. 

recommended method is to back up your data, defrag the harddrive, then boot with the gparted cd in and shrink the windows partition (keeping it as the first partition), create a primary partition, devide this into 2 logical partitions (one in NTFS for your data - so the big one) and leave one as free space. Then run ubuntu installer and tell it to use largest continuous free space and it will do the rest for you.

If you are more comfortable with partitioning then by all means tailor it to your needs but that's a good first step for begginers.

once done move your my documents to the new ntfs partition (if not already done).

I find it's usually good to keep different OS on different partitions especially with linux - most distros update every 6months and it keeps it all simple.

another thing to look into if you are running vista or windows 7 and you plan to install more than one linux or bsd distro on your machine is easy bcd - it uses the vista bootloader and saves you having to edit any grub files! it does a great job on my testing laptop which has osx,win7,bsd,and 6 linux on it!

---

### Post by locodog on 2010-10-13
These ware some detailed informations about ubuntu/windows. I've tried 10 times to have linux and windows installed on same machine... and as long as I've haved windows i'd never start linux. So I decided to install only ubuntu. Now I have 220GB NTFS partition for data storage and all others for windows everyday use. And it works great. But i'm not sure what will happen when I for example want to change my linux version (for newer ubuntu or something else)...

---

### Post by cpmman on 2010-10-13
Click on the WubiGuide link in my signature and look at the 8.8. Migrating from Wubi to full partition guide.

---

### Post by groover on 2010-10-13
Thanks to everyone for the suggestions!

I am so excited about Ubuntu and all the things it has to offer. However, I may (wrongly) feel as though I'm getting a tattoo or piercing- I'm so afraid that if I kill Windows I'll lose so much- 

Any thoughts to ease my qualms about just killing Windows completely? Can the system restore disk reinstall it if I feel like I made a mistake?



However, for a student I think Ubuntu is perfect. I've been able to remotely throw all of my music and files elsewhere so I am not concerned about those now in the switch- just losing my programs. 


Thanks for all y'all's support!!!

---

### Post by lisati on 2010-10-13
It's up to you. Killing Windows suits some people, keeping it around suits other people. 

What you might want to look at is using a "dual boot" for a while, i.e. Ubuntu has its own partition separate from Windows. Once you have been using Ubuntu for a while and the initial excitement has worn off, you can then decide.

---

### Post by anewguy on 2010-10-13
Crap!  I was hping from the title of the thread that I'd be able to suggest the direct brain-to-PC link, but guess I can't now!

Dave ;)

---

### Post by groover on 2010-10-13
> **jjex22 said:**
>  

[http://sourceforge.net/projects/gparted/files/gparted-live-stable/](http://sourceforge.net/projects/gparted/files/gparted-live-stable/)

you can use the ubuntu installer but it's always best to use gparted to get the HDD how you want it rather than let ubuntu decide. 

recommended method is to back up your data, defrag the harddrive, then boot with the gparted cd in and shrink the windows partition (keeping it as the first partition), create a primary partition, devide this into 2 logical partitions (one in NTFS for your data - so the big one) and leave one as free space. Then run ubuntu installer and tell it to use largest continuous free space and it will do the rest for you.

If you are more comfortable with partitioning then by all means tailor it to your needs but that's a good first step for begginers.

once done move your my documents to the new ntfs partition (if not already done).

I find it's usually good to keep different OS on different partitions especially with linux - most distros update every 6months and it keeps it all simple.




Let me make sure I know what's going on. 
First, I need to uninstall the Wubi from my Windows. Next, I need to partition my harddrive into three parts: one for my existing windows, one for Ubuntu, and one for my documents. Then, I can install Ubuntu on one of the partitions. 
Therefore, I will be able to open all documents in both from the documents partition?
If I decide to delete the Windows, will I be able just to erase the contents of the Windows partition and then "repartition" into Ubuntu and documents?

---

### Post by mikewhatever on 2010-10-14
> **groover said:**
> Let me make sure I know what's going on. 
First, I need to uninstall the Wubi from my Windows. Next, I need to partition my harddrive into three parts: one for my existing windows, one for Ubuntu, and one for my documents. Then, I can install Ubuntu on one of the partitions. 
Therefore, I will be able to open all documents in both from the documents partition?
If I decide to delete the Windows, will I be able just to erase the contents of the Windows partition and then "repartition" into Ubuntu and documents?

Something like that.

---

### Post by clive littlewood on 2010-10-14
Hi

If when you have windows only you can then install Ubuntu from the live CD and choose the option to install alongside windows.

This will give you a dual boot and the option to choose either OS and boot time.

Hope this helps

Clive

---

