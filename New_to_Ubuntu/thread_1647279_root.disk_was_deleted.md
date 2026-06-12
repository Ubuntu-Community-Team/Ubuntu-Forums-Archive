---
title: "root.disk was deleted"
date: 2010-12-17
forum: New to Ubuntu
---

### Post by yahonto on 2010-12-17
Tell me, please.
My file d: \ ubuntu \ disks \ root.disk was deleted. It was my ubuntu, which I need. Can I recover it?

---

### Post by yahonto on 2010-12-17
I was hoping to restore it using winhex, but winhex does not see it. Maybe someone knows the signature file, for its location? Help, please.

---

### Post by Mark Phelps on 2010-12-17
Some here will tell you that running Testdisk, in Ubuntu, will recover that for you.  I've not had success with Testdisk on MS Windows partitions, so I don't use it.

A problem you're going to run into IMMEDIATELY, is that if you install ANYTHING inside MS Windows now, you run  the risk of overwriting where root.disk used to be -- which will prevent any recovery of it.

So, if you want to use MS Windows utilities to recover this file (which is what I would recommend), you will need to be prepared to do the following:
1) Remove the drive from your PC
2) Download and install Recover My Files (from Runtime Software) on another PC -- this one, running MS Windows
3) Connect the troubled drive to this other PC as an external drive
4) Run Recover My PC -- and see what it finds.

IF it finds the file and indicates that it can be recovered -- you will then have to purchase it to do the actual recovery.

The only other alternative is to do the following:
1) Boot this PC from an Ubuntu CD in LiveCD mode
2) If testdisk is not already installed, then install it
3) Run testdisk to see if it can find and recover the file

But as I've said, I've not had success using testdisk to recover files in MS Windows partitions -- so someone else will need to jump in with the specifics.

---

### Post by Rubi1200 on 2010-12-17
> **yahonto said:**
> Tell me, please.
My file d: \ ubuntu \ disks \ root.disk was deleted. It was my ubuntu, which I need. Can I recover it?
How exactly was it deleted?

Are you sure this is the right path to it? Normally, Wubi would be installed to the C drive on Windows.

There is a program for use in Windows that you can use to read/copy Wubi files:
Use [ext2read]("http://ext2read.blogspot.com/") to recover any important data from the Ubuntu root.disk. (you can probably run it from a USB stick, so no need to install to the drive).

---

### Post by yahonto on 2010-12-17
> **Mark Phelps said:**
> Some here will tell you that running Testdisk, in Ubuntu, will recover that for you.  I've not had success with Testdisk on MS Windows partitions, so I don't use it.

A problem you're going to run into IMMEDIATELY, is that if you install ANYTHING inside MS Windows now, you run  the risk of overwriting where root.disk used to be -- which will prevent any recovery of it.

So, if you want to use MS Windows utilities to recover this file (which is what I would recommend), you will need to be prepared to do the following:
1) Remove the drive from your PC
2) Download and install Recover My Files (from Runtime Software) on another PC -- this one, running MS Windows
3) Connect the troubled drive to this other PC as an external drive
4) Run Recover My PC -- and see what it finds.

IF it finds the file and indicates that it can be recovered -- you will then have to purchase it to do the actual recovery.

The only other alternative is to do the following:
1) Boot this PC from an Ubuntu CD in LiveCD mode
2) If testdisk is not already installed, then install it
3) Run testdisk to see if it can find and recover the file

But as I've said, I've not had success using testdisk to recover files in MS Windows partitions -- so someone else will need to jump in with the specifics.

Many thanks for the tip!

The task is complicated by the fact that I have a laptop. I can not pull the hard drive. But root.disk was on drive D, and the system is installed on drive C. So I just stopped writing to the disk D. I still worry that I had not noticed the problem immediately and save multiple small files to disk D and the rules of some documents there. Nevertheless, Nevertheless, I still do not lose hope.

Testdisk I've already tried. He found nothing. Also, I tried Restorer2000 Professional, and he, too, sees nothing.
Also, I tried use Explore2fs and Ext2explore. They have a button Rescan Partitions. But after clicking, nothing happens.

I also tried winhex. If you just run a word search root.disk, he finds the word in several places, but to try to restore it I need to know the signature of this file. I thought that you can find a header created on another computer again root.disk and looking at this file using TrID.

Now going to try Recover My Files and Ubuntu CD in LiveCD mode, as you recommended.
Thanks again!

---

### Post by yahonto on 2010-12-17
> **Rubi1200 said:**
> How exactly was it deleted?

Are you sure this is the right path to it? Normally, Wubi would be installed to the C drive on Windows.

There is a program for use in Windows that you can use to read/copy Wubi files:
Use [ext2read]("http://ext2read.blogspot.com/") to recover any important data from the Ubuntu root.disk.

I have no idea where the missing file. I was shocked. Almost all are not stored in ubuntu, but there is still something that needs to be restored, if possible. I remember that after restarting the computer, just before I discovered that the missing root.disk, was to test the chkdsk. I do not know why it started, but I think that something happened while I was not at the computer and root.disk deleted by chkdsk, but could not recover because there was not enough free space.

Path exactly right.

ext2read not helped. He just does not see this file, and scan does not want.

Right now I trying use R-Linux, and he found something!!! I do not hope to restore the entire root.disk entirely, but it may be possible to restore a folder that I need and profile.

Thank you very much for your help.

---

### Post by bcbc on 2010-12-17
If chkdsk removed it, it likely placed it in a folder called d:\FOUND.000 (these folders are hidden). Once you find it, just move it back.

If you really deleted root.disk then you have little hope of recovering it because it's a huge file, and likely parts of it get overwritten quickly. And once that happens - you're out of luck.

---

### Post by yahonto on 2010-12-17
> **bcbc said:**
> If chkdsk removed it, it likely placed it in a folder called d:\FOUND.000 (these folders are hidden). Once you find it, just move it back.

Folder d: \ FOUND.000 not. Has previously happened that I found in this folder the restored files. But in this case the file was about 14Gb and chkdsk with him does not coped.

> **bcbc said:**
> 
If you really deleted root.disk then you have little hope of recovering it because it's a huge file, and likely parts of it get overwritten quickly. And once that happens - you're out of luck.

Exactly. 

R-Linux found a section of ext4. Scaned it and opened it. But the folder 'home', content that interests me was empty. And nowhere have I found no trace of the files I need. I noticed the folder Extra Found Files. There are files *. bz2. Their sizes are very large. It seems that this unrecognized part of the file root.disk. And hex search inside finds the words included in the files I need. It seems root.disk really never be able to recovered fully. Can Recover My Files will be able to understand these pieces.

Here is a screenshot of what I  obtained using R-Linux:
[[IMG]http://i042.radikal.ru/1012/fd/7b35de1658cdt.jpg[/IMG]](http://radikal.ru/F/i042.radikal.ru/1012/fd/7b35de1658cd.jpg.html)

---

### Post by yahonto on 2010-12-18
Recover My Files found nothing. Even ext4 is not found.
Explore2fs version 1.08 beta 9 as I understand only supports ext2 and ext3. Found nothing.

---

### Post by yahonto on 2010-12-18
R-Studio found the same as R-Linux. Looks like it's all the same (R-Studio includes the R-Linux).

---

### Post by yahonto on 2010-12-18
Raise Data Recovery for Ext2/3/4 found a lot of things. Something of this I needed, but the ~/.config/ I have not recovered :(
As I understood Live CD Ubuntu not help me. Or should I try?
Looks like will have to come to terms with the loss :(

---

### Post by yahonto on 2010-12-19
Zero Assumption Recovery (ZAR) was able to find many, but not that valuable. :(

---

