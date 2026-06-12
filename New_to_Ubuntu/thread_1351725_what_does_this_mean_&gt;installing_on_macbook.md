---
title: "what does this mean &gt;installing on macbook"
date: 2009-12-10
forum: New to Ubuntu
---

### Post by hollowtd on 2009-12-10
Hi 

Im getting ready to follow these to install linux on a partition in my macbook.

*******

Download Ubuntu Live CD and burn it. 

Install rEFIt (this step is optional, you can hold 'Alt' to select partition everytime instead). 

Use Boot Camp Assistant (it's in Applications/Utilities) to create new partition. I allocate 5GB partition. 
Insert the live CD into the drive and reboot 
Hold down ‘C’ button at the black screen to boot from CD. 
Follow usual Ubuntu installation step. In keyboard selection screen, choose “macintosh”. 
In partitioning screen, choose ‘manually edit partition table’. 
Delete the 5GB partition just created from BootCamp. Then create the ext3 partition at the same size. 

Mount it as ‘/’. 

Complete the installation process. Then reboot. 
If you install rEFIt, the boot menu will show up. If not, hold 'Alt' button for a while and select the Windows partition for Ubuntu. 


******

However, I don´t know what the Mount it as ‘/’ means? Can anyone explain this to me? I understand the rest. Do I need to leave a swap partition too?

cheers again

---

### Post by carnagex420x on 2009-12-10
If you can do a manual partition scheme, you should have a basic understanding of the root "/" of a file system. Every directory in your install falls under /. When doing manual partitioning it is possible to mount diff. directories to diff. partitions, however mounting / to a single partition is the easiest and most basic. You do not NEED a swap partition, however w/o one you could run into issues if you have a limited amount of RAM or you wish to do Hibernation.
There are many sources online (including the ubuntuforums) where you can get a better understanding but here is a link that may help. [http://tldp.org/HOWTO/Partition/requirements.html](http://tldp.org/HOWTO/Partition/requirements.html)

---

### Post by Merk42 on 2009-12-10
/ is the root partition in Linux. Meaning the complete top level folder.  Every other folder is after that.

---

### Post by hollowtd on 2009-12-10
so would i creat this¨

/ext3 

then

---

### Post by hollowtd on 2009-12-10
ive done this the hard way without bootcamp but i just dont remember what i did on this step thanks again

---

### Post by carnagex420x on 2009-12-10
Really you do not need Boot Camp to run linux on a Mac. Boot Camps big feature besides providing an easy dual boot solution, is Boot Camp provides you with the Windows drivers for you Macintosh hardware. Aside from that it makes resizing partitions easy to but, so does Gparted. I done this before, and I have used rEFIt before also. rEFIt is an awesome utility, Boot Camp not so much...

---

### Post by The_Pirate_King on 2009-12-10
It will allow you to choose the mount location during installation. Just choose "/".

---

### Post by hollowtd on 2009-12-10
thanks guys I'll give it a go cheers again

---

