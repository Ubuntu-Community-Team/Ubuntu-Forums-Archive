---
title: "Burning to several CD's"
date: 2010-05-10
forum: New to Ubuntu
---

### Post by newport_j on 2010-05-10
I want to burn a large backup file to a CD. The file is 6.8 GB. When I do this it says to insert a CD with that capacity. Of course that is impossible - such a CD does not exist! I want to put it on several CD's (each holds 700 MB, a normal capacity of a CD) of data. So what is the command in CD/DVD creator to do this? Is there a command in CD/DVD creator to do this? If not what other CD burning software for Linux Ubuntu 8.04 can do this?

Newport_j

---

### Post by Paddy Landau on 2010-05-10
How did you create your backup?

You can split your backup into several parts using tar.

**Method 1:**

[LIST=1]
[*]Create a backup with tar (if you have a single file, then back it up with tar). For example:
```
tar -cjf bigbackup.tar.bz2 *files*
```Replace *files* with the file or files that you want backed up.
[*]Split  the original file into separate pieces.
```
tar -cf cd-1.tar -ML 716000 --remove-files bigbackup.tar.bz2
```It will prompt you as needed for the next names, so you'd type [FONT=Courier New]cd-2.tar[/FONT], [FONT=Courier New]cd-3.tar[/FONT], etc. The option --remove-files will delete the bigbackup.tar.bz2 on successful completion.
[*]Copy your pieces ([FONT=Courier New]cd-1.tar[/FONT], [FONT=Courier New]cd-2.tar[/FONT], etc.) onto your CDs.[FONT=Courier New]
[/FONT]
[/LIST]

**Method 2:**

Caveat: I've not tested method 2, so I don't know whether it works, but if it does work it'll be a lot easier.

[LIST=1]
[*]Create a backup with tar (as in Method 1, step 1 ).
[*]Use the following command to copy directly to CD.
```
tar -cMf /media/cdrom0 bigbackup.tar.bz2
```
[/LIST]
Whichever method you use, be sure to **test restoring from your backup**!

I would recommend that instead of backing up to CDs, you purchase an external USB hard drive. In the long run, you'll save yourself lots of time and hassle.

---

### Post by philinux on 2010-05-10
Method 3.
> I would recommend that instead of backing up to CDs, you purchase an external USB hard drive. In the long run, you'll save yourself lots of time and hassle.

8gig usb stick costs about £14 - £20.

---

### Post by Paddy Landau on 2010-05-10
> **philinux said:**
> 8gig usb stick costs about £14 - £20.
+1. I just bought a 16Gb stick from Amazon for £18 including postage.

---

### Post by newport_j on 2010-05-10
The use of USB drives is strictly forbidden where I work. Thus I can use only CD's. The command:

tar -cf cd-1.tar -ML 716000 remove-files bigbackup.tar.bz2


I assume the big file to breakdown is bigbackup.tar.gz2.

The number 716000 is the number of bytes on each separate unit. It matches the space on a single CD. 

I did not know that tar could do this. I will try command.

Newport_j

---

### Post by philinux on 2010-05-10
What about dvd's.

---

### Post by newport_j on 2010-05-10
Here is what I got when i issued the command:


root@james-desktop:/home# tar -vcf cd-1.tar -ML 716000 --remove-files backup.tar.gz
backup.tar.gz
Prepare volume #2 for `cd-1.tar' and hit return: 
Prepare volume #3 for `cd-1.tar' and hit return: 
Prepare volume #4 for `cd-1.tar' and hit return: 
Prepare volume #5 for `cd-1.tar' and hit return: 
Prepare volume #6 for `cd-1.tar' and hit return: 
Prepare volume #7 for `cd-1.tar' and hit return: 
Prepare volume #8 for `cd-1.tar' and hit return: 
Prepare volume #9 for `cd-1.tar' and hit return: 
Prepare volume #10 for `cd-1.tar' and hit return: 
Prepare volume #11 for `cd-1.tar' and hit return: 



I had to change --cf to -cvf (I wanted verbose), but it uses only a single dash. The command simply rewrote cd-1.tar over and over again. I got no cd-2.tar only one cd-1.tar. What did I do wrong?



Newport_j

---

### Post by Paddy Landau on 2010-05-10
> **newport_j said:**
> ... but it uses only a single dash.
Oops, sorry.

> **newport_j said:**
> The command simply rewrote cd-1.tar over and over again. I got no cd-2.tar only one cd-1.tar. What did I do wrong?
<smacks head> Sorry again, I left out an important part!

When you get the prompt, type:
```
n cd-2.tar
```Or whatever name you need. So, it should look like the following (your typing in [COLOR=DarkRed]*italics*[/COLOR]):
```
[COLOR=DarkRed]*tar -vcf cd-1.tar -ML 716000 --remove-files backup.tar.gz*[/COLOR]
backup.tar.gz
Prepare volume #2 for `cd-1.tar' and hit return: *[COLOR=DarkRed]n cd-2.tar[/COLOR]*
Prepare volume #3 for `cd-1.tar' and hit return: [COLOR=DarkRed]*n cd-3.tar*[/COLOR]
Prepare volume #4 for `cd-1.tar' and hit return: [COLOR=DarkRed]*n cd-4.tar*[/COLOR]
Prepare volume #5 for `cd-1.tar' and hit return: [COLOR=DarkRed]*n cd-5.tar*[/COLOR]
Prepare volume #6 for `cd-1.tar' and hit return: [COLOR=DarkRed]*n cd-6.tar*[/COLOR]
Prepare volume #7 for `cd-1.tar' and hit return: [COLOR=DarkRed]*n cd-7.tar*[/COLOR]
Prepare volume #8 for `cd-1.tar' and hit return: [COLOR=DarkRed]*n cd-8.tar*[/COLOR]
Prepare volume #9 for `cd-1.tar' and hit return: [COLOR=DarkRed]*n cd-9.tar*[/COLOR]
Prepare volume #10 for `cd-1.tar' and hit return: [COLOR=DarkRed]*n cd-10.tar*[/COLOR]
Prepare volume #11 for `cd-1.tar' and hit return: [COLOR=DarkRed]*n cd-11.tar*[/COLOR]
```Please try again.

There is a way to automate the renaming, but it's complicated.

---

### Post by newport_j on 2010-05-10
It worked, mostly. I did get an unusual output on one file. Here is the output after I ls -al the directory.


total 23410836
drwxr-xr-x  4 root         root               4096 2010-05-10 13:09 .
drwxr-xr-x 23 root         root               4096 2010-04-12 15:07 ..
-rw-r--r--  1 root         root         4625233920 2010-05-10 10:13 back3.tar.gz
-rw-r--r--  1 root         root         4620636160 2010-05-07 16:43 bak.tar.gz
-rw-r--r--  1 root         root         7351644160 2010-05-07 16:30 bk.tar.gz
-rw-r--r--  1 root         root          733184000 2010-05-10 13:09 cd-10.tar
-rw-r--r--  1 root         root           19814400 2010-05-10 13:09 cd-11.tar
-rw-r--r--  1 root         root          733184000 2010-05-10 13:01 cd-1.tar
-rw-r--r--  1 root         root          733184000 2010-05-10 13:02 cd-2.tar 
-rw-r--r--  1 root         root          733184000 2010-05-10 13:03 cd-3.tar
-rw-r--r--  1 root         root          733184000 2010-05-10 13:03 cd-4.tar
-rw-r--r--  1 root         root          733184000 2010-05-10 13:04 cd-5.tar
-rw-r--r--  1 root         root          733184000 2010-05-10 13:05 cd-6.tar
-rw-r--r--  1 root         root          733184000 2010-05-10 13:06 cd-7.tar
-rw-r--r--  1 root         root          733184000 2010-05-10 13:07 cd-8.tar
-rw-r--r--  1 root         root          733184000 2010-05-10 13:08 cd-9.tar
drwxr-xr-x  2 code25retina code25retina       4096 2010-04-28 13:42 code25retina
drwxr-xr-x 82 james        james             12288 2010-05-10 11:58 james
-rw-r--r--  1 root         root              12804 2010-05-10 10:48 out


Now all of the tar files are in red, except for one. That one is cd-2.tar. I am not sure why that is so. I need to change it to red so that it is now an archive file.

When I ls cd-2.tar it shows up as not accesible. That is even though it is shown on the list.

Observe:



root@james-desktop:/home# ls cd-2.tar
ls: cannot access cd-2.tar: No such file or directory


How do I make it like the other files. I think it is alright other than for the file name in black, not white.

Newport_j

---

### Post by Paddy Landau on 2010-05-10
> **newport_j said:**
> When I ls cd-2.tar it shows up as not accesible.
Firstly, the files are all owned by root and not by yourself. Was that deliberate?

Secondly, do the following command, please:
```
ls -lq
```I'm wondering whether you mistyped something when entering [FONT=Courier New]cd-2.tar[/FONT], accidentally adding a control character.

---

### Post by newport_j on 2010-05-10
I will just redo it. I think I did it correct. I am just not willing to risk it. This is my backup.

BTW, how does one undo this. I mean get the original back.

Newport_j

---

### Post by Paddy Landau on 2010-05-10
I've been testing and I think you may have a space in the name. Do this command:
```
echo "<$( ls cd2* )>"
```If there is a space, it will show something like this:
```
<cd-2.tar >
```Notice the space. To remove the space, do:
```
mv 'cd-2.tar ' cd-2.tar
```Notice that I use the quotes to show the space.

To restore the original file, do the following.
```
[COLOR=DarkRed]*tar -xMf cd-1.tar*[/COLOR]
Prepare volume #2 for `cd-1.tar' and hit return: [COLOR=DarkRed]*n cd-2.tar*[/COLOR]
Prepare volume #3 for `cd-2.tar' and hit return: [COLOR=DarkRed]*n cd-3.tar*[/COLOR]
* (etc.)*
```But you need to fix [FONT=Courier New]cd-2.tar[/FONT] first.

---

### Post by newport_j on 2010-05-11
It works now. I am needing the command to put it back together. This is obviously a backup for me before I reorder my hard drive, I would like to test this idea and put some cd-1.tar, cd-2.tar, cd-3.tar, etc back together. 

I think this is a good idea: the breaking up of a large file and putting into smaller pieces and putting each piece on a CD disk. It works. Now I need to verify that I did it correctly and the best way to do that is to put it back together before I reorder my hard drive. If I reorder my hard drive and it fails and then I discover that I cannot put the file pieces back together then it is too late.

Newport_j

---

### Post by newport_j on 2010-05-11
I thought this question was put on the Forum earlier. I have the system working and my large file is now on several cd's each having a piece of this file. Now before I reorder my hard drive, how do I reverse this? I want to test the backup before I reorder my hard drive. 

If it works, fine. I get to work on my hard drive. It it does not then I can change before, I reorder my hard drive.

What is the command to reverse? To put the large file back together from the many pieces it is now in on several cd's.

Newport_j

---

### Post by newport_j on 2010-05-11
This above problem has been fixed. I have question that keeps getting removed from the Forum on how to put these pieces back together? I am very reluctant to do any permanent changes to my hard drive owing to the fact that I d not know if my back up has been successful. I want to check that. How do I do it.

I must know the commands to put this back together. The other half of this procedure.

Newport_j

---

### Post by newport_j on 2010-05-11
I have posted a reply to the statements above three times in the last 2 hours, but they keep getting removed from the Forum. Why?

I believe that it is a legitimate question that requires an answer. I am under a tight schedule to modify my hard drive and I will not do it until my back is complete and verified.

I am asking how to verify it.

This is the fourth posting of the question today.

Any help appreciated.

Newport_j

---

### Post by Paddy Landau on 2010-05-11
I don't know why you can't see your posts... I see all four of them! :D

The answer you want is in [post 12]("http://ubuntuforums.org/showthread.php?p=9274643#post9274643") near the end.

---

### Post by newport_j on 2010-05-13
Everything worked. All files backed up, but thankfully that was not needed. I am now using Ubuntu 8.04 on all of the hard disk and Windows XP is gone.

I have one small error, though, the Windows XP option stills shows up on the boot menu. I select it and it says that no Windows partition exits. Of course it does not; since I removed it yesterday.

However, I would like to remove that option from my boot menu anyway. How do I do that?


Newport_j

---

### Post by Paddy Landau on 2010-05-13
I'm glad you got it all sorted.

I think the command you need is this.
```
sudo update-grub
```Let us know.

BTW, did you manage to see your four posts eventually?

---

### Post by newport_j on 2010-05-14
I did see all four of my repetitive videos. Sorry about the confusion, the fault is all mine.

However, the command sudo update-grub 

did not remove the windows option in my boot menu. 

It did show me a file: menu.1st

that seems to have most of the boot menu info in it - all nice and organized. The idea struck that if I remove all references to Windows XP, then it will likewise affect the boot menu.

Do you think that will do it?

Newport_j

---

### Post by Paddy Landau on 2010-05-14
> **newport_j said:**
> Do you think that will do it?
Sorry, I don't know the new grub that comes with 10.04.

There are a number of posts on this forum explaining how to tell grub to reconfigure itself; I suggest that you search for them.

As your original problem is solved, do you want to mark this tread as Solved?

---

### Post by newport_j on 2011-08-16
Okay, I now have a set of cd-1.tar, cd-2.tar, etc. disks. Now how do put tem back together into the original file? In other words how do I get them back in the form backup.tar.gz. I want to put all the pieces back into the largest file and get back to the original to check my backup.
 
Any help appreciated.
 
Thanks in advance.
 
Newport_j

---

### Post by Paddy Landau on 2011-08-16
> **newport_j said:**
> Okay, I now have a set of cd-1.tar, cd-2.tar, etc. disks. Now how do put tem back together into the original file? In other words how do I get them back in the form backup.tar.gz. I want to put all the pieces back into the largest file and get back to the original to check my backup.
 
Any help appreciated.
 
Thanks in advance.
 
Newport_j
I don't get it. Did you not see [post 12]("http://ubuntuforums.org/showthread.php?p=9274643#post9274643") and [post 17]("http://ubuntuforums.org/showthread.php?p=9280856#post9280856")?

BTW, for future use, it will be easier to use a more modern archive system such as 7z. In Nautilus, select the file you want to compress; right-click and select Compress; select .7z next to the file name; click Other Options; fill in "Split into volumes of..."

---

### Post by newport_j on 2011-08-18
Yes, I got the other posts. I have not been on the Forum for several months. I was in error.
 
Newport_j

---

### Post by Paddy Landau on 2011-08-18
> **newport_j said:**
> Yes, I got the other posts. I have not been on the Forum for several months. I was in error.
Oh good, I'm glad you got it sorted.

If your problem is solved, please mark this thread as Solved. Thanks.

---

