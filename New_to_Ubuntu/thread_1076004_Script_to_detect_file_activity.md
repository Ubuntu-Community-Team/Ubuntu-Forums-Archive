---
title: "Script to detect file activity"
date: 2009-02-20
forum: New to Ubuntu
---

### Post by bpowell2005 on 2009-02-20
Not sure which forum I should post this in, but thought I'd start here.

I am backing up files from a laptop to a Mythbuntu box on the local network. 

I'd like a script to run on the Mythbuntu box that would monitor the backup directory, and let me know (via email) if no backup files have arrived in say...5 days.

I'm open to running an SMTP server on the Mythbuntu box to support the email if needed...but don't know anything about scripting or how to monitor for file activity based on date.

Any ideas?

---

### Post by Hospadar on 2009-02-20
First off, why might there be doubt as to whether or not files are actually getting backed up?
I think you'd be better off recording the output of whatever you are using to back up the files (rsync probably?) and just checking every now and then to make sure there are no errors.

That said, you could certainly check the timestamps of files in a bash script and see how old they are, although I think it's kind of the hard way to do do things.
consider a script like this:```
#!/bin/bash

#list the files and loop through them all
ls -l | while read LINE
do
#get the date from the ls line
DATE=`echo $LINE | awk '{print $6}'`
#get the day of month out of the date
FDOM=`echo $DATE | awk -F '-' '{print $3}'`
#get the month
FMON=`echo $DATE | awk -F '-' '{print $3}'`
#you could do all sorts of checking here to see if the date is 5 or more days ago, then send an email or whatever.
done

```
Of course if you go this route, you'll need to be familiar with bash scripting and awk and some basic arithmetic in bash

Also look into the "date" command.

I think all this scripting is a worthwhile thing to learn, I just think maybe for your application it might not make the most sense.

---

### Post by bpowell2005 on 2009-02-21
> **Hospadar said:**
> First off, why might there be doubt as to whether or not files are actually getting backed up?
I think you'd be better off recording the output of whatever you are using to back up the files (rsync probably?) and just checking every now and then to make sure there are no errors.

That said, you could certainly check the timestamps of files in a bash script and see how old they are, although I think it's kind of the hard way to do do things.
consider a script like this:```
#!/bin/bash

#list the files and loop through them all
ls -l | while read LINE
do
#get the date from the ls line
DATE=`echo $LINE | awk '{print $6}'`
#get the day of month out of the date
FDOM=`echo $DATE | awk -F '-' '{print $3}'`
#get the month
FMON=`echo $DATE | awk -F '-' '{print $3}'`
#you could do all sorts of checking here to see if the date is 5 or more days ago, then send an email or whatever.
done

```
Of course if you go this route, you'll need to be familiar with bash scripting and awk and some basic arithmetic in bash

Also look into the "date" command.

I think all this scripting is a worthwhile thing to learn, I just think maybe for your application it might not make the most sense.


Thanks for the suggestions! I'd like to play around with scripting, this seems like a good project to start learning on. 

The idea is to have an automated message sent to me if the backup process is failing...I might expand this application to monitor other computers as well. I guess I could check the output of my backup utility (simple backup) but that relies on manual intervention; I'd like it automated if possible. Also, I'd like the checking done on the receiving side. 

Thanks again for the script suggestions; I will do some playing this weekend!

---

