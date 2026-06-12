---
title: "Backup to FTP"
date: 2009-01-29
forum: New to Ubuntu
---

### Post by ozPATT on 2009-01-29
Hi all, I am guessing this is possible, but not sure. I would like to create a script, which will copy specific files, and upload them to an ftp server, overwriting if newer. 

I would like the successful script to run automatically, either at a certain time of day, or when the computer is first switched on.

There would always be an internet connection, though when the computer is first switched on, it takes a little bit of time to connect, so probably the time option is better. 

Is this possible? If so, please could someone point me to a tutorial for it, or else explain how I can do it?

Thanks!

Patrick

---

### Post by Cypher on 2009-01-29
I don't think FTP is the right transport for what you are trying to do. FTP is an interactive program, so you'd have to make it non-interactive by using Expect or something. Additionally, FTP tends to overwrite files without care for remote files being newer or not.

To only get new content onto a remote location, Rsync is probably a better option.

---

### Post by ozPATT on 2009-01-29
hi cypher, i have a desktop which has ubuntu server edition on it, which is what im trying to get my files backed up onto. Can Rsync be run automatically? I would need to have Rsync on both computers wouldn't I? 

I'm certainly open to suggestions, the goal is to get a rolling weekly backup on the server box, so that I have my work and emails covered. 

Are there good tutorials for Rsync? just going to look into it now..

---

### Post by niteshifter on 2009-01-29
Hi,

If you have control of the server, then as Cypher indicated set up rsync on the server and have at it - rsync does what you want. The scripting job reduces to generating the file list for feeding to rsync.

OTOH if you can't install rsync on the server then yes, you can certainly script ftp. Google "ftp perl" for some ideas / scripts that do this. Checking out cpan.org would also be a good place to start. Your's is a common problem, not everyone has control of the server and ftp is the only way to move files.

---

### Post by NeuralEskimo on 2009-01-29
I disagree a bit. FTP can be scripted like you want; however, copying only the changes is better handled by a program like rsync. Here are a few options to consider:
1) use FTP to copy everything,
2) use SCP to copy everything using an encrypted connection, or
3) use rsync to copy only the changes.
By the way, rsync can use FTP or SSH (SFTP/SCP) to communicate with the remote server or rsync can communicate with a rsync daemon (daemon = server).

I suggest either SFTP/SCP or rsync (via SSH or an rsync daemon). IMHO, your first step should be to see if the server is running SSH and/or rsync. Your second step is to install rsync and write a script. I have a script I use which I can post if you are interested. Finally, the last step is to use cron to schedule the backup to run. 

Decide what you want to do about the protocol and then we can proceed from there...

---

### Post by ozPATT on 2009-01-29
hi, i have just had a look at [https://help.ubuntu.com/community/rsync](https://help.ubuntu.com/community/rsync) and tried the simple ssh backup it suggests, which seems to have done the job, so thats great news! I am still wondering though how I would set up a cron job to do this at say 4.45pm each day, and also I have 7 folders, named 1,2,3,4,5,6,7 so that I can upload to the relevant day number, giving me a weekly rolling backup. Can rsync be setup to do this do you know? 

Thanks

Patrick

---

### Post by ozPATT on 2009-01-29
hi neuraleskimo, i want to proceed with using rsync over ssh, as i think that this is exactly what i am looking for. i would definitely be interested in having a look at the script you use, as i don't really know anything about setting up cron jobs on linux, im quite a newbie when it comes to the technical side of things...

---

### Post by NeuralEskimo on 2009-01-29
> **ozPATT said:**
> ... im quite a newbie when it comes to the technical side of things...

No biggie. Everyone is a newbie at some point. ;)

To make everything work with cron, you will need to setup ssh to connect without a password (no one will be there to enter a password and there will be no prompt). I won't give you a detailed step-by-step, unless you run into trouble, but do the following:
1) create a password-less ssh key (Google if needed),
2) because this key has no password, defend it with your life, 
3) copy the public key to the remote server, specifically in the .ssh directory of the user your script will login as,
4) test it by typing the following at the commandline: "ssh user@server", if everything worked, you will not be prompted for a password

Now, we move to the rsync script. Here is a script that does a backup of my laptop when I connect to a specific network which contains a specific server. How connecting to a network kicks off this script is way too much detail and not relevant to your situation, so I'm going to skip it.

sync_helper
```
#!/bin/bash

sync_directories()
{
	SRC=$1	# source file or directory
	DST=$2	# destination file or directory
	echo "--- Syncing $SRC with $DST ---"
	rsync --progress --stats --compress --rsh=/usr/bin/ssh \
		--recursive --times --perms --links --delete \
		--exclude-from=$HOME/.backup-exclude --delete-excluded \
		"$SRC" "$DST"
	# --verbose  --stats 
	return 0
}

begin_critical_section()
{
	LOCKFILE=$1
	if ( set -o noclobber; echo "$$" > "$LOCKFILE") 2> /dev/null;
	then
		#echo "Entering critical section \"$LOCKFILE\""
		trap 'rm -f "$LOCKFILE"; exit $?' INT TERM EXIT
		return 0
	else
		echo "Error entering critical section named: $LOCKFILE"
		return 1
	fi
}

end_critical_section()
{
	LOCKFILE=$1
	#echo "Exiting critical section \"$LOCKFILE\""
	rm -f "$LOCKFILE"
	trap - INT TERM EXIT
	return 0
}

```

```
#!/bin/bash

#
# global variables
#
NETWORK="Some Network"
SERVER=user@server:/home/user/path
LOCKFILE="/tmp/sync_home_directory.$USER"

things2sync()
{
    date

    #    Source File/Directory  Destination File/Directory
    sync_directories "$HOME/$USER" "$SERVER/Backups/$USER"
}

#
# main program
#
source sync_helper

test_network "$NETWORK" && begin_critical_section "$LOCKFILE" && things2sync
end_critical_section $LOCKFILE

exit 0

```

This script may be a bit complex, but focus on the rsync line, which is 
```
	rsync --progress --stats --compress --rsh=/usr/bin/ssh \
		--recursive --times --perms --links --delete \
		--exclude-from=$HOME/.backup-exclude --delete-excluded \
		"$SRC" "$DST"

```

This should do everything you want. Replace $SRC with the source directory path, like /home/user, and replace $DST with the destination, like user@server:/home/user/path.

Also, this script spits out a bunch of info to the screen. If you want it to be quite, take out "--progress --stats". If you leave these things in, cron will email you the output, assuming you have suitably configured your computer. 

Oh, and the command above also consults a file which contains a list of files/directories which you DO NOT want backed up. For example, there is a lot of cached data, such as from firefox, that I don't care to backup and only slows the backup. This file is called .backup-exclude and should be placed in your HOME directory.

You don't need anything quite as fancy as my scripts, you should be able to do the following:

```
#!/bin/bash
	
SRC=/home/$USER
DST=user@server:/path/to/backups/$USER

    rsync --progress --stats --compress --rsh=/usr/bin/ssh \
          --recursive --times --perms --links --delete \
	  --exclude-from=$HOME/.backup-exclude --delete-excluded \
	  "$SRC" "$DST"

```

Finally, you will need to setup cron. From the commandline, type:
"sudo crontab -e -u user"
where user is the username the script will run as.
The format of the crontab file is simple, but odd for a beginner.
Type the following at the end of the file:
"45  16  *   *   *  /path/to/your/rsync_script"
Save changes and exit. You should have a functional backup.

As far as your desire to have directories (numbered 1 to 7), I would probably handle that a little different. If you edit the script above to change the destination directory based on the day of the week, which would be straight forward, you would have a small problem. Consider the first seven days. Day 1 will require a full copy to directory 1 because the directory is empty, Day 2 will require a full copy because directory 2 is empty, and so on. This is not too big of a deal, but it wastes the power of incremental copies that you get with rsync. Now consider the 8th day. Instead of an incremental copy against directory 7, you are doing an incremental copy against directory 1, which is seven days old! Again, this is not a problem, but it wastes the power of incremental copy. Instead, you might want to rotate the directories. One way you can do this is by editing your script to look something like the following:

```
#!/bin/bash

# rotate the backups

ssh -n user@server "rm -rf /path/to/backups/7"
scp user@server:/path/to/backups/6 user@server:/path/to/backups/7
scp user@server:/path/to/backups/5 user@server:/path/to/backups/6
     ....
scp user@server:/path/to/backups/1 user@server:/path/to/backups/2


# do the backups

SRC=/home/$USER
DST=user@server:/path/to/backups/$USER/1

    rsync --progress --stats --compress --rsh=/usr/bin/ssh \
          --recursive --times --perms --links --delete \
	  --exclude-from=$HOME/.backup-exclude --delete-excluded \
	  "$SRC" "$DST"
``` 

Of course, this is a very inefficient way to rotate the directories, but it will get you started. Besides, I am running out of energy and I suspect you are tired of reading.

[COLOR="Red"]EDIT: I forgot to offer a hint on a more efficient on a better way to rotate the directories. Can you think of a way to use rsync from the server side to do the rotate in a more efficient manner?[/COLOR] 

Anyway, I hit you with a lot of info. I hope this helps. Let me know if you have any questions.

---

### Post by ozPATT on 2009-01-29
hey there, that is so cool, thanks for taking the time to go through all that, I will read it in depth and give it a try this evening, hopefully I don't run into too much trouble!

---

### Post by shane2peru on 2009-02-16
> **NeuralEskimo said:**
> I disagree a bit. FTP can be scripted like you want; however, copying only the changes is better handled by a program like rsync. Here are a few options to consider:
1) use FTP to copy everything,
2) use SCP to copy everything using an encrypted connection, or
3) use rsync to copy only the changes.
By the way, rsync can use FTP or SSH (SFTP/SCP) to communicate with the remote server or rsync can communicate with a rsync daemon (daemon = server).

I suggest either SFTP/SCP or rsync (via SSH or an rsync daemon). IMHO, your first step should be to see if the server is running SSH and/or rsync. Your second step is to install rsync and write a script. I have a script I use which I can post if you are interested. Finally, the last step is to use cron to schedule the backup to run. 

Decide what you want to do about the protocol and then we can proceed from there...

hey can you expand on using rsync with FTP or a link that shows how to do that?  I'm really interested in running that!  My server doesn't accept ssh connections, so I'm very much limited to using FTP, however I only want to upload the updated stuff, not everything.  I have used rsync quite a bit in the past but was not aware that it works with FTP, please do share!

Shane

---

### Post by HermanAB on 2009-02-16
I agree that rsync usually works better, but to answer the original question about using a FTP script, see this: [http://aeronetworks.ca/windows-backup.html](http://aeronetworks.ca/windows-backup.html)

Cheers,

Herman

---

### Post by shane2peru on 2009-02-16
> **HermanAB said:**
> I agree that rsync usually works better, but to answer the original question about using a FTP script, see this: [http://aeronetworks.ca/windows-backup.html](http://aeronetworks.ca/windows-backup.html)

Cheers,

Herman

That how to is for windows.  Unless I missed something, I thought we were trying to script out this for Linux. 

Shane

---

### Post by shane2peru on 2009-02-16
I found this:  [http://sourceforge.net/news/?group_id=38241](http://sourceforge.net/news/?group_id=38241)   Which may be relevant, it is new ftpsync.  Seems to do what we are looking for in ftp format.

Scratch the above, **sitecopy** is what you want to use!  It is in the repos and seems to use (mis-use) ftp to backup files if that is what you are looking to do. :)

Shane

---

### Post by shane2peru on 2009-02-19
Ok, sitecopy may be good for trying to upload normal stuff, but I don't think it is cut out for backing up a lot of files.  I have had a bit of difficulty getting it to work consistently.  If anyone has any other ideas I'm open for suggestions.

Shane

---

### Post by shane2peru on 2009-05-02
Found a way to do this.  You need to install mirrordir with
```

sudo apt-get install mirrordir

```
Then create this file
```

gedit ~/.netrc

```
if it exists just tack this info on to the end, if not here is an example file:
[PHP]
# FTP access to my Web host
machine ftp.your.domain.com 
	login username 
	password your_password
[/PHP]

I then wrote up this little script:
[PHP]
#!/bin/bash
#This will copy all my pictures to the offline web site.
copydir --verbose --netrc /home/username/directory/ ftp://username@ftp.your.domain.com/directory/
[/PHP]

You can just copy that line with copydir and modify and run it on the command line to get it to work.  This seems to do what we have wanted.  Hope this helps!

man mirrordir will help you understand all the options, copydir is part of mirrordir, mirrordir will actually remove files too, it has a very similar function to rsync, but truly works through ftp.

Shane

**EDIT:** Oct 14, 2009 - fixed package name error.

---

