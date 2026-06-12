---
title: "Debugging Shell Script"
date: 2009-08-17
forum: New to Ubuntu
---

### Post by duiu on 2009-08-17
I'm completely new to shell scripting and I'm working on a script for cygwin that will ping the Ubuntu server 'mainhub' to see if its on, and if it is, run rsync. It also logs the date and time to a file, as well as the rsync output. However, I keep getting an error for Line 15 'unexpected token $\r' Line 15 is blank. I expect the error is somewhere else in my syntax. If someone could point me in the correct direction, I'd be extremely grateful.

```
#!/bin/bash
#
# Background rsync (backrsync)
#
# Checks to see if mainhub is on
# If mainhub is off, logs, then exits
# If mainhub is on, rsyncs then logs
# Notifies me once logfile reaches 1mb
#
# Exit statuses
#	1 - mainhub is not on
#	2 - log file hit 1MB, now on Desktop
ping mainhub -n 1
RESP='echo \$\?'

# Function to run rsync, then log it
function dosync
{
	echo 'date' >> /home/David/.rsync/backrsync.log
	rsync -qaxe ssh --stats --compress --recursive --times --delete --exclude-file=/home/David/rules.rsync "/cygdrive/c/Documents and Settings/David/My Documents/My Music/iTunes/iTunes Music" mainhub:/srv/SAMBA/FileServer/David/Music >> /home/David/.rsync/backrsync.log
	SIZE='echo 'ls /home/David/.rsync -lh | grep M''
	if [ -z $SIZE]
	then 
		exit 0
	else
		mv /home/David/.rsync/backrsync.log /cygdrive/c/Documents\ and\ Settings/David/Desktop/backrsync.full.log.
		exit 2
	fi
}

if [ $RESP ! -eq 0]
then
	echo 'date' >> /home/David/.rsync/backrsync.log && echo "No connection to mainhub" >> backrsync.log >> /home/David/.rsync/backrsync.log
	exit 1
else
	dorsync
fi

```

---

### Post by freebeer on 2009-08-17
I'm a scripting newbie, but my guess is a problem with line 14.

Your line 

```

RESP='echo \$\?'

```

should probably be

```

RESP=`echo \$\?`

```

I think you're supposed to use "backticks" (`) not single quotes (').

---

