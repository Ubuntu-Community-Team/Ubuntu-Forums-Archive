---
title: "Backup Script I wrote (with help of others) check it over?"
date: 2009-03-11
forum: New to Ubuntu
---

### Post by altech6983 on 2009-03-11
Hey guys, I am working on this backup script and I pretty much have it is done, I just wanted to have y'all check it over. I have already run it and I know it works, I just though there may be better ways to do some of the stuff in there and I like learning better ways. So what do you think? (Of course this is free for sharing, modifications, bla bla, all that good stuff.)

```
#!/bin/bash
#This is a simple script that I wrote to clean up Ubuntu and then backup to my external hard drive.
#This script will empty uers trash, removes residual config files, removes partial packages, and removes orphaned packages then starts the backup process.
#This script requires that you have the wajig, deborphan, and trash-cli packages installed
#You must chmod +x this script.

#Test to see if wajig is installed. If $?=1 then it is not installed.
dpkg-query -l wajig
if [ $?=1 ]; then
	apt-get -y install wajig
fi

#Test to see if deborphan is installed. If $?=1 then it is not installed.
dpkg-query -l deborphan
if [ $?=1 ]; then
	apt-get -y install deborphan
fi

#Test to see if trash-cli is installed. If $?=1 then it is not installed.
dpkg-query -l trash-cli
if [ $?=1 ]; then
	apt-get -y install trash-cli
fi

dialog --yesno 'Are you ready to start the backup process? (This will empty users trash! Remove all residual config files! Remove all partial packages! Remove all orphaned packages! ##Please close all open windows except for this terminal##)' 9 60

#Checks the yes or no status of answer
if [ $? = 0 ]; then

	#Removes all residual config files
	for package in `grep -B1 config-files /var/lib/dpkg/status | grep -v -- '--' | grep -v 'Status:' | awk '{ print $2 }' `; do
		echo "Removing $package residual config files"
		wajig purge $package
	done

	#Removes partial packages
	apt-get -y autoclean

	#Removes orphaned packages
	deborphan | xargs sudo apt-get -y remove --purge

	#Empties user trash
	empty-trash

	#Unmounts my attached drives (You need to edit this one to your specific system)
	umount /dev/sda2
	umount /dev/sdd5
	
	#Mounts and switches to the external drive that will contain the backup
	mount /dev/sdd5
	cd /media/"My Book B"

	#Finds current date
	NOW=$(date +"%b-%e-%y")

	#Backs up all files excluding proc, lost+found, media, mnt, and sys folders, to a file named backup-Currentdate.tar.bz2
	tar cvpjf backup-$NOW.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys /
	
	#Remounts drives that were unmounted
	mount /dev/sda2
else
	exit 1
fi
exit 0
```

Edit 3-11-09 8:40PM Central
inserted "not" before the three installs.

---

### Post by binbash on 2009-03-11
I will test it out but first i have to rewrite it a little for me

---

### Post by lovinglinux on 2009-03-11
I liked the part that you check if a dependency is installed. It would be nice to use it on my FF extension, but I can't get it to work.

When I run a script to check an installed application like this

```
dpkg-query -l xmlstarlet
```

the output is 

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  xmlstarlet     1.0.1-2        command line XML toolkit
```

When I check an application not installed like this:

```
dpkg-query -l miro
```

the output is:

```
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
pn  miro           <none>         (no description available)
```


On both cases, the code will execute the commands after "then". Additionally, since *if $?=1*  means the application is installed, why *apt-get -y install* is in the place where the condition is satisfied?

---

### Post by altech6983 on 2009-03-11
Thanks for the compliment, this is even my first script. Took me about three or four hours to cobble it together.

dpkg-query will return with a exit code of 0 if it is installed and a 1 if it isn't.

That should be it, but then again I can't really help you much more than that as I just started scripting.

---

### Post by brokentroy on 2009-03-11
I'd like to use this, but I am a total noob and don't understand how to run it.  I copied the script into a txt editor and saved it to my home file as "backup".  I ran the chmod on it.  When I browse to it and type in backup I get "The program 'backup' is currently not installed.  You can install it by typing:
sudo apt-get install openafs-client".  I know I am doing something wrong, but I don't know what.  

Sorry, I'm still very new to linux, but trying to learn as much as I can.  

thanks guys.

---

### Post by brokentroy on 2009-03-11
hey,  figured it out.  lol.  just found this website to explain it all. [http://www.linfo.org/create_shell_1.html](http://www.linfo.org/create_shell_1.html)

thanks anyway!  I'll let you know if it works for me.

Troy

---

### Post by altech6983 on 2009-03-11
@lovinglinux: sorry about the confusion, I can understand why, there should have been a "not" before those three installs (typo). Should make sense now.

@brokentroy: Don't forget to change the paths to fit your system. I am going to work on writing a better version.

Also if anyone knows how to auto detect and auto unmount non-necessary drives and then remount the ones the script unmounted that would be helpful.

---

### Post by brokentroy on 2009-03-11
thanks.  I did notice that afterwards and did make those changes.  However, when I ran it again it still tried to make the tar file in my home directory.  I'm sure that will cause problems as over half of my dirve is used up laready, so it won't be able to write roughly the same amount back to it.  

I did the queries and also got the same response as lovinglinux.  do i need to change something else. here's what my file looks like

> #!/bin/bash
#This is a simple script that I wrote to clean up Ubuntu and then backup to my external hard drive.
#This script will empty uers trash, removes residual config files, removes partial packages, and removes orphaned packages then starts the backup process.
#This script requires that you have the wajig, deborphan, and trash-cli packages installed
#You must chmod +x this script.

#Test to see if wajig is installed. If $?=1 then it is installed.
dpkg-query -l wajig
if [ $?=1 ]; then
	apt-get -y install wajig
fi

#Test to see if deborphan is installed. If $?=1 then it is installed.
dpkg-query -l deborphan
if [ $?=1 ]; then
	apt-get -y install deborphan
fi

#Test to see if trash-cli is installed. If $?=1 then it is installed.
dpkg-query -l trash-cli
if [ $?=1 ]; then
	apt-get -y install trash-cli
fi

dialog --yesno 'Are you ready to start the backup process? (This will empty users trash! Remove all residual config files! Remove all partial packages! Remove all orphaned packages! ##Please close all open windows except for this terminal##)' 9 60

#Checks the yes or no status of answer
if [ $? = 0 ]; then

	#Removes all residual config files
	for package in `grep -B1 config-files /var/lib/dpkg/status | grep -v -- '--' | grep -v 'Status:' | awk '{ print $2 }' `; do
		echo "Removing $package residual config files"
		wajig purge $package
	done

	#Removes partial packages
	apt-get -y autoclean

	#Removes orphaned packages
	deborphan | xargs sudo apt-get -y remove --purge

	#Empties user trash
	empty-trash

	#Unmounts my attached drives (You need to edit this one to your specific system)
	umount /dev/sda1
        umount /dev/sdb1
        umount /dev/sdb2
	
	#Mounts and switches to the external drive that will contain the backup
	mount /dev/sdb3
	cd /media/New Volume

	#Finds current date
	NOW=$(date +"%b-%e-%y")

	#Backs up all files excluding proc, lost+found, media, mnt, and sys folders, to a file named backup-Currentdate.tar.bz2
	tar cvpjf backup-$NOW.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys /
	
	#Remounts drives that were unmounted
	mount /dev/sda1
else
	exit 1
fi
exit 0

---

### Post by theozzlives on 2009-03-11
Looks good from what I remember from programming. To "hard coded" for my uses though.

---

### Post by lovinglinux on 2009-03-11
> **altech6983 said:**
> @lovinglinux: sorry about the confusion, I can understand why, there should have been a "not" before those three installs (typo). Should make sense now.

No problem, but I still don't get it. I don't think you can put a "not" in front of install. Besides, if it's not supposed to install, why running a "notinstall" command in the first place?

The code should check if it is installed. If it is not, then the install command should be executed. What you are proposing now, is that if the the program is installed then run a "notinstall" command. But if it isn't, then nothing will happen, because there isn't an install command when the condition is zero.

Anyways, it seems that the condition does not return a 0 or a 1, because the command after the condition is executed, no matter if the application is installed or not.

---

### Post by altech6983 on 2009-03-12
@brokentroy: Try this version that I posted and see what happens (Take note of the changes I made ;) )

Would have replied earlier but this posting box kept telling me that I had to post more than one character? I switched it from full editor to simple editor and that seems to have fixed it.

sorry lovinglinux, I didn't even notice but it wasn't even working on my code, this programming goes over my head sometimes. I did figure it out though, there needed to be a space in-between like this $? = 1 instead of $?=1. That should fix it.

I am posting a new version that I have modified:

It now doesn't unmount or mount any drives. (Function not really needed due to the exclusion of the /mnt and /media directories)

It will now let you enter the path for the saving directory and the backup directory in the form of ./nameofscript /savingdirectory /backupdirectory

It now checks the paths entered to make sure they exist (make sure you mount the drive you want your backup on ;) )

I removed the pre-checking for the dependencies as apt-get really does the same thing, if it is installed it just continues if it isn't then it installs and continues.

This should be a little better now, and just forget about the auto mount and unmount thing I posted earlier.

New Version

```
#!/bin/bash
#This is a simple script that I wrote to clean up Ubuntu and then backup to my external hard drive. It requires two arguments ./nameofscript [Path to save archive] [Path to backup]
#This script will empty users trash, removes residual config files, removes partial packages, and removes orphaned packages then starts the backup process.
#This script requires that you have the wajig, deborphan, and trash-cli packages installed
#You must chmod +x this script.

#Checks to see if directory entered exist, if not it exits
if [[ ! -d "$1" ]]; then
    echo "Error, no backup files made, storage directory does not exist!"
    exit 1
fi

if [[ ! -d "$1" ]]; then
    echo "Error, no backup files made, backup directory does not exist!"
    exit 1
fi

#Installs dependencies
apt-get -y install wajig
apt-get -y install deborphan
apt-get -y install trash-cli

dialog --yesno 'Are you ready to start the backup process? (This will empty users trash! Remove all residual config files! Remove all partial packages! Remove all orphaned packages! ##Please close all open windows except for this terminal##)' 9 60

#Checks the yes or no status of answer
if [ $? = 0 ]; then

	#Removes all residual config files
	for package in `grep -B1 config-files /var/lib/dpkg/status | grep -v -- '--' | grep -v 'Status:' | awk '{ print $2 }' `; do
		echo "Removing $package residual config files"
		wajig purge $package
	done

	#Removes partial packages
	apt-get -y autoclean

	#Removes orphaned packages
	deborphan | xargs sudo apt-get -y remove --purge

	#Empties user trash
	empty-trash

	cd "$1"

	#Finds current date
	NOW=$(date +"%b-%e-%y")

	#Backs up all files excluding proc, lost+found, media, mnt, and sys folders, to a file named backup-Currentdate.tar.bz2
	tar cvpjf backup-$NOW.tar.bz2 --exclude=/proc --exclude=/lost+found --exclude=/media --exclude=/mnt --exclude=/sys "$2"

else
	exit 1
fi
exit 0
```

---

### Post by brokentroy on 2009-03-12
Thanks.  I'll give it a try and let you know how it works.

---

### Post by brokentroy on 2009-03-13
I'm sorry. where do I enter the directories?  I'm really new to this.  thanks.

---

### Post by brokentroy on 2009-03-13
ok  figured that part out. I have to enter it in the terminal.  However, now I get

here's what I am entering 

> troy@troy-laptop:~$ sudo ./filebackup /media/disk-2

Here's what I get

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
wajig is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
deborphan is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
trash-cli is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.


Then the prompt.

Then:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
tar: Substituting `.' for empty member name
tar: : Cannot stat: No such file or directory
tar: Error exit delayed from previous errors

A Tar file was created on my external, but nothing was written to it.

---

### Post by brokentroy on 2009-03-13
ok.  Progress.  lol.

I typed in this

> sudo ./filebackup /media/disk-2 Archive

I got the prompt and hit yes.  this time i got no errors.  A tar.bz2 was created with a directory in it called Archive.  However,  the Archive folder is empty.  

I'll keep playing.

---

### Post by brokentroy on 2009-03-13
Got it!  Works great.  Thanks.  Takes a long time though.  lol.  I have 35 gig to back up.  Started it around 1:30 am.  At 8:30 it was still running.  But then again, that is a heck of a lot of data.  I assume that from now on it will only back up anything new or newly modified?  

Anyway, for those who want to know.  Here's what I did.

Open Text Editor.  Copy and paste the code above into it (the second one altech created, not the first).  Save it to your home directory.  Open a terminal and type 

> sudo chmod +x *filename*

This gives you read/write permission to the file.

Hook up your external and let it mount.  Go to Places>Computer and take note of your external's path.  Mine was /media/disk-2.

In the terminal type 

> sudo ./*filename* /*backuppath* /*sourcepath*

*Backuppath* is where it is going. *Sourcepath* is what you want backed up.  

For example, mine looked like this:

> troy@troy-laptop:~$ sudo ./filebackup /media/disk-2 /home/troy

The script will run and you will get a prompt.  Select Yes.

If all goes well a tar.bz2 file should have been created on your external and you will see all of your files being backed up.  You can see if the .tar is there by browsing to it, but don't try to open it while the backup is running.

That's my experience.  Thanks altech for the script!  It was still running when I left for work, so I'll post again if I notice any problems when I get home.  

Troy

---

### Post by altech6983 on 2009-03-13
Well I wish it would only do incremental (only the new stuff) backups after the first but unforuntaly I am way to much of a noob programmer to figure out how to do that. I wrote this script as kind of a failsafe as I am always fooling around inside of ubuntu and have had to reinstall twice, this way there is a full backup. 

Also, sorry for taking so long to reply.

The program always creates a file called backup-<CURRENTDATE>.tar.bz2 I could if you want write it so that you could put the file name in as an argument. Also the reason it take so long is 1) That is a lot of files for such a unoptimized process like this 2) It is taring it in bz2 format which is a high compression format and when I wrote the script my computer runs at 3.5 GHz quad core so I didn't really have a problem with that. I could also code in that option of changing compression format if you want/think would be useful.

---

