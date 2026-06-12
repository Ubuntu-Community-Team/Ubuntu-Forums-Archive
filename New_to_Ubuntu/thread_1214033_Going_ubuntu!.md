---
title: "Going ubuntu!"
date: 2009-07-15
forum: New to Ubuntu
---

### Post by porkpork on 2009-07-15
Hi, I am new to ubuntu and was hoping someone with some experience could shed some light on a few questions that I have.
 
First off I'd like to explain that I have been an exclusive Windows user and am now looking to tryout other operating systems, ubuntu seems to be a popular one at no cost. I am currently running Windows Vista 32-bit on a 500G NTFS disk drive seperated into 3 partitions: 9.76GB EISA Configuration(whatever the hell that is??), 228GB Windows Vista formatted C drive, and a 227GB NTFS D drive.
 
What I'm looking to do is have the latest version of ubuntu desktop edition installed on my C drive so that on boot up I can choose to boot either Windows Vista or ubuntu. I have found a video on youtube that seems pretty straightforward and noobie friendly that I will use to help me install ubuntu, seen here ([http://www.youtube.com/watch?v=-opSR3YM8KQ](http://www.youtube.com/watch?v=-opSR3YM8KQ)), so installation doesn't seem to be a real issue.
 
What is bothering me is that I have heard that ubuntu as well as all Linux operating systems, can not write to NTFS drives safely. Some people say they are satisfied with just having the ability to read from a NTFS drive because that is all they need. Im not sure if I fall into this catagory. I am learning how to program on a Windows system with C++, but I'd also like to program on a Linux system as well as use general features such as playing music, watching videos, using various video/picture editing software or simply browsing the web - which is more of less all the things I do on my Windows OS. 
 
So my questions to you are:
 
1) If I need to write to NTFS, how do I do it, and what do I risk if I do?
2) Is there another file system other than NTFS that ubuntu AND vista are highly compatible with?
3) If so, do I need to buy another hard drive for ubunto to write to or is it possible AND practical to set up differently formatted partitions on the same disk?
 
I have tried researching answers to these questions but most of my results have been about past versions of ubunto, and I want current info from actual ubuntu users, this seems like the right place.
 
Thanks in advance, 
porkpork

---

### Post by philinux on 2009-07-15
Either try the live cd first or try wubi.

[http://www.ubuntu.com/](http://www.ubuntu.com/)
[http://wubi-installer.org/](http://wubi-installer.org/)

Linux can write to ntfs.

---

### Post by germanix on 2009-07-15
[QUOTE=porkpork;7620987]
So my questions to you are:
 
1) If I need to write to NTFS, how do I do it, and what do I risk if I do?
2) Is there another file system other than NTFS that ubuntu AND vista are highly compatible with?
3) If so, do I need to buy another hard drive for ubunto to write to or is it possible AND practical to set up differently formatted partitions on the same disk?

Hi Porkpork, welcome to Ubuntu. I am no expert but I do believe that both Ubuntu and Windows can read/write to FAT32. Normally Linux uses EXT3. You do not need to buy another harddrive, you can format the partitions as you need. You can even install Ubuntu under Windows as a Window file if you want. Have fun.

---

### Post by porkpork on 2009-07-15
Thanks for the quick reply, I'll check out Wubi right now. And Linux can read/write to NTFS safely now? So either way I'm good to go? I must have been reading some old posts about this writting issue then. 
 
Well if its safe and fully functional on NTFS then I don't mind burning a cd and going through that process. But looking at Wubi, it seems stupefyingly easy, no cd burning no partitions or formatting disks, will I loose any features or functionality if I simple use Wubi? Or is it better to burn a disk and install like I have heard about.

---

### Post by Ratscallion on 2009-07-15
Wubi is exactly the same as a normal install, with only minor differences:
*It is installed INSIDE windows, so you can uninstall it from add/remove programs, unlike the partition install
*There is no partition needed
*You can access you Windows files from /host rather than another partition,
*but you cannot access your Ubuntu files from within Windows. Be careful on that.
Other than the aforementioned items, there are no other differences. No speed or program loss at all.

---

### Post by Old_Grey_Wolf on 2009-07-15
> **porkpork said:**
> 
1) If I need to write to NTFS, how do I do it, and what do I risk if I do?
2) Is there another file system other than NTFS that ubuntu AND vista are highly compatible with?
3) If so, do I need to buy another hard drive for ubunto to write to or is it possible AND practical to set up differently formatted partitions on the same disk?

1) Ubuntu can write to NTFS. If you are concerned about your Windows partition, you can create an extra NTFS partition to share data between Ubuntu and Windows. 

2) Other than NTFS there is FAT32.

3) You can repartition your disk. Actually, the Ubuntu installation will do it for you.

I recommend that you back up your data before installing an OS. I also recommend that you try Ubuntu using the Live CD before you install it.

---

### Post by philinux on 2009-07-15
I'm using ubuntu 9.04 and this program is installed by default.

> read-write NTFS driver

The **ntfs-3g** driver is an open source, GPL licensed, third generation Linux
NTFS driver which was implemented by the Linux-NTFS project. It provides
full read-write access to NTFS, excluding access to encrypted files, writing
compressed files, changing file ownership, access right.

Technically it's based on and a major improvement to the third generation
Linux NTFS driver, ntfsmount. The improvements includes functionality,
quality and performance enhancements.



---

### Post by ramnarayan on 2009-07-15
> **porkpork said:**
> 
 
Well if its safe and fully functional on NTFS then I don't mind burning a cd and going through that process. But looking at Wubi, it seems stupefyingly easy, no cd burning no partitions or formatting disks, will I loose any features or functionality if I simple use Wubi? Or is it better to burn a disk and install like I have heard about.

Yes go ahead, i think the only functionality you lose is some ego at not have a free based system (or being unable to hide windows from prying open source fans) ;-)

Another is once you go "advanced" you will find that its easier to manage multiple OS' using Linux rather than Wincedows

---

### Post by porkpork on 2009-07-15
Oh so I can simply create another drive on the disk and format it as FAT32 so both vista and ubuntu can read/write to it w/o issue. That's good to know. However philinux is saying that ubuntu reads/writes to NTFS without issue, or at least thats what Im getting from his reply. If that's the case then I might as well keep the format of all partitions as NTFS. So is the latest desktop edition of ubuntu fully compatible with NTFS? Before I go burn this disk and start installing it.

---

### Post by porkpork on 2009-07-15
Ah okay, I'm a couple posts behind you guys, alright I think I have all the info I need, seems like NTFS read/write was an old issue thats been dealt with. Thanks for the insight, I'm gunna go install it. Cheers.

---

### Post by Old_Grey_Wolf on 2009-07-15
> **porkpork said:**
> Oh so I can simply create another drive on the disk and format it as FAT32 so both vista and ubuntu can read/write to it w/o issue. That's good to know. However philinux is saying that ubuntu reads/writes to NTFS without issue, or at least thats what Im getting from his reply. If that's the case then I might as well keep the format of all partitions as NTFS. So is the latest desktop edition of ubuntu fully compatible with NTFS? Before I go burn this disk and start installing it.

You don't need FAT32 at all actually, it is just an option. Ubuntu wants a Ext3 formatted partition and Windows a NTFS formatted partition. The Ubuntu install will however, do that formating for you.

I will repeat this, I recommend that you back up your data before installing an OS. :)

---

### Post by philinux on 2009-07-15
> **Old_Gray_Wolf said:**
> You don't need FAT32 at all actually, it is just an option. Ubuntu wants a Ext3 formatted partition. The Ubuntu install will however, do that for you.

I will repeat this, I recommend that you back up your data before installing an OS. :)

Yes and with fs-driver installed on windows, windows can read the ext partition.

---

### Post by oldfred on 2009-07-15
Years ago there were issues with the Linux NTFS drivers. I installed a FAT32 partition for all data that I wanted to share on my system when I set it up 2-3 years ago. Now most people seem to recommend using NTFS for the shared partition, but you can use either. EXT3 and NTFS are journaled, so that problems can usually be repaired with out a full disk analysis. FAT32 also has a maximun of 4GB, and is not journaled, but is used on almost all the USB keys and camera memory cards, which can be read by both Windows and Linux. Someone also said the Windows7 NTFS is slightly different and may cause issues.

---

