---
title: "Incredibly slow file moving"
date: 2010-11-10
forum: New to Ubuntu
---

### Post by ubunwhat on 2010-11-10
I am still quite new to Ubuntu and am pulling my hair out on a basic issue.  I am having a terrible time opening file folders or moving files between folders.  This is all on the same disk with plenty of free space etc.  If I have a folder with say 2000 items in it, mostly small items such as text files or small images, it will take over 5 minutes to open the folder.  It will then take up to 25 minutes to move 100 of those files to another folder on the same drive.  This is insane!  I don't know enough about Linux to check logs or anything but clearly it is an issue with Nautilus. Sometimes I give up halfway through and try to reboot and I get a warning that Nautilus is still working and I can't shut down.  This cannot be the norm so, seriously, how can I fix this?

---

### Post by tajiknomi on 2010-11-10
[SIZE=2]what about your **swap space** and **Ram**,...?


[/SIZE]

---

### Post by ubunwhat on 2010-11-10
I have 2GB of RAM, which is the max for this motherboard.  I have checked the System Monitor during these times and, while the CPU is maxed out the memory and swap space stay around 60%.

---

### Post by ubunwhat on 2010-11-10
I have also followed advice in similar threads and switched to list view, 33%, no thumbnails, and only displaying file name and type, while dropping file size and date modified.  It really didn't make much of a difference.

---

### Post by HermanAB on 2010-11-10
Try Dolphin, Konqueror or Thunar instead of Nautilus.

---

### Post by endotherm on 2010-11-10
that is weird. if everything is on the same partition, then there really isn't any IO involved in moving a file. just rewrite the inode info to reflect the new location. it may take a little while with a huge number of files, but not too long. 

if you open up System -> Administration -> disk Utility, does your disk report that it is healthy? my first guess is that your HDD is dying, but it could be a bad filesystem problem, or even just a bad misconfiguration between the HDD and the system bus. 

if the HDD reports healthy, try running fsck on the drive (you will have to boot off a live CD to scan your / partiton) and see if it is a filesystem corruption.

---

### Post by ubunwhat on 2010-11-10
The self-assessment was good.  The only issue was in reallocated sectors, which is at 13 with a threshold of 36.  The HDD is new and shows no signs of problems in any other areas of operation.

---

### Post by endotherm on 2010-11-10
> **ubunwhat said:**
> The self-assessment was good.  The only issue was in reallocated sectors, which is at 13 with a threshold of 36.  The HDD is new and shows no signs of problems in any other areas of operation.
then the issue is likely with the creation of thumbnails. loading thumbnails can put a huge load on your system when you have just opened a very large folder with many multimedia files. does the lag disappear if you switch to compact view (you will have to wait for it to load once, then switch view, close the window, and open it again to test if it is faster)?

---

### Post by ubunwhat on 2010-11-10
> **HermanAB said:**
> Try Dolphin, Konqueror or Thunar instead of Nautilus.

Aren't those for older versions of Ubuntu?

---

### Post by ubunwhat on 2010-11-10
> **endotherm said:**
> then the issue is likely with the creation of thumbnails. loading thumbnails can put a huge load on your system when you have just opened a very large folder with many multimedia files. does the lag disappear if you switch to compact view (you will have to wait for it to load once, then switch view, close the window, and open it again to test if it is faster)?

As I said  before I turned off thumbnails and it really did not help.  It is as if Nautilus is hanging somewhere in the process itself.

---

### Post by endotherm on 2010-11-10
Hes basically telling you to use kubuntu instead of normal ubuntu. not the advice i'd give


one thing to check, is how much of the delay you are experiencing is actually disk IO. install teh package 'iotop' via software center or wherever and run it from within a terminal. then open your problematic folder and watch what iotop is reading during the lag. 
another simillar utility is 'htop' which is more focused on CPU and Ram usage. see if you can;t find out where the bottle neck is.

---

### Post by ubunwhat on 2010-11-10
> **endotherm said:**
> Hes basically telling you to use kubuntu instead of normal ubuntu. not the advice i'd give

one thing to check, is how much of the delay you are experiencing is actually disk IO. install teh package 'iotop' via software center or wherever and run it from within a terminal. then open your problematic folder and watch what iotop is reading during the lag. 
another simillar utility is 'htop' which is more focused on CPU and Ram usage. see if you can;t find out where the bottle neck is.

I will do that this evening.  Have to run into a meeting but I will try that and report back.  It isn't just one folder though, it is all folders.  And it is random.  For instance,  I may open a folder with, say 1500 documents in it ( again text files and small images ), and try to parse it into other existing folders.  I will move 200 into folder A and it goes instantly.  Next I move 150 into folder B and it goes instantly.  Then I move 120 into folder C and it takes 20 minutes.  After that another 150 goes into folder D instantly.  Then I move 80 into folder E and it takes half an hour.  That's what makes it so maddening.  There is not rhyme or reason to it.

---

### Post by AngusH on 2010-11-10
> **endotherm said:**
> Hes basically telling you to use kubuntu instead of normal ubuntu. not the advice i'd give

Can I suggest we test whether the issue is with nautilus or the IO functionalities.
Could you please fire up a terminal and type in ```
cd /path/to/folder
```(if you experience the problem in your home folder don't bother with this).

Then type in ```
ls
``` and see how long it takes. If this takes a long time then the issue is almost certainly with your drive/filesystem.

Angus

EDIT Just read that your having the problem intermittently, so repeat that a few times to be sure.

---

### Post by ubunwhat on 2010-11-10
> **AngusH said:**
> Can I suggest we test whether the issue is with nautilus or the IO functionalities.
Could you please fire up a terminal and type in ```
cd /path/to/folder
```(if you experience the problem in your home folder don't bother with this).

Then type in ```
ls
``` and see how long it takes. If this takes a long time then the issue is almost certainly with your drive/filesystem.

Angus

steven@Minerva:~$ cd /path/to/folder
bash: cd: /path/to/folder: No such file or directory
steven@Minerva:~$ 1s
1s: command not found
steven@Minerva:~$

---

### Post by AngusH on 2010-11-10
Sorry that's a lower case L in the second command and /path/to/folder should be replaced with a real path that's giving you the issue.
Angus

---

### Post by ubunwhat on 2010-11-10
> **AngusH said:**
> Sorry that's a lower case L in the second command and /path/to/folder should be replaced with a real path that's giving you the issue.
Angus


Again, it's pretty much any given folder.  I'm not sure how to express that path in Linux.  I gather you are talking about the mirror of what would be cd c:/windows/system32/drivers in Windows.  Let's assume that it is a folder in Home/Documents.  How would I express that?

---

### Post by AngusH on 2010-11-10
Since it's causing you problems with any folder you can pretty much forget the first command.

Just for you info, paths in linux start with / and then you have every folder that it's in, each followed by another / . So for example my desktop is as /home/angus/Desktop.

---

### Post by ubunwhat on 2010-11-10
> **AngusH said:**
> Since it's causing you problems with any folder you can pretty much forget the first command.

Just for you info, paths in linux start with / and then you have every folder that it's in, each followed by another / . So for example my desktop is as /home/angus/Desktop.

I'm not sure what I was supposed to get, but when I did this for a typical folder containing 2300 files it gave me a list of all of the files almost instantly.

---

### Post by blackmail on 2010-11-10
What is the filesystem you are using, reiser4 would be a good alternative, but ext4 is also nice. All of these are very good filesystems, you could check the HDD it could be that this is the thing causing the performance, also please post the contents of your fstab
```
sudo cat /etc/fstab
```
paste the thing that is shoown to the thread. I am looking at FS, mounting, or HDD problems in this particular case. 2GB of ram should be enough.

---

### Post by AngusH on 2010-11-10
> **ubunwhat said:**
> I'm not sure what I was supposed to get, but when I did this for a typical folder containing 2300 files it gave me a list of all of the files almost instantly.

Hey, if ls always works then there's nothing wrong with IO, that's what I'm trying to test. However it's hard to be sure when the problem is intermittent. Check it a few times in different folders, if you never get a delay, then the problem almost certainly lies with nautilus.

Angus

---

### Post by ubunwhat on 2010-11-11
Ok, I ran the ls test several times for several folders but the results were always instant.  Never a delay.  I downloaded iotop but that proved useless.  For some reason all of the percentages came back unavailable.  So then I downloaded htop and ran it when things started to hang up in moving files.  In this particular case I was moving 81 files, all either text or small images.  The hang up appeared to be in a process called /usr/lib/gvfs/gvfsd-metadata.  It took nearly 28 minutes to move those 81 files.  This is after moving several hundred from the same folder without a problem and moving several hundred more afterward without a problem.  I have attached the screenshot from htop below if it helps.

---

### Post by ubunwhat on 2010-11-11
I managed to find a few older threads on here of people having the same problem as it related to gvfsd-metadata.  The main difference is that they all claim that this occurred after their HDD maxed out on space.  Mine has never had fewer than 300GB free.  Their solution seemed to be removing the metadata file that is being written, but wouldn't that be a bandage at best?  Isn't the loop in the code that writes to the file?  Am I going to have to kill this process and erase the file a dozen times a day?  


[http://ubuntuforums.org/showthread.php?t=1421580]("http://ubuntuforums.org/showthread.php?t=1421580")

---

### Post by ubunwhat on 2010-11-11
Just ran the fix as listed in other thread and tried to do a simple file operation.  I moved 36 files from one folder to another.  It hung up immediately.  I guess that closes the book on deleting gvfsd-metadata as being the fix.  It is clearly the process itself somewhere.  Any thoughts?

---

### Post by toekneewood on 2010-11-11
I will do a bit of digging around.  But for now to view one of the log files in real time (the last 10 lines).  Open up a terminal and type
```

tail -f /var/log/messages

```
or from your menu select
```

System, Administration, Log file viewer

```

---

### Post by toekneewood on 2010-11-11
How about if you open a terminal and launch nautilus as sudo
```

sudo nautilus

```
Then do the copy.  You might see a message in the terminal.

Would it be possible to format the destination partition using something like gparted?

---

### Post by ubunwhat on 2010-11-11
> **toekneewood said:**
> How about if you open a terminal and launch nautilus as sudo
```

sudo nautilus

```
Then do the copy.  You might see a message in the terminal.

Would it be possible to format the destination partition using something like gparted?

The destination partition is the same as the initial partition.  This is simply moving files between folders in the same partition.  Often times within the same directory. 

I could open nautilus from terminal but again, the problem is intermittent.  Not having a problem in Nautilus from terminal would not really mean much.

I can keep a log file open, I guess, and try to flip to it when things do go wrong.  Which log file would you suggest?

---

### Post by toekneewood on 2010-11-11
I find most things go to 
```

tail -f /var/log/messages

```

I will do a bit of digging around and see if a log exists for general file copy

I wonder if doing a "cp -v /source /destination" might give some verbose output

---

### Post by toekneewood on 2010-11-11
Just another thought, what about a failing disk.  This would give you an intermittent/performance problems.  I use this command to check for dead disks.
```

cat /var/log/messages | grep Unrecovered

```

I also run this script in a crontab (scheduler )once a day, just to check
```

#!/bin/bash
# Author Name: Your Name
# Date: Thu Jul 22 12:34:07 2010   
# Description: Check to see if the you have a pending dead disk and email alert & Backup ~ to /DISK2
# NOTE: preRequisites: needs sendmail and mutt installed to send email
# Version history:
# 1.0   Initial version
# Sync all data from disk1 to disk2

#################################
# Check for possible dead disks #
#################################
SENDTO="your-email@yourdomain.com"
MESSAGE="Unrecovered errors found on DISK"
#This will check the log for Unrecovered disk error and then email one line from the log into the body of the email
if [ $(cat /var/log/messages | grep Unrecovered | wc -l) -ne 0 ]
        then
        echo -e "Please check your disk to see what disk is Unrecovered\n\n$(cat /var/log/messages | grep Unrecovered | tail -n1 )" | mail -s "$MESSAGE" $SENDTO
        #cat /var/log/messages | grep Unrecovered | tail -n1  
else
        echo "NO BAD DISK FOUND :-)"
fi

```

---

### Post by endotherm on 2010-11-11
yeah, the cpu is definitely the bottleneck per the htop output, or more to the point, gvfsd-metadata is not behaving properly. btw if you want to try iotop again, try it with sudo. it may require root. 

just to clarify, on the gvfsd-metadata side of the issue, did you try somthing like
```
mkdir ~/BadMetadata 
mv ~/.local/share/gvfs-metadata ~/BadMetadata/
sudo reboot
```

---

