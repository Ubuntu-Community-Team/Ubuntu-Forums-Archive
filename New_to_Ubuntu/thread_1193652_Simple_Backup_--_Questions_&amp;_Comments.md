---
title: "Simple Backup -- Questions &amp; Comments"
date: 2009-06-21
forum: New to Ubuntu
---

### Post by knomaly on 2009-06-21
The following questions and comments regard the Simple Backup (SB) program. They are divided into two sections. The first section regards what is written in Chapter 31 titled "Backing Up Data", of Keir Thomas and Jaime Sicam's book "Beginning Ubuntu Linux: Third Edition" ( C2008 ). The second section consists of SB questions and comments (Q&C) that are more general in nature.
 
=====
 
SB: Book Q&C:  
 Beginning Ubuntu Linux: Third Ed:  
 Chapter 31: Backing Up Data > Using Simple Backup
 
-----
 
Page 602. Topic: Backing Up Data via Simple Backup > Use recommended backup settings
 
"This is by far the best choice for fuss-free operation. . .[SB] will deliberately exclude any multimedia files (because of their large size), along with any temporary files and files of any type that exceed 100MB (again for size reasons)."
 
Q&C:  
 
Why does this recommended backup setting qualify as the "best choice" if it excludes multimedia files? The implication here is that an additional backup program must be used if SB is employed. However, no backup program optimized for backing up larger files is recommended. This also begs the question, don't most people want to backup their multimedia and text files with just one program, excluding the use of online backup utilities for archiving smaller files?
 
-----
 
Page 603. Topic: Backing Up Data via Simple Backup > Including Files and Folders in the Backup Job  
 
For custom backup: Backup Properties [dialog box] > Include: Files/Directories. "Bear in mind that adding a directory does so recursively. . .For this reason, you don't need to specifically add your /home/<username> directory, because the entire /home directory is included in the backup by default. This means that the backup will also include all other users' directories within /home, too.  
 
Q&C:  
 
SB is designed to backup personal and configuration data, excluding multimedia-type files, for all user accounts. Due to the use of recursion, for any backup job, SB will not permit the inclusion of specific child directories within /home/<username>/, to the exclusion of other directories within /home/<username>/. For example: SB will not back up data that only resides in the Mozilla Thunderbird directory (/home/<username>/.mozilla-thunderbird) for a given user account, to the exclusion other directories in the user's home directory.
 
-----
 
Page 604. Topic: Backing Up Data via Simple Backup > Changing the Backup Directory Destination
 
The default backup directory = "/var/backup". You can choose to save your SB backup archive to another location, but "In most cases, we advise that you use /var/backup to store the newly created backup files, and copy the files to their permanent destination later. You might even choose to do this periodically and automatically. . .you could set up a cron job to automatically copy the files to a network mount or removable storage device. . ."  
 
Q&C:  
 
What advantage is there in storing the newly created backup files in /var/backup, and then copying them to an external storage destination? Why would this two-step "archive and copy" process be recommended over selecting an external target/storage destination?
 
-----
 
Page 605. Topic: Backing Up Data via Simple Backup > Changing the Time Period Between Backups
 
Backup Properties > Time tab: Set backup frequency: Hourly, Daily, Weekly, etc., and precise or imprecise (simple) time of backup: day of month, week, hour, or minute.
 
Q&C:
 
For all SB backup jobs where the backup frequency is set (excluding the "manual" backup setting), how does a user know that a backup job has been either executed or completed, or is in operation?  
 
What process priority is an SB backup job given?  
 
Does SB support the live or real time backup feature, in which a backup is made in the background (during idle or less CPU-intense periods) while the user is working in their account, or must the account be kept inactive during the backup job?  
 
What effect do open files have on the backup process?  
 
How would a cron job be set up to automatically copy the archive files after the completion of a backup job? What kind of reporting utility can be used to indicate that both jobs, archive and cron, have been properly completed?
 
Is there an easy way to specify that the computer enter one of three power modes: standby, hibernate, or shutdown, after backup job completion or copy of the archive files, if a cron job is run in addition to the backup job? If "yes", then please explain the process.
 
-----
 
Page 605. Topic: Restoring Data via Simple Backup
 
"Restored files and directories are owned by root. . ." Use the sudo and chown commands ". . .to change the ownership and group of the file to what they were originally. See Chapter 14 for more details about file ownership and how the chown command works."
 
Q&C:  
 
Working examples of valid file ownership restoration procedures are not provided, in either Chapter 31 or 14, for a hypothetical beginning Ubuntu user who backed up data using SB's "recommended" settings, and thus archived personal and configuration data for one or more user accounts. Why?
 
Note: For the beginning Ubuntu user, it is likely that the specifics of the file ownership restoration procedure is a function of Ubuntu's default file ownership settings for personal and configuration data in each user account. But considering the variety of files and folders in each user account, what are these file ownership settings?
 
=====
 
SB: General Q&C:
   
 Is Simple Backup (SB) under active project development? If "no", then why not?
 
Does SB use compression? If "yes", then what kind and level of compression does SB use? If "no", then why not?
 
Is any integrity verification routine built into SB's archive or restoration process to ensure that the data backed up or restored is not corrupt? If "no", then why not?
 
What are the range of filesystems that SB will backup data to? How do the various filesystems supported, other than ext3, effect file permissions settings and file restoration in general?
 
How well does SB handle filename changes? What about spaces in the filenames?  
 
-----
 
SB Backup Properties: Include and Exclude tabs
 
Default paths:
 Include: /var/, /home/, /usr/local/, etc
 Exclude: /proc, /sys/, /var/cache/, /tmp/, /dev/, /var/tmp/
 
Should the default paths listed for both SB's Include and Exclude functions be used as a reference for all backups performed by general users, whether or not the backup utility used is SB, rsync, tar, or of another kind? Why wouldn't the default paths listed by alphabetized?

---

### Post by HermanAB on 2009-06-21
Hmm, rsync is your friend.

---

### Post by knomaly on 2009-10-08
The following represents a sample, composite FYI for the Ubuntu community:
 
I am a novice Linux user, running Ubuntu 9.04 Desktop on several laptops at home, who is searching for one or more powerful, stable, user-friendly backup utilities that can handle filename changes and longer filenames that read like sentences, and therefore include such things as spaces and special characters, for instance: 

2009-06-09 -- rpa -- Greens' UN climate advice: slash CO2, pay $160 billion.odt 

In my search for such a program or two, I came across several excellent articles that describe rsync and its variants. One article is titled "Backing Up to the Clouds" by Marcel Gagne, published in the April edition of the Linux Journal. Another article is by freelance systems engineer Federico Kereki. It is titled "The rsync family", dated April 14, 2009, and published on IBM's website.  
 
While both articles are excellent in their scope, and compliment one another well, before I begin using a more advanced backup tool for backing up my home folder to a USB HDD, or backing up to a NAS compatible with multiple platforms, I would like to get some authoritative feedback regarding what backup solutions would be most appropriate for my needs, considering the wealth of backup options available to Linux users. I would also like to better understand exactly what directories, outside of the user home directory, to back up. 

With respect to specific backup solutions, I am aware that there are cloud-based backup options like SpiderOak, DropBox and Ubuntu One, which may be great for backing up smaller files, but considering the throughput penalties exacted by the combination of end-to-end encryption and real-world, last-mile Internet constraints for the home user, how is one to backup larger multimedia-type files that so dominate the storage landscape? 

Please note that I have considered a local NAS option, even a NAS to NAS replication option for remote backup, but there are power consumption, compatibility, complexity, and maintenance issues (server software must be kept up-to-date, passwords periodically changed, etc). 

To keep things simple, perhaps it would be best to purchase several external drives for each home computer, and then rotate the drives once a week or every two weeks, but even that can get complicated and costly. 

No doubt there's a growing demand for simple, secure, dependable, and "green" backup solutions across the computing spectrum, considering the increasing importance and centrality digital data has in our lives. The response to this demand in the Windows and Mac worlds that service the home user is increasing in strength, but I do not yet see a comparable response from the Linux community, as made evident by the dearth of information pertaining to backup solutions found in most books and other material targeted at educating the beginning Linux user. 

For example, check out the absence of backup how-to material found in the "Linux Starter Pack", a 132 page special Linux Format beginner's guide published in October 4, 2008, freely available for the public to download. Also, check out the dearth of backup information presented in Keir Thomas' books, from his recently-published "Ubuntu Pocket Guide and Reference", also free to download, to his "Ubuntu Kung Fu" and third edition "Beginning Ubuntu Linux". 

Note how the last two books focus primarily on using Simple Backup (SB). The problem with the SB explanations given in these books is manifold, and includes such things as: 

* Material on backing up data is presented at the end of the texts, rather than near the beginning where it belongs. If a user loads his data after installing the OS and tightening desktop security, then the next logical thing is to backup his data. 

* SB is a program that is not under active development. 

* SB's limitations are not described in detail. 

Regarding articles like Marcel Gagne's, I would like to see more working examples, particularly targeted at addressing the interests of beginning-level Linux users. I would also like to see more information regarding backup file integrity verification and restoration techniques to help avoid file corruption and ensure that everything restores properly. 

In summary, I am under the impression that more work is necessary in the Linux community to provide high-quality, real-world working examples addressing preferred backup strategies, tools, methods, restoration techniques, etc, particularly if the community is serious about not just attracting Linux newbies like myself, but keeping them invested in this remarkable open source movement which fosters such things as transparency, accountability, sharing, cooperation, and trust through honest community engagement.
 

Material cited:
 
Backing Up to the Clouds: [http://www.linuxjournal.com/article/10409](http://www.linuxjournal.com/article/10409)
 The rsync family: [http://www.ibm.com/developerworks/aix/library/au-rsyncfamily/index.html](http://www.ibm.com/developerworks/aix/library/au-rsyncfamily/index.html)
 Linux Starter Pack: [http://www.tuxradar.com/linuxstarterpack](http://www.tuxradar.com/linuxstarterpack) 
 Ubuntu Pocket Guide and Reference: [http://www.ubuntupocketguide.com/index_main.html](http://www.ubuntupocketguide.com/index_main.html)

---

### Post by knomaly on 2009-10-08
[SIZE=1]Other related topics: 

*Disk partitioning: data on one side, OS on the other.

*File permissions: external device, ext3 or ext4 formatted, etc., as described on this thread, under the heading  “gksu nautilus error message” @ [/SIZE][SIZE=1]http://ubuntuforums.org/showthread.php?t=1283457
[/SIZE]

---

### Post by Zill on 2009-10-09
That's a lot of questions, knomaly :-)  As a SBackup user I will *try* to answer a few of them...

> **knomaly said:**
>  
Why does this recommended backup setting qualify as the "best choice" if it excludes multimedia files? The implication here is that an additional backup program must be used if SB is employed. However, no backup program optimized for backing up larger files is recommended. This also begs the question, don't most people want to backup their multimedia and text files with just one program, excluding the use of online backup utilities for archiving smaller files?

[COLOR="Red"]Multimedia files are rarely unique and, as such, can easily be recovered from elsewhere in the event of data loss on *your* PC.  However, Simple Backup is *very* configurable and so, if you want to include these files then feel free to do so![/COLOR]
  
SB is designed to backup personal and configuration data, excluding multimedia-type files, for all user accounts. Due to the use of recursion, for any backup job, SB will not permit the inclusion of specific child directories within /home/<username>/, to the exclusion of other directories within /home/<username>/. For example: SB will not back up data that only resides in the Mozilla Thunderbird directory (/home/<username>/.mozilla-thunderbird) for a given user account, to the exclusion other directories in the user's home directory.

[COLOR="Red"]As before, SBackup can be configured to include or exclude whichever specific directories *you* choose![/COLOR]
 
What advantage is there in storing the newly created backup files in /var/backup, and then copying them to an external storage destination? Why would this two-step "archive and copy" process be recommended over selecting an external target/storage destination?

[COLOR="Red"]You can configure SBackup to save to any local or remote destination.  For example, I save directly to a remote PC via NFS.[/COLOR]

For all SB backup jobs where the backup frequency is set (excluding the "manual" backup setting), how does a user know that a backup job has been either executed or completed, or is in operation?

[COLOR="Red"]Simple answer - you don't!  SBackup runs in the background and the process can be monitored but it is necessary to monitor the destination location to verify that all the files have been backed-up.[/COLOR]

What process priority is an SB backup job given?

[COLOR="Red"]No idea![/COLOR]
 
Does SB support the live or real time backup feature, in which a backup is made in the background (during idle or less CPU-intense periods) while the user is working in their account, or must the account be kept inactive during the backup job?  

[COLOR="Red"]Obviously the backup process does use the CPU - if you have a fast PC then backups may not slow things down too much.  However, I avoid the problem by running my backups at night when I am tucked-up in bed. :-)[/COLOR]

What effect do open files have on the backup process? 

[COLOR="Red"]Nothing as far as I know.  SBackup just creates a "snapshot" of the files in their current state.[/COLOR]

How would a cron job be set up to automatically copy the archive files after the completion of a backup job? What kind of reporting utility can be used to indicate that both jobs, archive and cron, have been properly completed?

[COLOR="Red"]A cron job is set up in exactly the same way as any other! (man cron)  If you want to report on this I would think you would need to write a bash script.[/COLOR]
 
Is there an easy way to specify that the computer enter one of three power modes: standby, hibernate, or shutdown, after backup job completion or copy of the archive files, if a cron job is run in addition to the backup job? If "yes", then please explain the process.

[COLOR="Red"]No idea - I only use desktops![/COLOR]
 
Note: For the beginning Ubuntu user, it is likely that the specifics of the file ownership restoration procedure is a function of Ubuntu's default file ownership settings for personal and configuration data in each user account. But considering the variety of files and folders in each user account, what are these file ownership settings?

[COLOR="Red"]SBackup runs as root.  However, it is easy to change the ownership of restored files with the chown command, or via the Nautilus GUI.  Most files within a user account will be owned by that user.[/COLOR]

Is Simple Backup (SB) under active project development? If "no", then why not?

[COLOR="Red"]Probably - it has received regular updates over the years.  You must appreciate that most FOSS developers are, in general, volunteers and, as such, we cannot *demand* that they work on a particular project.  I personally am very grateful for the time and effort they devote to giving us such great software.[/COLOR]
 
Does SB use compression? If "yes", then what kind and level of compression does SB use? If "no", then why not?

[COLOR="Red"]SBackup uses the standard gzip compression system.[/COLOR]

Is any integrity verification routine built into SB's archive or restoration process to ensure that the data backed up or restored is not corrupt? If "no", then why not?

[COLOR="Red"]I don't know of any verification.  However, if you believe this would be useful then please help with the development of such a feature.[/COLOR]
 
What are the range of filesystems that SB will backup data to? How do the various filesystems supported, other than ext3, effect file permissions settings and file restoration in general?

[COLOR="Red"]SBackup should backup to any file system that you can mount to your root directory.  I would guess that any constraints on filenames and permissions etc will be those of your chosen filesystem.  i.e. if you saved your backups to a FAT filesystem I doubt that permissions would be retained.[/COLOR]
 
How well does SB handle filename changes? What about spaces in the filenames?  

[COLOR="Red"]Don't know about changes.  Spaces seem to be handled correctly if you use a suitable Linux filesystem such as Ext3 or Reiser.[/COLOR]

Should the default paths listed for both SB's Include and Exclude functions be used as a reference for all backups performed by general users, whether or not the backup utility used is SB, rsync, tar, or of another kind? Why wouldn't the default paths listed by alphabetized?

[COLOR="Red"]The default paths are, IMHO, a good guide for "general" users.  However, they are not "carved in stone" so you are, of course, quite welcome to change them to suit *your* usage.[/COLOR]
I appreciate you have put considerable time into thinking about backups - quite wisely IMO :-)

All I can say is that I have used SBackup on a regular, automated, basis on several PCs for years now with no problems.  All applications can be improved and the great thing about Free and Open Source Software (FOSS) is that we can all play a part in this.  I am sure your ideas and assistance will be appreciated by the development team.  Take a look at [this link]("http://sourceforge.net/projects/sbackup/develop") for more details.

---

### Post by knomaly on 2010-11-29
[FONT=Arial][SIZE=2]Zill, thank you for the time you took last October to respond to my questions regarding Simple Backup! Hats off to the excellent help you provided!

PS: Since the time that I posted my first message on this subject last June, I have examined some first-rate books that provide additional insight into the Unix, Linux, and Ubuntu Linux environments. For instance:[/SIZE][/FONT] [FONT=Arial][SIZE=2]


Schwartz, David I. [/SIZE][/FONT] [FONT=Arial][SIZE=2]_Introduction to UNIX: Second Edition_. New Jersey: Pearson Education, 2006.

Taylor, Dave. _Unix in 24 Hours - Fourth Edition_. U.S.A: Sams Publishing, 2006.

Negus, Christopher., & Caen, Francois. _Ubuntu Linux Toolbox: 1000+ Commands for Ubuntu and Debian Power Users_. Indianapolis, Indiana: Wiley Publishing, 2008.

Sobell, Mark G. _A Practical Guide to Ubuntu Linux_. Boston, MA: Pearson Education, 2011.


[/SIZE][/FONT]  [FONT=Arial][SIZE=2]These books, in conjunction with a variety of articles published on this topic like the one titled "[/SIZE][/FONT][FONT=Arial][SIZE=2]Best Linux backup software: 8 tools on test[/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=#000000]. [/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2]In Depth: What's the best Linux backup tool for home use?" [/SIZE][/FONT][FONT=Arial][SIZE=2][COLOR=#000000]b[/COLOR][/SIZE][/FONT][FONT=Arial][SIZE=2]y Shashank Sharma, which was [/SIZE][/FONT][FONT=Arial][SIZE=2]posted on techradar last Saturday, and [/SIZE][/FONT][FONT=Arial][SIZE=2]cited on internet.com's Linux Today, have also been beneficial. 

Link to article: [/SIZE][/FONT][http://www.techradar.com/news/software/applications/best-linux-backup-software-8-tools-on-test-909380](http://www.techradar.com/news/software/applications/best-linux-backup-software-8-tools-on-test-909380)

---

