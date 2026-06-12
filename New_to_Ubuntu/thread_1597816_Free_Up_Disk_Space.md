---
title: "Free Up Disk Space?"
date: 2010-10-15
forum: New to Ubuntu
---

### Post by EpikRageQuit on 2010-10-15
I am totally new to Ubuntu. I have a desktop version and it's new and recently updated. I was transferring large files from the Windows 7 file system when I got a warning stating I only had a few mbs left on the disk. I saw a different post similar to this but was confused. I have Windows 7 and Ubuntu on my laptop. I created a directory to move files from Windows 7 to Ubuntu. I ran a cmd to get this info. could someone please explain to me how to make more space on the partition that has documents/videos/downloads etc on it. Thanks


jordan@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/loop0             17G   16G   14M 100% /
none                  1.8G  324K  1.8G   1% /dev
none                  1.8G  520K  1.8G   1% /dev/shm
none                  1.8G   88K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw
/dev/sda2             452G  123G  330G  28% /host
none                   17G   16G   14M 100% /var/lib/ureadahead/debugfs
/dev/sda2             452G  123G  330G  28% /mnt/windows
/dev/sda4             100M  7.2M   92M   8% /media/HP_TOOLS
/dev/sda1             199M   29M  171M  15% /media/SYSTEM
jordan@ubuntu:~$

---

### Post by sandyd on 2010-10-15
> **EpikRageQuit said:**
> I am totally new to Ubuntu. I have a desktop version and it's new and recently updated. I was transferring large files from the Windows 7 file system when I got a warning stating I only had a few mbs left on the disk. I saw a different post similar to this but was confused. I have Windows 7 and Ubuntu on my laptop. I created a directory to move files from Windows 7 to Ubuntu. I ran a cmd to get this info. could someone please explain to me how to make more space on the partition that has documents/videos/downloads etc on it. Thanks


jordan@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
**/dev/loop0             17G   16G   14M 100% /**
none                  1.8G  324K  1.8G   1% /dev
none                  1.8G  520K  1.8G   1% /dev/shm
none                  1.8G   88K  1.8G   1% /var/run
none                  1.8G     0  1.8G   0% /var/lock
none                  1.8G     0  1.8G   0% /lib/init/rw
/dev/sda2             452G  123G  330G  28% /host
none                   17G   16G   14M 100% /var/lib/ureadahead/debugfs
/dev/sda2             452G  123G  330G  28% /mnt/windows
/dev/sda4             100M  7.2M   92M   8% /media/HP_TOOLS
/dev/sda1             199M   29M  171M  15% /media/SYSTEM
jordan@ubuntu:~$
the ubuntu partition here is 17 GB.
are you using wubi or a true dual boot?

---

### Post by EpikRageQuit on 2010-10-15
Uhmmm... Not to sure what wubi is, but when I start my laptop before anything loads I can choose Ubuntu or Windows 7... So, I think true dual boot??...

---

### Post by anspideog on 2010-10-15
I'm having exactly the same issue.
I'm running a dual boot with Windows Vista and have over 80GB free on the hard drive (Ubuntu disk analyser is telling me this also).
Not sure what's going on - I think maybe my system preferences aren't set up so that when I'm transferring my files over they're not going to the correct root folder..

---

### Post by anspideog on 2010-10-15
Having spent the past 2 hours trawling through the forum and other sources I think the whole Wubi download issue is very confusing. I reckon Ubuntu should explicitly state on the Download page that there are two different ways to dual boot for Windows people i.e. 1. by creating a true partition and 2. by using Wubi. 

At the very least they should warn people to remove their backed up data from Windows before installing with Wubi. It looks like my problem was that I kept my Windows files while doing the install (I was scared to lose them, even though I had them backed up) and so Wubi automatically only allocated me the remaining space in my hard drive at that point. Now I've gone back and deleted my files in Windows and freed up another 40GB but because that was done after the Wubi install Ubuntu can't use this space. 

It seems from the website that Ubuntu are really pushing for dual boot Windows people to use Wubi, but, as is evidenced by all the threads here, many people end up wanted to switch to a true dual boot / partition install. 

Harrump - this has really taken the shine off my initial happiness with Ubuntu. Going to have to spend another 2-3 hours tomorrow figuring out how to do this partitioning thingy.

---

### Post by sandyd on 2010-10-15
> **EpikRageQuit said:**
> Uhmmm... Not to sure what wubi is, but when I start my laptop before anything loads I can choose Ubuntu or Windows 7... So, I think true dual boot??...
no, which is why im asking.
your root parition, which contains all your files is mounted as **/dev/loop0** which indicates that you installed ubuntu through wubi.

how did you install ubuntu?

---

### Post by EpikRageQuit on 2010-10-15
I downloaded it from the site put it on a USB and installed it. I used this site [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
I installed it a couple of months ago but started using it today :S I liked windows 7 at first then realized the disaster that it was and switched. :P

---

### Post by sandyd on 2010-10-15
> **EpikRageQuit said:**
> I downloaded it from the site put it on a USB and installed it. I used this site [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
I installed it a couple of months ago but started using it today :S I liked windows 7 at first then realized the disaster that it was and switched. :P
if you go into windows add-remove, can you see one of the entries?
Wubi
Ubuntu
 (and sorry, I can't remember what its called in add-remove since I have never used wubi).
If you do, your not doing a dual boot.
and unfortunately, it means that you cannnot allocate more space for ubuntu.
You will have to uninstall it (remove ubuntu and all the data on it), and install dual boot the propper way.

Follow the instructions at
[https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows](https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows)

ive modded the instructions... a bit to make them less confusing.

---

### Post by EpikRageQuit on 2010-10-15
sad face... I just setup today and I found an uninstall wubi application...I'll chaeck that link for sure. Thanks

---

### Post by EpikRageQuit on 2010-10-15
Uhmm... That link doesn't explain how to remove linux. I assume i just load Windows 7 and move the files and unistall wubi. Or can I just delete it?


*edit also.. what's this for...

**How To Recover**
To recover from this boot problem, you can either;

Boot from your Windows Recovery Cd and select "startup repair".
Download.
For Vista : [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
For Windows 7 : [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Burn the ISO to a disc
Boot up from it
Select Startup Repair.

---

### Post by jtarin on 2010-10-15
> **anspideog said:**
>  

It seems from the website that Ubuntu are really pushing for dual boot Windows people to use Wubi, but, as is evidenced by all the threads here, many people end up wanted to switch to a true dual boot / partition install. 

Harrump - this has really taken the shine off my initial happiness with Ubuntu. Going to have to spend another 2-3 hours tomorrow figuring out how to do this partitioning thingy.Can you link to this statetment or where you found this information....because like you I don't like deceptive practices either if this is what your hinting at.

---

### Post by sandyd on 2010-10-15
> **EpikRageQuit said:**
> Uhmm... That link doesn't explain how to remove linux. I assume i just load Windows 7 and move the files and unistall wubi. Or can I just delete it?


*edit also.. what's this for...

**How To Recover**
To recover from this boot problem, you can either;

Boot from your Windows Recovery Cd and select "startup repair".
Download.
For Vista : [http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/](http://neosmart.net/blog/2008/windows-vista-recovery-disc-download/)
For Windows 7 : [http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)
Burn the ISO to a disc
Boot up from it
Select Startup Repair.
as said in my previous post, uninstall wubi = remove ubuntu

---

### Post by jtarin on 2010-10-16
You uninstall/remove WUBI like any other Windows application.....through the control center.

---

### Post by bcbc on 2010-10-16
Be careful uninstalling wubi. If you've moved a bunch of files onto it, when you uninstall they will be deleted (gone for good).

It should go without saying, that you need to get your data out first, but I've seen people do it: when you go to control panel, add/remove programs and double click on Ubuntu, you get one popup: Uninstall? and if you continue, it is gone.

Wubi uses a virtual disk that is (more) susceptible to corruption. I wouldn't put any important data on it without keeping regular backups. (Actually the same goes for any important data)

---

### Post by EpikRageQuit on 2010-10-16
Alright thanks guys, I'll post a success story on this later lol. This is what 'll be doing all day! i think ubuntu is worth it!

---

### Post by EpikRageQuit on 2010-10-16
Okay so I have backed up the files on another computer, and have uninstalled Ubuntu. Now in the link earlier provided it says to boot from Ubuntu CD/DVD... Do I download the file from the main site and burn it, becuase that would be the wubi thing, or could somone give me a link to the download I need. Ubuntu 10.10 desktop thanks.

edit***

I think it would be important to know I have Windows 7 64-bit on my laptop. I have an AMD Vision processor. So I think I found the download I need... Can someone verify so I don't mess up thanks...

[http://linux.softpedia.com/progDownload/Ubuntu-Maverick-Meerkat-Download-57327.html](http://linux.softpedia.com/progDownload/Ubuntu-Maverick-Meerkat-Download-57327.html)

.... the second option ISO desktop CD amd64 right?

---

### Post by Elfy on 2010-10-16
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)


[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Hope that helps

---

### Post by sandyd on 2010-10-16
> **EpikRageQuit said:**
> Okay so I have backed up the files on another computer, and have uninstalled Ubuntu. Now in the link earlier provided it says to boot from Ubuntu CD/DVD... Do I download the file from the main site and burn it, becuase that would be the wubi thing, or could somone give me a link to the download I need. Ubuntu 10.10 desktop thanks.

edit***

I think it would be important to know I have Windows 7 64-bit on my laptop. I have an AMD Vision processor. So I think I found the download I need... Can someone verify so I don't mess up thanks...

[http://linux.softpedia.com/progDownload/Ubuntu-Maverick-Meerkat-Download-57327.html](http://linux.softpedia.com/progDownload/Ubuntu-Maverick-Meerkat-Download-57327.html)

.... the second option ISO desktop CD amd64 right?
Download
[http://ubuntu-cd.mirror.iweb.ca//maverick/ubuntu-10.10-desktop-amd64.iso](http://ubuntu-cd.mirror.iweb.ca//maverick/ubuntu-10.10-desktop-amd64.iso)
then burn iso and follow these instructions. If you don't, you may have to recover windows later, which is not a good thing. [https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows]("https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows")

---

### Post by EpikRageQuit on 2010-10-16
> **forestpiskie said:**
> [http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)


[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)
[https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
[https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
[https://help.ubuntu.com/community/Installation/CDIntegrityCheck](https://help.ubuntu.com/community/Installation/CDIntegrityCheck)

Hope that helps

Thanks I think I found the proper ISO to burn and the 2nd link will help me install it but is the ISO I posted above correct for my laptop?

---

### Post by EpikRageQuit on 2010-10-16
> **sandyd said:**
> Download
[http://ubuntu-cd.mirror.iweb.ca//maverick/ubuntu-10.10-desktop-amd64.iso](http://ubuntu-cd.mirror.iweb.ca//maverick/ubuntu-10.10-desktop-amd64.iso)
then burn iso and follow these instructions. If you don't, you may have to recover windows later, which is not a good thing. [https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows]("https://help.ubuntu.com/community/RecoveringWindows#Resizing%20a%20Windows%20Partition%20in%20Windows")

Okay thank you guys a lot! Nice to see really friendly forums to new people like me... Thanks

---

### Post by EpikRageQuit on 2010-10-16
Okay so I downloaded the file... do i unzip it the burn the files... Sorry to bother you but I have never mounted an image before. I have burnt movies though if there is any similarities. Is there a program I need or can windows expolrer do it?

edit never mind, google fixed my problem

---

### Post by sandyd on 2010-10-16
> **EpikRageQuit said:**
> Okay so I downloaded the file... do i unzip it the burn the files... Sorry to bother you but I have never mounted an image before. I have burnt movies though if there is any similarities. Is there a program I need or can windows expolrer do it?
windows 7 burns isos I think.

right click on the file. select burn disc image

---

### Post by EpikRageQuit on 2010-10-16
Okay so I am at the point where I need to resize the Windows partition... Step 6 of the instructions and I clicked shrink(there was no resize option) on the windows partition then it "Queried volume for available shrink space" and then displayed a window with info stating the size of C: before shrink, size available to shrink, and an option to enter how much i would like to shrink it, and the total size after I shrink it... What should I do, And once I'm done how do I boot from the cd?

I know I must be a pain by now so sorry, but i really appreciate the help people. Thanks


**EDIT**

Okay so I'm past that part^^, and now I am on the boot cd trying to install it completely. I want the dual boot, so I selected the option of partition. There is all the free space wich I made and it says "No root file system is defined. Please correct this from the partitioning menu." What does it mean? Doesn't ubuntu create its own root file system??? I'm stuck and I don't want to overwrite any of the other drives... my options for partitions are... /dev/sda1(208mb), /dev/sda2(261619mb), unusable(223666mb), /dev/sda3(14502mb), /dev/sda4(108mb)

---

### Post by EpikRageQuit on 2010-10-16
I decided to carry on this under a different problem so I will mark this solved because I did figure out that I was unable to expand my space unless installed Ubuntu properly via livecd. So I continue this thread here [http://ubuntuforums.org/showthread.php?t=1598492](http://ubuntuforums.org/showthread.php?t=1598492)

(Not really solved, just a new problem)

---

