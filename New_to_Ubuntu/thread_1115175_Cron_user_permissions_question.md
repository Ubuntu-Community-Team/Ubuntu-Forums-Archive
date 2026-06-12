---
title: "Cron user permissions question"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by mashedbear on 2009-04-03
Hi - I want to use cron to run an rsync command everyday at a set time to backup /home to a second disk.

I can run this at the command line using sudo and everything works fine:
```
sudo rsync -av --logfile=/var/log/$(date +%Y%m%d)rsync-backupHOME.log --ignore-errors --progress --delete /home /mnt/disk2/gandalf_home_backup
```

To run this from the cron do I simply add this to the root cron - which i think would be:
```
sudo crontab -u root -e
```



Or is it better to create a bash script and set cron to execute the script. In which case if I am using sudo in the script - how would I configure cron to avoid needing to put a password in each time cron runs the script?

Thanks for any help

---

### Post by kyalee on 2009-04-03
You might find this post helpful: 

[http://ubuntuforums.org/showthread.php?t=786410](http://ubuntuforums.org/showthread.php?t=786410)

---

### Post by mali2297 on 2009-04-03
> **mashedbear said:**
> Or is it better to create a bash script and set cron to execute the script. In which case if I am using sudo in the script - how would I configure cron to avoid needing to put a password in each time cron runs the script?

If you use *sudo crontab -e* then you will edit root's crontab. Any script in that crontab will be executed with super-user privileges. Thus, you don't have to use sudo in your script.

---

### Post by mashedbear on 2009-04-04
Thanks kyalee and Martin.

Have got this to work. The root crontab is now

```
# m h  dom mon dow   command
0 22 * * * cd /home/paul/bash; sh rootCronBackupHOME.sh

```

so I back up /home at 10pm each night.

I had to do some looking to work out how to get the cron to run the command from /home/paul/bash. Not sure if I have done this the 'best' way. When I was reading about this I saw that ```
 ./rootCronBackupHOME.sh 
``` would be the 'usual' way to run a script. When I do this I get permission denied. Can you point me in the right direction to get an answer to this one?

Thanks again

---

### Post by MrWES on 2009-04-04
> **mashedbear said:**
> Thanks kyalee and Martin.

Have got this to work. The root crontab is now

```
# m h  dom mon dow   command
0 22 * * * cd /home/paul/bash; sh rootCronBackupHOME.sh

```

so I back up /home at 10pm each night.

I had to do some looking to work out how to get the cron to run the command from /home/paul/bash. Not sure if I have done this the 'best' way. When I was reading about this I saw that ```
 ./rootCronBackupHOME.sh 
``` would be the 'usual' way to run a script. When I do this I get permission denied. Can you point me in the right direction to get an answer to this one?

Thanks again

Another way to go about it, is to place your executable script, owned by root in /etc/cron.daily

Any script that is in the /etc/cron.daily directory will run according to the settings in the system wide /etc/crontab .

You can deploy this methodology for hourly, daily, weekly and monthly tasks that you run from scripts. For example; I have my cron.daily set to run at:

```
30 10	* * *	root	test -x /usr/sbin/anacron || ( cd / && run-parts --report /etc/cron.daily )

```

That's 10:30am everyday, it'll run any scripts in /etc/cron.daily -- which I have a transmission torrent blocklist update script that runs. 

Works very well, and you can edit the /etc/crontab to change the run time to suit your needs.

Bill

---

### Post by mali2297 on 2009-04-04
> **mashedbear said:**
> Thanks kyalee and Martin.

Have got this to work. The root crontab is now

```
# m h  dom mon dow   command
0 22 * * * cd /home/paul/bash; sh rootCronBackupHOME.sh

```

so I back up /home at 10pm each night.

I had to do some looking to work out how to get the cron to run the command from /home/paul/bash. Not sure if I have done this the 'best' way. When I was reading about this I saw that ```
 ./rootCronBackupHOME.sh 
``` would be the 'usual' way to run a script. When I do this I get permission denied. Can you point me in the right direction to get an answer to this one?

Thanks again

Make the script executable with
```

chmod +x /home/paul/bash/rootCronBackupHOME.sh

```
Then, in the crontab, just put
```

0 22 * * * /home/paul/bash/rootCronBackupHOME.sh

```

---

### Post by ftabor on 2009-04-04
I've been following along with this, I'm trying to get cron to update and upgrade at 1 AM local here once a week.

I have tried this both with terminal and gnome-shedule and using gnome-schedule, I can manually run the entry and it will work, however when cron tries to run it, it fails.  Syslog has this entry;
Apr  4 16:20:01 SeniorChief CRON[13803]: Authentication failure

Here's what I have.  I have this script in root, and it's executable;

```
#!/bin/bash
apt-get update && apt-get upgrade --yes
```

Using terminal, I enter;
```
sudo crontab -u root -e
```

and in nano I have;

```
0 1 * * 7 /root/update-shell.sh # JOB_ID_3
20 16 * * 6 /root/update-shell.sh
```

The first line is the recurring job and the second line is the one I wrote to try it out.  The second line is the one that gave the Auth failure. (The first job was scheduled for 1 AM this morning, but it failed also, so I've rescheduled.)

Any ideas why it has an Authentication Failure?

The auth.log entry is;
Apr  4 16:20:01 SeniorChief CRON[13803]: pam_unix(cron:account): account root has expired (account expired)

---

### Post by mali2297 on 2009-04-04
> **ftabor said:**
> 
Any ideas why it has an Authentication Failure?

The auth.log entry is;
Apr  4 16:20:01 SeniorChief CRON[13803]: pam_unix(cron:account): account root has expired (account expired)

Yes, the root account is disabled in Ubuntu. Just use
```

sudo crontab -e

```
This will edit the *system* crontab file as it seems (not root's as I said earlier).

---

### Post by ftabor on 2009-04-04
> **mali2297 said:**
> Yes, the root account is disabled in Ubuntu. Just use
```

sudo crontab -e

```
This will edit the *system* crontab file as it seems (not root's as I said earlier).

I've got other problems I think, although I'll try that and see, I can't log into root, and I cant' change the passwd in root,  I had set one, because VMServer requires a root password to admin the serve in the browser.

I think I'm going to have to reinstall to get this and several other things fixed.  

I do appreciate the answer.  Thanks.

---

### Post by ftabor on 2009-04-05
> **ftabor said:**
> I've got other problems I think, although I'll try that and see, I can't log into root, and I cant' change the passwd in root,  I had set one, because VMServer requires a root password to admin the serve in the browser.

I think I'm going to have to reinstall to get this and several other things fixed.  

I do appreciate the answer.  Thanks.

I found my solution in a bug report at Launchpad.  It has to do with a bug in passwd -l --lock.  After I applied the fix there, I stopped getting the expired root sessions and auth failures on cron jobs.

---

### Post by mashedbear on 2009-04-18
> **mali2297 said:**
> Make the script executable with
```

chmod +x /home/paul/bash/rootCronBackupHOME.sh

```
Then, in the crontab, just put
```

0 22 * * * /home/paul/bash/rootCronBackupHOME.sh

```
Thanks Martin. Problem solved. Thanks again for your help.

---

