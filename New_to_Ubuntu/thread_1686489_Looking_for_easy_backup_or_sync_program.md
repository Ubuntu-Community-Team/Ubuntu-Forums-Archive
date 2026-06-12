---
title: "Looking for easy backup or sync program"
date: 2011-02-12
forum: New to Ubuntu
---

### Post by ianp5a on 2011-02-12
I bough a NAS drive and I've been searching for a nice application to do backups of my folders onto it.
This is what I need:
[LIST]
[*]Synchronise Folders on PC to Folders on NAS (Local Network)
[*]Save multiple Sync pairs for separate manual synchronising
[*]Scheduling or change detection to keep the folders up to date
[/LIST]

The only thing I found is Conduit. But it has its problems. And only does manual initiation not regular backups.

I would appreciate any suggestions.

Ian

Ubuntu 10.10

---

### Post by thefasterblueone on 2011-02-12
Try Deja Dup, it is a real simple backup utility. It can be found in Applications> Ubuntu Software Center> Get Software>  and search deja dup.

Here is a link showing how to use it.

[http://www.n00bsonubuntu.net/content/how-to-make-a-backup-using-deja-dup/]("http://www.n00bsonubuntu.net/content/how-to-make-a-backup-using-deja-dup/")

---

### Post by ianp5a on 2011-02-12
Thanks. I've tried that. And most of the other in the software center and one reccommened on various websites.

Deja Dup will only back up one Folder at a time. It can't save several backups. And, in fact it does not save any backup paths at all. So you have to navigate every time. And the worst part is it creates compressed files that I cant access. I need the backed up data accessible as files. So Deja Dup fails on all counts except it can access the NAS.

---

### Post by cipherboy_loc on 2011-02-12
So what you want is a way to sync the state of your system over your local network? Try rsync. It allows you to set up a daemon on one computer, and use another computer to copy every thing (if you log in as root) to another directory. Or you could take the computer you want to back up, mount the network share where you back things up, and use rsync (no daemon) to copy files there.


Cipherboy

---

### Post by asmoore82 on 2011-02-12
rsync

There is a decent graphical frontend to rsync: Grsync.
It also has support for batch operation for scheduled backups.

But be forewarned: scheduled backups left on their own for too long
are backups no more! It's just the nature of the universe - neither could
you drive a car around forever without checking the oil or tires.

To get the most out of rsync, you need a "*smart*" NAS box that supports it natively.
The blazing efficiency of it requires the agent code running on both sides of
the transfer - but it can fall back to do whatever is necessary.

P.S. You never need to set up the rsync dæmon for modern usage unless
you are doing a public archive for anonymous users. The modern rsync,
including Grsync, always uses secure SSH transport unless told otherwise.

---

### Post by ianp5a on 2011-02-12
Thanks. I've tried Grsync. 

Grsync allows me to save several backups, but it does not allow me to select a path on the local network. I could not find a way to schedule backups either. 

Rsync presumably doesn't save the backup paths either. I'm not going to use a command line program. 

So I'm still looking. Remember, save multiple paths, LAN access, and automated starting.

---

### Post by theozzlives on 2011-02-12
> **ianp5a said:**
> Thanks. I've tried Grsync. 

Grsync allows me to save several backups, but it does not allow me to select a path on the local network. I could not find a way to schedule backups either. 

Rsync presumably doesn't save the backup paths either. I'm not going to use a command line program. 

So I'm still looking. Remember, save multiple paths, LAN access, and automated starting.

I'm just going to say that you NEED to learn to function at the CLI. You won't even make it in Windows without learning some CLI.

---

### Post by ianp5a on 2011-02-12
It seems you are not up to date on this. The CLI has not been required in Windows for a long time and is not essential in Linux any more. The vast majority of Windows users have never used a CLI in Windows. I have been using Ubuntu for quite some time and not used a CLI. The guys writing the GUI applications have done a good job. I do not want to use a CLI.

If I can use Linux without using the command line, I can tell others not yet on Linux that the command line is not necessary for using Linux. This will encourage more users.

It seems that rsync does not meet all the criteria either.

---

### Post by asmoore82 on 2011-02-12
> **ianp5a said:**
> Grsync allows me to save several backups, but it does not allow me to select a path on the local network. I could not find a way to schedule backups either.
You can be persistently connected to the backup location and give Grsync that path.
**Or** you can type the true network path into Grsync and it will use it.
An example of such a path would be 'user@nasbox:/media/backups/'

> **ianp5a said:**
> Rsync presumably doesn't save the backup paths either.
It's best never to *presume* anything.
"save the backup paths" is meaningless in the context of a scheduled task.
Should rsync "save the backup paths" or should the task scheduler?

> **ianp5a said:**
> I'm not going to use a command line program.
Don't kid your self, "graphical" and "fully automated" contradict each other.
A pure graphical app cannot even begin to do its job unless you are actively
logged in to a graphical session on a machine. Even if a graphical "wizard"
interface of some kind sets this up for you completely, you must understand
that the "agent" of the scheduled task itself is command line based.
Is and always will be, regardless of the OS.

> **ianp5a said:**
> So I'm still looking. Remember, save multiple paths, LAN access, and automated starting.
The command line rsync does it all. The graphical Grsync does it all.

----------------
P.S.
> **ianp5a said:**
> &#8230; I can tell others not yet on Linux that the command line is not necessary for using &#8230;
That last word there is the key to it all.
If *using* is all you expect, then *using* is all you will get.

Other expectations may include *using*, power using, understanding, mastering,
developing, etc. Again, this is computing in general, regardless of OS.

If you are banging your head on the wall with why networked group polices
aren't working *on Windows*, you will eventually break down to the CLI and
```
gpupdate /force
```

If you want to run multiple independent firefox's you can use the CLI and
```
firefox -no-remote -P
```
Now a shortcut can easily be made to do this for you, but don't *con* yourself
*and others* into believing the command line isn't underneath it all.

This holds true for every shortcut you've ever even thought of clicking.

---

### Post by The Cog on 2011-02-12
I am sure that rsync can do what you want. And it can be scheduled as a cron job however often / whenever you want.

I doubt that it is possible to use grsync to schedule backups although it probably has the capabilities you think it's missing. I suspect you are looking for the -R (or --relative) option. I've never used grsync as I don't want a gui getting in the way of what I want to do.

Really, rsync and cron are the proper tools to solve your backup requirements. If you refuse to use them, then you are just making life difficult for yourself.

---

### Post by scottuss on 2011-02-12
> **asmoore82 said:**
> You can be persistently connected to the backup location and give Grsync that path.
**Or** you can type the true network path into Grsync and it will use it.
An example of such a path would be 'user@nasbox:/media/backups/'


It's best never to *presume* anything.
"save the backup paths" is meaningless in the context of a schedule task.
Should rsync "save the backup paths" or should the task scheduler?


Don't kid your self, "graphical" and "fully automated" contradict each other.
A pure graphical app cannot even begin to do its job unless you are actively
logged in to a graphical session on a machine. Even if a graphical "wizard"
interface of some kind sets this up for you completely, you must understand
that the "agent" of the scheduled task itself is command line based.
Is and always will be, regardless of the OS.


The command line rsync does it all. The graphical Grsync does it all.

----------------
P.S.

That last word there is the key to it all.
If *using* is all you expect, then *using* is all you will get.

Other expectations may include *using*, power using, understanding, mastering,
developing, etc. Again, this is computing in general, regardless of OS.

If you are banging your head on the wall with why networked group polices
aren't working *on Windows*, you will eventually break down to the CLI and
```
gpupdate /force
```

If you want to run multiple independent firefox's you can use the CLI and
```
firefox -no-remote -P
```
Now a shortcut can easily be made to do this for you, but don't *con* yourself
*and others* into believing the command line isn't underneath it all.

This holds true for every shortcut you've ever even thought of clicking.

or ping, nslookup, route etc.

I love it when people argue Windows users don't need to use the CLI.

---

### Post by seshomaru samma on 2011-02-12
What The Cog said:
rsync
cron

/thread

---

### Post by waynefoutz on 2011-02-12
Flyback. It's a clone of Apple's "Time Machine." It uses rsync. 


[http://www.omgubuntu.co.uk/2010/04/flyback-%E2%80%93-time-machine-style-backup-for-ubuntu/]("http://www.omgubuntu.co.uk/2010/04/flyback-%E2%80%93-time-machine-style-backup-for-ubuntu/")

---

### Post by rustutzman on 2011-02-12
Mint has a pretty good backup tool you can load in ubuntu from ppa

[http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html](http://www.webupd8.org/2010/07/install-mintbackup-linux-mint-backup.html)

Russ

Other MintBackup features:
It can check differences in files and perform incremental backups/restorations
It can check the integrity of the files after it copies them
It can backup straight to an archive and compress it on the fly

Since MintBackup is designed for non-geeks mostly, it can only do local backups so if you want something more advanced, I suggest you see what the WebUpd8 readers consider to be the best Linux backup tool.

[http://www.webupd8.org/2010/05/poll-results-best-linux-backup-tool.html](http://www.webupd8.org/2010/05/poll-results-best-linux-backup-tool.html)

---

### Post by rustutzman on 2011-02-12
If you're using NAS you can mount it as a local drive in fstab but you might have to type a little. 

[http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html](http://www.justlinux.com/nhf/Filesystems/Mounting_smbfs_Shares_Permanently.html)

Russ

---

### Post by ianp5a on 2011-02-13
Thanks for the suggestions. I'll try those.

Grsync didn't like the network paths I pasted in. 
smb://server-1tb/public/ and also //localhost/home/ian/.gvfs/server-1Tb/public
Some apps like Conduit allow you to browse the LAN.

As far as Windows goes, some of you might be surprised that most Windows users do not know what the command line is. We are talking about kids and grannies and all sorts. You don't need it ever. Unless you really want to that is. If you like the CLI I can imagine you havn't looked for GUI alternatives. If you do a bit of research you can find some great Linux GUI solutions. Those guys are doing a great job there. You don't even need the CLI for ping on Linux. 

But that is debate for another time and place. 

I really am looking for an app to do all the techie work for me. They do it better than I could. It seems that Mint or Flyback could be the solution.

---

### Post by eentonig on 2011-02-13
> **ianp5a said:**
> ...

As far as Windows goes, some of you might be surprised that most Windows users do not know what the command line is. We are talking about kids and grannies and all sorts. You don't need it ever. Unless you really want to that is. If you like the CLI I can imagine you havn't looked for GUI alternatives. If you do a bit of research you can find some great GUI solutions. Those guys are doing a great job there. You don't even need the CLI for ping on Linux. 

But that is debate for another time and place. 

I really am looking for an app to do all the techie work for me. They do it better than I could. It seems that Mint or Flyback could be the solution.
But then, most Windows users don't have such difficult requirements as you seem to have. 

I spent my time as a sysadmin in a company. And you're right, people don't know the CLI. They just call us whenever something doesn't work, and then my colleagues and I use the CLI or instruct them to type the commands.

No matter how you turn it. For average day to day use, no CLI needed. 

For the techies or anyone who wants more from his system, the CLI is a bless. And if one refuses to learn or use it, he's just doing himself short in so many ways. 

95% of my work CAN be done without CLI. Yet, 95% of my job IS done using the CLI. Not because I have to, but because it's faster, easier, more automated, provides more options, ...

My advice, read the man pages of rsync and cron and experiment with them. Once your satisfied with the result, you'll have learned some cli magic, you'll have a solution that matches your needs 100% and you'll never have to look back at it again.

---

### Post by ianp5a on 2011-02-13
> **eentonig said:**
> But then, most Windows users don't have such difficult requirements as you seem to have.
Yes, that is precisely it. The Windows users can do all their stuff without it. There is always a program designed to do what they need. And the online helpers know all about them. My kids home PCs have never needed any CLI use. And they are connected to the same NAS and have programs that fulfil the requirements.

My requirements are not difficult though. I've found many Linux programs that do 2 of my 3 requirements already. My task is to find the ones that do all 3 comfortably. The forums have lots of helpful people who know about such programs. However, if you are not interested in GUI applications, then it is unlikely that you would have searched for them and use them.

---

### Post by eentonig on 2011-02-13
I've used and use plenty of GUI apps. 

But for most of my non-daily use things, CLI is just faster and more flexible.

In reality, I've found that everything that I want to be automated and/or repetitive, is better done if I take the time to catch up on the cli possibilities.

---

### Post by joris1977 on 2011-02-13
[http://luckybackup.sourceforge.net/](http://luckybackup.sourceforge.net/)

is also a nice gui backup tool. It uses rsync and you can automate backups with it.

---

### Post by Paqman on 2011-02-13
> **ianp5a said:**
> The CLI has not been required in Windows for a long time and is not essential in Linux any more.

I totally agree with you on this. However, rsync and (ana)cron are actually a very effective and easy to use solution.

It's as simple as saving a single line of rsync command (which there are plenty of examples you can simply copy) as a Bash script and dropping it into the appropriate anacron folder. If you want the backup to run hourly, you just put the script in /etc/cron.hourly. Couldn't be simpler, should take you about 5 minutes to set up (although i'd advise doing a bit of testing before you unleash it on your data) Once it's set you just forget about it.

Here's an example of the backup script I use. It's more than one line because i've found it's useful to check the destination is mounted before syncing:
```
#!/bin/sh 

if df |grep -q '/path/to/destination/'
    then
        echo "Found mount point, running task"
        rsync -av --delete /path/to/files/ /path/to/destination/
    else
        echo "Aborted because the disk is not mounted"
        exit -1
fi
```

---

### Post by uaebuntu on 2011-02-13
I use a QNAP NAS connected using nfs and back up 4 computers using simple backup, did the set up using the GUI.

---

### Post by ianp5a on 2011-02-13
Thanks. Luckybackup doesn't seem to allow me to browse to the local network. But its scheduler looks good.
I couldn't get simple backup to install at all.
I'm investigating mounting the LAN somehow, as suggested earlier. But it's a lot of work to find out exactly how to do it on Linux.

---

### Post by aktiwers on 2011-02-13
[http://backintime.le-web.org/](http://backintime.le-web.org/)

Should be in the repos as well

---

### Post by Girya on 2011-02-13
backuppc

uses rsync or tar as the backend and a webpage as the frontend. 

 [http://backuppc.sourceforge.net/]("http://backuppc.sourceforge.net/")

---

### Post by ianp5a on 2011-02-27
Thanks for all those that suggested something.

The initial problem was that many backup programs can only navigate local folders. I have now managed to mount the NAS so that it appears as a Hard Disk (icon), using fstab. It took a long time to get that working as it came up with many different and mysterious errors. For example it was easy to mount with a "network" icon in Nautilus. But that was never visible as a local folder. Amongst the solutions I installed smbfs from the Software center. and I had to use the IP number instead of the server name in fstab. It's a shame that they can't all browse the LAN like Conduit does.

I chose Lucky Backup in the end as it has a nice scheduling setting. So I can do my one click backups as well as fully automated backups.

---

### Post by indusarts on 2011-04-11
I read through this whole thread because I, too, have spent hours trying to find a simple solution to perform scheduled sync/backups to a network drive.  

While this is exceptionally easy in Windows, it is a Herculean task in Linux.  I have used four different, free programs in Windows and all have worked well.  And none needed the command line to accomplish any of it.

I don't understand/ can't find an explanation why Nautilus will see Network Drives, but none of the Sync/BU programs will.  Even if I mount them in Nautilus, the file systems in the Sync/ BU programs still can't see them.

This seems elementary to me, yet I still haven't found a solution.  Why would backup to a network drive be less essential than backing up to a local drive?  

Thanks

Mark Springer
industrial arts

---

### Post by dFlyer on 2011-04-11
> **indusarts said:**
> I read through this whole thread because I, too, have spent hours trying to find a simple solution to perform scheduled sync/backups to a network drive.  

While this is exceptionally easy in Windows, it is a Herculean task in Linux.  I have used four different, free programs in Windows and all have worked well.  And none needed the command line to accomplish any of it.

I don't understand/ can't find an explanation why Nautilus will see Network Drives, but none of the Sync/BU programs will.  Even if I mount them in Nautilus, the file systems in the Sync/ BU programs still can't see them.

This seems elementary to me, yet I still haven't found a solution.  Why would backup to a network drive be less essential than backing up to a local drive?  

Thanks

Mark Springer
industrial arts

Try Deja Dup.

---

### Post by indusarts on 2011-04-11
Deja Dup doesn't allow multiple jobs and only stores compressed files.

I really need to sync more than backup, I keep multiple copies of data in seperate locations in case of drive failure.

Thanks

---

### Post by Blasphemist on 2011-04-11
Back In Time will let you take advantage of rsync and cron for this via its GUI. Best of both these worlds:D

---

### Post by indusarts on 2011-04-11
Thanks

I just installed it, but haven't tested it yet.  It doesn't seem to see network drives, either.

Mark Springer
industrial arts

---

### Post by Blasphemist on 2011-04-11
Could be that it can't see the network. I'm using it with an external USB connected drive. Looks like it should be able to see what the pc can see though.

---

### Post by Locke_99GS on 2011-04-11
Anything that is mounted will exist on your local file system. For FUSE mounted network drives and the sort, look in */media/* or *~/.gvfs/* for your mount.

---

### Post by indusarts on 2011-04-12
Thanks for your help.  I am going to post a different thread because I don't understand how to make the folders on my network server available for the back up programs.

---

### Post by indusarts on 2011-04-13
I finally found out how to access network drives via these programs file manager interfaces.  I had to access them via the .gvfs folder.  

I am suprised that info didn't arise in this thread.

Why don't these programs use Nautilus as a file manager?

Mark Springer
industrial arts

BU - Sync programs on my computer
back in time
deja dup
grsync
lucky backup
simply backup
unison

---

### Post by The Cog on 2011-04-13
> **indusarts said:**
> I finally found out how to access network drives via these programs file manager interfaces.  I had to access them via the .gvfs folder.  
Be careful there. Things that get mounted onto .gvfs are only visible to that user. So a backup program running with root's id (which I expect many automated backup processes do) will not be able to back up those remote files.> 
Why don't these programs use Nautilus as a file managerBecause nautilus is a GUI program and it's hard for backup programs to see where the mouse is and click the buttons at the right time. 

rsync and family are perfectly capable of accessing remote drives using either ssh or the rsync protocol. Or of accessing remote drives that are already mounted into the local filesystem tree (except other user's .gvfs mounts). I think one could argue that mounting remote drives is not the job of a backup program - other programs exists to mount and unmount drives.

---

### Post by Locke_99GS on 2011-04-13
> **indusarts said:**
> I am suprised that info didn't arise in this thread.

It did, 2 posts prior.

---

### Post by indusarts on 2011-04-13
Thanks for your response but that gives me another question.

The file manager in the backup/sync program also has a GUI.  So do I understand correctly that each of these programs is using their own file manager?  Or is there a core Linux file manager with GUI that is commonly used?

From my (very)limited knowledge of programming, I would think that there is a "hook" to call a file manager and any program would use the file manager that is with that desktop.  

For right now there is only a single user - me.  So until I can understand how to mount folders in a way that the program can see them, it will work for right now. 

Thanks again for your help

Mark Springer
industrial arts

---

### Post by seanbw on 2011-04-15
> For right now there is only a single user - me. So until I can understand how to mount folders in a way that the program can see them, it will work for right now.

Right now there are two of you with different levels of access - you as the user and you as root. When you use sudo and its derivatives - you are effectively changing your access level to root which is why Linux is always more secure than Windows. This is also why you  need root access to mount some folders. If you are on a mixed network, the level of access you use to invoke your program determines the folders available to you and the program and if you are using GUI, then you dont actually know your level of access unless you go behind the GUI.

Please correct me if im wrong. but my experience tells me that (plus many a broken pc).

---

### Post by indusarts on 2011-04-15
> Right now there are two of you with different levels of access - you as the user and you as root.

That is an excellent explanation that makes perfect sense.  And it's something I did not understand about Linux but certainly changes the way I look at the operating system.

This is now crossing with another post I made, but I still am having difficulty with the idea - and the method - to mount a share point.  If you have somewhere to direct me to, I'd appreciate it.  

I just found this link - [https://help.ubuntu.com/community/Samba/SambaClientGuide](https://help.ubuntu.com/community/Samba/SambaClientGuide) - which I think tells me how to do it, but I haven't quite sussed it all out.

Thanks

Mark Springer

---

### Post by ianp5a on 2011-04-18
Mark

This is what I did to get the Server mounted:
 
1) Is the server visible somehow in Nautilus?
2) Check if smbfs is installed. (Software center)
3) Create a folder in /media
4) Set the permissions of the folder.
5) Use the mount command in fstab (use the IP number just in case)
*//192.168.178.20/ian/   /media/Servername  cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=0777 0 0*
6) Is the Server mounted with a Hard disk icon (not a folder Icon)
As soon as it has a Hard disk Icon, *all* the backup programs can see it.

---

### Post by indusarts on 2011-04-21
> 4) Set the permissions of the folder.

How do I set them and what do I set them to?

Thanks

Mark Springer
industrial arts

---

### Post by ianp5a on 2011-04-21
Good question. I think it was Right-click on the folder -> Properies ->Permissions tab. Set Owner, Group and Others *all* to "Create and Delete Files".

 1) Is the server connected? i.e. visible somehow in Nautilus?
 2) Check if smbfs is installed. (Software center)
 3) Create a folder in /media
[COLOR="Navy"] 4) Right click on the folder->Properties/Permissions "Create and Delete Files" for Owner,Group,Others.[/COLOR]
 5) Use the mount command in fstab (use the IP number just in case)
*[COLOR="SeaGreen"]//192.168.178.20/ian/ /media/Servername cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=07 77 0 0[/COLOR]*
 6) Check the Server is mounted with a Hard disk icon (not a network folder Icon)

If you anyone can help improve this checklist for non-experts it would be appreciated.

---

### Post by collisionystm on 2011-04-21
Dude. Stop using bogus 3rd party software from the repo's to solve your problem. Do not use .tar. Just use RSYNC. 
 
It is a great program. It does ONE full backup of your system or folder and then everyother time its ran it just backups the data that changed since the last backup. I see it was suggested multiple times and yet no one has explored the idea. It is extremely simple. Do not let the command line scare you because its as simple as this:
 
This is all done in terminal... DO NOT BE AFRAID!!!! Terminal is your friend =)
 
If you are using an external drive, it is probably mounted in /media
 
Open terminal and type cd /media
type ls (LS) to list the subdirectories
Do you see your device??
 
If you are using ubuntu-server with a usb drive, please install usbmount
this will mount your usb drive automatically and place it under /media/usb0 or usb1...etc. depending on how many you have.
 
You cannot set permissions on file systems that are not native to linux I.E. ntfs or fat32 etc...
 
It must be an EXT file system to set your permissions.
 
However, a usb drive should cause no problem to just dump files on. If you want to preserve permissions please format it to ext4 and then proceed using it as backup. Keep in mind, after you do this it will only be usable by linux and you will need to transfer files from your linux box to windows using samba. No more plugging this drive directly into a windows machine.
 
The terminal command for rsync is:
 
rsync -rqa <source> <destination>
I.E. rsync -rqa /home/me/* /media/usb0/
 
Make sure to include the /* after your source. This is a wildcard to grab EVERYTHING in the directory. It will not however grab subdirectories unless you include the -r in the rsync command.
 
r = recursive a.k.a. go into subdirectories
q = quiet, do not print output
a = archive
 
type rsync --help in the terminal to see your other options for preserving permissions...etc.
 
Now just add this to your crontab so it runs automatically
 
crontab -e
 
if this is your first time, use NANO
 
add this line
 
rsync -rqa <otheroptions> <source> <destination>
0 1 * * * rsync -rqa /home/me* /media/usb0/me
 
This says, rsync at 1 am everyday.
 
press CTRL+X then Y to save
 
'crontab successfully installed'
 
To check your files, just cd to your backup destination
 
type ls -lh ( LS -LH ) to show time stamps, NOTE: Your time stamps will vary. This does not mean its not running, just check a few folders and subdirectories.
 
type ls -a ( LS -A ) to check your hidden files.
 
 
Congrats. your backing up like a pro. Now get rid of all that other crap you installed.
 
 
 
> 
Quote:
4) Set the permissions of the folder. 
How do I set them and what do I set them to?
 
Thanks
 
Mark Springer
industrial arts

 
You set permissions using the terminal and chmod.
 
You will 99.9% of the time see chmod using 3 digits
chmod 777 <file>
 
First number is OWNER
second GROUP
third OTHERS
 
chmod <owner><group><others>
Owner of the file, group the file belongs to, and other users trying to access.
 
You can check the files propertys by doing an ls -lh in its parent directory
 
I.E. to check the permissions of your home folder, just cd to /home
 
type ls -lh and look at your folder
 
These are the rules for the chmod numbers
 
7 rwx read, write, execute
6 rw- read, write
5 r-x read, execute
4 r-- read
3 -wx write, execute
2 -w- write
1 --x execute
0 --- no permissions
 
so chmod 000 to keep everyone out but root, 777 to give everyone accesss. 770 to give only owner and group full accesss .... etc.......
 
If its a folder, or you want to include everything in the folder just use this:
 
chmod <numbers> -R <file>
 
I.E. chmod 770 -R /home/collisionystm/
 
sorry for the typo's, I need the coffee to kick in. =)

---

### Post by indusarts on 2011-04-22
> **ianp5a said:**
> Good question. I think it was Right-click on the folder -> Properies ->Permissions tab. Set Owner, Group and Others *all* to "Create and Delete Files".

 1) Is the server connected? i.e. visible somehow in Nautilus?
 2) Check if smbfs is installed. (Software center)
 3) Create a folder in /media
[COLOR="Navy"] 4) Right click on the folder->Properties/Permissions "Create and Delete Files" for Owner,Group,Others.[/COLOR]
 5) Use the mount command in fstab (use the IP number just in case)
*[COLOR="SeaGreen"]//192.168.178.20/ian/ /media/Servername cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=07 77 0 0[/COLOR]*
 6) Check the Server is mounted with a Hard disk icon (not a network folder Icon)

Thanks but it didn't work.

Couldn't change folder permissions from right click, it told me I wasn't the owner.  Changed file permissions from the command line.

Still not clear on your instructions where it says "/media/Servername/".  What do you mean by Servername?  The IP address of the server or the name (in this case Tower) of the server as seen on the network?
What does "guest" mean in your command line?  I do not have quest enabled in Samba.

Thanks

Mark Springer
industrial arts

---

### Post by collisionystm on 2011-04-22
> **indusarts said:**
> Thanks but it didn't work.

Couldn't change folder permissions from right click, it told me I wasn't the owner.  Changed file permissions from the command line.

Still not clear on your instructions where it says "/media/Servername/".  What do you mean by Servername?  The IP address of the server or the name (in this case Tower) of the server as seen on the network?
What does "guest" mean in your command line?  I do not have quest enabled in Samba.

Thanks

Mark Springer
industrial arts

What he means by servername is the folder you created in /Media

You would use the name of the server A.K.A. servername to name the folder so you can keep track.

Your share gets smb mounted on this folder

---

### Post by indusarts on 2011-04-23
Still not working.

The unRaid server ip is 192.117.14.202, the share name is 100g.
It's mounted on the desktop and I can see it in .gvfs
It does not require user name or password.

The folder I created on the Ubuntu computer is /Media/100g
It has permissions to create and delete files.  

I created this line in my fstab file.
//192.117.14.202/100g/ /media/100g cifs guest,rw,iocharset=utf8,file_mode=0777,dir_mode=07 77 0 0

I try to mount it in terminal using "sudo mount /media/100g" and get the error "can't find /media/100g in /etc/fstab or etc/mtab"

---

### Post by killabee44 on 2011-05-01
Collisionytm:

You Da man! This is probably the most complete guide Ive found yet. Thanks a lot man. I really appreciate it!

Edit: Some questions:

1) This requires sudo right? Because I am getting the following errors:


rsync: mkdir "/media/Backup" failed: Permission denied (13)
rsync error: error in file IO (code 11) at main.c(595) [Receiver=3.0.7]
rsync: connection unexpectedly closed (9 bytes received so far) [sender]
rsync error: error in rsync protocol data stream (code 12) at io.c(601) [sender=3.0.7][/CODE]

Also, if it does require sudo, how will I automate it in cron? 

Does Cron already have sudo priviledges? 

(I am guessing so, but thought I'd ask)...

2) Does rsync know to only backup differences in files if they already exist? or is that another option I need to enable?



Thanks.
KB

> **collisionystm said:**
> Dude. Stop using bogus 3rd party software from the repo's to solve your problem. Do not use .tar. Just use RSYNC. 
 
It is a great program. It does ONE full backup of your system or folder and then everyother time its ran it just backups the data that changed since the last backup. I see it was suggested multiple times and yet no one has explored the idea. It is extremely simple. Do not let the command line scare you because its as simple as this:
 
This is all done in terminal... DO NOT BE AFRAID!!!! Terminal is your friend =)
 
If you are using an external drive, it is probably mounted in /media
 
Open terminal and type cd /media
type ls (LS) to list the subdirectories
Do you see your device??
 
If you are using ubuntu-server with a usb drive, please install usbmount
this will mount your usb drive automatically and place it under /media/usb0 or usb1...etc. depending on how many you have.
 
You cannot set permissions on file systems that are not native to linux I.E. ntfs or fat32 etc...
 
It must be an EXT file system to set your permissions.
 
However, a usb drive should cause no problem to just dump files on. If you want to preserve permissions please format it to ext4 and then proceed using it as backup. Keep in mind, after you do this it will only be usable by linux and you will need to transfer files from your linux box to windows using samba. No more plugging this drive directly into a windows machine.
 
The terminal command for rsync is:
 
rsync -rqa <source> <destination>
I.E. rsync -rqa /home/me/* /media/usb0/
 
Make sure to include the /* after your source. This is a wildcard to grab EVERYTHING in the directory. It will not however grab subdirectories unless you include the -r in the rsync command.
 
r = recursive a.k.a. go into subdirectories
q = quiet, do not print output
a = archive
 
type rsync --help in the terminal to see your other options for preserving permissions...etc.
 
Now just add this to your crontab so it runs automatically
 
crontab -e
 
if this is your first time, use NANO
 
add this line
 
rsync -rqa <otheroptions> <source> <destination>
0 1 * * * rsync -rqa /home/me* /media/usb0/me
 
This says, rsync at 1 am everyday.
 
press CTRL+X then Y to save
 
'crontab successfully installed'
 
To check your files, just cd to your backup destination
 
type ls -lh ( LS -LH ) to show time stamps, NOTE: Your time stamps will vary. This does not mean its not running, just check a few folders and subdirectories.
 
type ls -a ( LS -A ) to check your hidden files.
 
 
Congrats. your backing up like a pro. Now get rid of all that other crap you installed.
 
 
 

 
You set permissions using the terminal and chmod.
 
You will 99.9% of the time see chmod using 3 digits
chmod 777 <file>
 
First number is OWNER
second GROUP
third OTHERS
 
chmod <owner><group><others>
Owner of the file, group the file belongs to, and other users trying to access.
 
You can check the files propertys by doing an ls -lh in its parent directory
 
I.E. to check the permissions of your home folder, just cd to /home
 
type ls -lh and look at your folder
 
These are the rules for the chmod numbers
 
7 rwx read, write, execute
6 rw- read, write
5 r-x read, execute
4 r-- read
3 -wx write, execute
2 -w- write
1 --x execute
0 --- no permissions
 
so chmod 000 to keep everyone out but root, 777 to give everyone accesss. 770 to give only owner and group full accesss .... etc.......
 
If its a folder, or you want to include everything in the folder just use this:
 
chmod <numbers> -R <file>
 
I.E. chmod 770 -R /home/collisionystm/
 
sorry for the typo's, I need the coffee to kick in. =)

---

### Post by collisionystm on 2011-05-02
Yes sorry. Do this

```

sudo bash

```

Your now root.

Now run crontab -e and put your entries.

You mainly need to act as root for any kind of stuff like this... so just sudo bash =)

Glad I could help you out!

Oh and yes, you just need to sudo bash and then run your mkdir...etc. 

And rsync does automatically know. It checks itself against the other files as it goes along....kind of a parallel function

Like I said, run

rsync- -help

In the terminal to check the command switches!

---

### Post by collisionystm on 2011-05-02
The sudo crontab is different than a regular user....

---

### Post by killabee44 on 2011-05-02
I do understand that when I create the cron job I should be using sudo bash.

But do I also need to use sudo bash before the command inside the cron? Im not sure I understand that part. 


Ok, so let's say that my rsync says: 

```
0 3 * * 5 /usr/bin/rsync -rqa -r /usr/local/bin.* /media/250Backup/backups/usr/local/
```

I should really be using: 

```
sudo bash 0 3 * * 5 /usr/bin/rsync -rqa -r /usr/local/bin.* /media/250Backup/backups/usr/local/
```



Also, If I need to schedule multiple jobs in the crontab for rsync (different origin and destination folders), do I need to schedule them at different times? Or will rsync do one after the other? Can I put them on for the same day/time?

I only ask because I don't really want multiple instances of rsync copying files at the same time.)


One file I would like to backup with rsync is fstab. I run: 

```
rsync -rqa -r /etc/fstab.* /media/250Backup/backups/etc/
```

but I get a "no such file or directory" error. What am I doing wrong there?


Im having a serious issue with this one: 

```
rsync -rqa -r /etc/.* /media/250Backup/etc/
```

for some reason rsync fills up my backup drive completely. Im not sure what is going in there. I can't tell because the files look just like the normal /etc files. 

The etc folder is only supposed to be 10mb. How can this be happening?





Do I need to create the folder that I specify in the command? Or will rsync create any target folders that are not already there? 



Thanks again.

> **collisionystm said:**
> Yes sorry. Do this

```

sudo bash

```

Your now root.

Now run crontab -e and put your entries.

You mainly need to act as root for any kind of stuff like this... so just sudo bash =)

Glad I could help you out!

Oh and yes, you just need to sudo bash and then run your mkdir...etc. 

And rsync does automatically know. It checks itself against the other files as it goes along....kind of a parallel function

Like I said, run

rsync- -help

In the terminal to check the command switches!

---

