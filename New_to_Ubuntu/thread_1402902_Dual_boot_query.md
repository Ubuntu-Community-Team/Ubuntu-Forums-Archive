---
title: "Dual boot query"
date: 2010-02-09
forum: New to Ubuntu
---

### Post by boxcorner on 2010-02-09
Hello
Yet another newbie.
Yet another dual boot query.
Yet another M$ user thinking of migrating to Linux.
Background:
I have a PC with XP installed on one 40GB HDD [NTFS].
I have a 2nd HDD in the system 80GB [FAT] that I currently use to store Windows files.
Aim:  
I would like to ease into Ubuntu gently, whilst continuing to use XP for the time being, until I feel confident enough to quit using XP.  Meanwhile, I would like to be able to transfer files back and forth between the two drives (ie between the the two OS's).
Question(s):
If I install Ubuntu on my 80GB drive (* without first removing the 40GB XP drive *) will Ubuntu set up dual boot automatically, so I can then either boot into XP or Ubuntu?
If I partition the 80MB drive into 40/40 and install Ubuntu in one 40MB partiton, will I then be able to use the other partition to transfer files back and forth between the two OS's?
Thanks in advance for your help and advice.

---

### Post by mcduck on 2010-02-09
The answer is "yes" to both questions.

If you leave both drives plugged in when doing the install, Ubuntu will automatically detect your Windows system and add it to a boot menu where you can select which OS to boot into. The default will be Ubuntu, but you can change that afterwards to start Windows by default.

And yes, if partition sme part of the 80GB drive as FAT of NTFS filesystem you'll be able to sue that from both operating systems. Actually Ubutnu would be able to access your Windows partition directly, but Windows can't read Linux filesystems (at least wthout 3rd party drivers, and even then writing  to Linux filesystems drom Wibndows might not be a good idea) so some shared partition will probably be a good way to handle things.

Just make sure you select the right drive for installation, and you should be fine. If you want to, you can create the shared partition beforehands and leave the rest of the 80GB drive as empty, unpartitioned space. That would make the install very easy as Ubuntu would automatically detect that empty space and offer you a choise to use that. Or you can use manual partitioning with Ubuntu installer, and create the shared partition at that point.

Note that Ubuntu will actually use (at least) two partitions, one for the system and a small one for swap. If you choose to use the manual partiitoner you'll need to make both. :)

---

### Post by crlang13 on 2010-02-09
Hey mate,

I'm a newbie too.  I went for the "gently" option, by duel booting as well.  I then found I was never using XP so I wiped it just the other day.  I'm very happy about the decision.  But I still think it's a good idea to duel boot for awhile, just in case.

When you go to install ubuntu, it will ask you whether you want to duel boot or just wipe windows.  This is in the same step as when you set up the partitions.  Then, each time you boot up you'll be asked to choose which operating system you want to use.  It's that easy.

As for transferring back and forth...  I may have this a bit wrong, because I haven't really tried it myself, but when I was duel booting, I had access to my windows hard drive and could view and edit files in my windows hard drive when in ubuntu.  I could not, however, get to my ubuntu files through windows.

you may also want to check out ubuntu 1 - [https://one.ubuntu.com/](https://one.ubuntu.com/) - it's a free 2 gigs of online storage you can use if you're having trouble transferring from one to the other.

Either way, back everything up before installing ubuntu or doing any tinkering.

---

### Post by netlaptop on 2010-02-09
Here you have 2 HDDs for your desktop right?
1 40GB XP
1 80GB for storage...

I think there is an easy and safe alternative way:
(back up ur data first, if you need...)

Boot to XP and insert Ubuntu CD, then just install Ubuntu inside Window XP as a program via Wubi.

Then reboot, it will automatically gives you 2 options to boot, Ubuntu or XP.

When you feel it is ok to switch to Ubuntu completely, Just format and install full Ubuntu to that 40 GB disk.

---

### Post by oldfred on 2010-02-09
If you just want to try ubuntu the wubi install is a step above the liveCD as it looks and acts like ubuntu, but it is running as a file on a windows partition. If you have windows problems you also have wubi problems.

If you want to convert (even long term) to ubuntu I would do the full install to the second hard drive. I like having grub/ubuntu on the first drive and it will find windows on the second drive. If windows boot loader is still in the MBR of the windows drive then you can switch drives in BIOS and still directly boot windows.

Three or four years ago I was where you were and I had to make sure my spouse was ok with the change. I created a shared partition for files, firefox and thunderbird profiles so from both systems these main applications looked almost identical with the same data.

---

### Post by boxcorner on 2010-02-10
More background :
Used MS-DOS before Windows.  Used Windows through to XP.  In 92 built desktop, installed and dabbled with Red Hat (dual boot with XP).  Since then used XP exclusively on laptop which died recently.  Refurbished old desktop, updated XP with SP3 on 40MB NTFS HDD, upgraded RAM, PSU died, moved 40MB HDD to my wife's old desktop, reactivated XP, increased RAM, have now replaced PSU in my desktop, about to increase RAM, plan to move 40MB NTFS HDD back to my desktop, then install Ubuntu in partition on 80MB FAT HDD.

> **mcduck said:**
> The answer is "yes" to both questions.  :)

Many thanks.  That's very helpful.

> **crlang13 said:**
>  ... I could not, however, get to my ubuntu files through windows ... you may also want to check out ubuntu 1 - [https://one.ubuntu.com/](https://one.ubuntu.com/)  ... back everything up before installing ubuntu or doing any tinkering.

Many thanks for your help.  Hopefully I will be able to use the Windows partition on my 80MB FAT HDD to transfer files between Ubuntu in the other partition on that drive and XP on my 40MB NTFS HDD which currently is my boot drive.  Thanks for the tip about online storage.  My Windows configuration and data is backed up to an external 300GB NTFS HDD.

> **netlaptop said:**
>  ... install Ubuntu inside Window XP as a program via Wubi ...
Just format and install full Ubuntu to that 40 GB disk.

Many thanks for your help.  I considered using virtualization, such as VirtualBox, but am concerned about the overheads (processor & RAM).  I would like to avoid formatting.  One advantage of installing the 2 OS's on separate HDDs seems to be that one drive can then moved to different machine later, if required.

> **oldfred said:**
>  ...want to convert (even long term) to ubuntu ... I created a shared partition for files, firefox and thunderbird profiles so from both systems these main applications looked almost identical with the same data.

Many thanks for your help.  Planned to convert to Linux ages ago, but got distracted by work and then moving to France.  Weaned myself off M$ IE, Office & Outlook; been using Firefox, OpenOffice and Thunderbird.  Looking forward to getting my old desktop running dual boot XP & Ubuntu, so I can complete the conversion.  That's Plan-A!

> **mcduck said:**
> The answer is "yes" ...

It works!  I divided my 80MB FAT32 HDD into two equal partitions and installed Ubuntu 9.10  

It all went smoothly.  Absolutely no hassle.  So, now when I start my PC, I get a dual-boot menu, to start Ubuntu from the 80MB HDD or start XP from my 40MB HDD.  

I was online, via Firefox, typing this a few minutes later, using Ubuntu.  Incredible!

Thanks again for your help!

---

### Post by oldfred on 2010-02-13
That's great. We love to hear success stories as all we seem to have are problems on this site. If you need further help with anything related to Ubuntu someone here is always willing to help.:popcorn:

---

### Post by boxcorner on 2010-02-17
> **oldfred said:**
> That's great. We love to hear success stories as all we seem to have are problems on this site. If you need further help with anything related to Ubuntu someone here is always willing to help.:popcorn:

Ubuntu is truly amazing. I now understand why so many people are talking about it.  The quality of the  support and documentation that is available for it is most impressive.    Linux seems to have improved immensely since I played around with Red Hat at the beginning of the last decade.  It is a pity that you only get to hear about problems.  I fully understand though as I spent some time managing qa in the development process.  -ve feedback can be extremely frustrating, whereas +ve feedback is motivating.  Well done to you and the rest of the crew!  My next task is to import my Thunderbird profiles from XP, so I can start using Ubuntu productively.

---

### Post by oldfred on 2010-02-17
While you can import your thunderbird and firefox profiles you can put them in a shared NTFS partition so you have the same emails and bookmarks in both systems. It makes converting easier as you so not have to worry about where those settings are. I also copy my entire profile to a portable when traveling and copy back so it is easy to do. Not sure about the new TB3, as I understand it updates some things.

[http://www.mozilla.org/support/thunderbird/profile#locate](http://www.mozilla.org/support/thunderbird/profile#locate)
[http://kb.mozillazine.org/Profile_Manager#Linux](http://kb.mozillazine.org/Profile_Manager#Linux)
More info:
    *  (Firefox) ./firefox -profilemanager
    * (Mozilla Suite) ./mozilla -profilemanager
    * (SeaMonkey) ./seamonkey -profilemanager
    * (Thunderbird) ./thunderbird -profilemanager 
[http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux](http://kb.mozillazine.org/Sharing_a_profile_between_Windows_and_Linux)
[http://kb.mozillazine.org/Category:Profiles](http://kb.mozillazine.org/Category:Profiles)

---

