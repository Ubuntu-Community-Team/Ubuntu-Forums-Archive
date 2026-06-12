---
title: "Can't run rsync bash script with cron"
date: 2009-07-20
forum: New to Ubuntu
---

### Post by bertwagner on 2009-07-20
I wrote the following backup script:

```

#!/bin/bash
rsync -rtpogv -progress --delete --rsh='ssh -p 1338' bertwagner@xx.xx.xx.xxx:/Users/bertwagner/Pictures/ /home/bert/backup/Pictures/

```

I saved this file as 'homebackup', placed it in /usr/local/bin, gave it execute permissions.  If I run 'homebackup' in terminal it executes the script like I want it to and there are no problems.

I tried setting up the following cron job using 'sudo crontab -e':
```
* * * * * /usr/local/bin/homebackup
```

(I have it running every minute just for testing purposes now)
Although the script worked fine when I ran it from terminal, it for some reason does not work with cron.  I added a line to the script 'homebackup' both before and after the rsync command in the form of:
```
echo "TEST $(date)" >> /home/bert/backup/backup.log
```
in order to check if cron was actually working.  

I came to the conclusion that cron is working because every minute 'homebackup' is writing to the log file both before and after the rsync command in the script, however the rsync command is not being executed.  Can anyone help me figure out what I'm doing wrong?  Thanks!

---

### Post by XCan on 2009-07-21
> **bertwagner said:**
> I wrote the following backup script:

```

#!/bin/bash
rsync -rtpogv -progress --delete --rsh='ssh -p 1338' bertwagner@xx.xx.xx.xxx:/Users/bertwagner/Pictures/ /home/bert/backup/Pictures/

```


So, it appears that you are connecting via ssh, have you checked so that it does not get stuck on the ssh authentication? I don't see you specifying your ssh key file with the -i flag.

Btw, why don't you use the -a flag instead of the -rtpog flag?

---

### Post by Paddy Landau on 2009-07-21
Also, you can get the program to redirect the output -- including any error messages -- to a file. Try adding it to the end of the command, like this:
```
rsync -rtpogv -progress --delete --rsh='ssh -p 1338' bertwagner@xx.xx.xx.xxx:/Users/bertwagner/Pictures/ /home/bert/backup/Pictures/ **>>/home/bert/backup/backup.log 2>&1**
```That way, you'll see if there are any errors (such as the SSH that XCan mentioned).

---

### Post by bertwagner on 2009-07-23
Thank you for your help so far XCan and Paddy Landau.  Using your suggestions I've made some progress figuring out what's going on but the script still isn't working like it should.  My new rsync command is as follows:

```

rsync -avvv -progress --delete --rsh='ssh -p 1338 -i /home/bert/.ssh/id_dsa' bertwagner@xx.xx.xx.xxx:/Users/bertwagner/Pictures/ /home/bert/backup/Pictures/ >>/home/bert/backup/backup.log 2>&1

```

Running this command in terminal works fine; my SSH key works and I am able to backup across the network without any manual input from me.  However, when I put this command in my script and run it via cron, the following error occurs:

```

opening connection using: ssh -p 1338 -i /home/bert/.ssh/id_dsa -l bertwagner xx.xx.xx.xxx rsync --server --sender -vvvogtpre.iLs . /Users/bertwagner/Pictures/
Host key verification failed.
rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(600) [receiver=3.0.5]
_exit_cleanup(code=12, file=io.c, line=600): about to call exit(255)

```

I interpret this as meaning there is a problem with authentication, but I'm stumped because the command works fine in terminal on its own and only creates errors when ran from within the script.  Any additional help is appreciated.

---

### Post by Paddy Landau on 2009-07-23
When you run rsync from the terminal, does it prompt you for a password? Where is the SSH command getting its password from?

EDIT: Doh! Sorry, it's getting the password from /home/bert/.ssh/id_dsa

Does cron have permission to access that file, I wonder?

---

### Post by bertwagner on 2009-07-23
> **Paddy Landau said:**
> When you run rsync from the terminal, does it prompt you for a password? Where is the SSH command getting its password from?

EDIT: Doh! Sorry, it's getting the password from /home/bert/.ssh/id_dsa

Does cron have permission to access that file, I wonder?


I switched from using sudo crontab to just using my user's crontab.  I set 777 permissions to the id_dsa file and this is the error I get now:
```
opening connection using: ssh -p 1338 -i /home/bert/.ssh/id_dsa -l bertwagner xx.xx.xx.xxx rsync --server --sender -vvvogtpre.iLs . /Users/bertwagner/Pictures/ 
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

@         WARNING: UNPROTECTED PRIVATE KEY FILE!          @

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@

Permissions 0777 for '/home/bert/.ssh/id_dsa' are too open.

It is recommended that your private key files are NOT accessible by others.

This private key will be ignored.

bad permissions: ignore key: /home/bert/.ssh/id_dsa

Permission denied, please try again.

Permission denied, please try again.

Received disconnect from xx.xx.xx.xxx: 2: Too many authentication failures for bertwagner

rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(600) [receiver=3.0.5]
_exit_cleanup(code=12, file=io.c, line=600): about to call exit(255)
```

If I play around with permissions I can't seem to get any combination that will allow the command to run - I either give id_dsa too much access and receive the error above or I restrict access to only the user and receive:
```
opening connection using: ssh -p 1338 -i /home/bert/.ssh/id_dsa -l bertwagner xx.xx.xx.xxx rsync --server --sender -vvvogtpre.iLs . /Users/bertwagner/Pictures/ 
Permission denied, please try again.

Permission denied, please try again.

Received disconnect from xx.xx.xx.xxx: 2: Too many authentication failures for bertwagner

rsync: connection unexpectedly closed (0 bytes received so far) [receiver]
rsync error: unexplained error (code 255) at io.c(600) [receiver=3.0.5]
_exit_cleanup(code=12, file=io.c, line=600): about to call exit(255)
```

---

### Post by Paddy Landau on 2009-07-23
I'm no expert in this.

Permissions for my .ssh are drwx------. The permissions for files within it are -rw-r--r--.

Try setting those permissions and try again.

If that still doesn't work (and it probably won't), perhaps some more knowledgeable person can tell you how to get your cron job to run with the right permissions.

---

### Post by neilevan814 on 2009-09-27
I am struggling with this right now too.  I have my rsync set up through rsnapshot and keychain.  Upon researching the rsync 255 error, I found this:

It looks like SSH auth is failing as you thought.

Bash will not use your '.bash_profile' for non-interactive shells by
default. There are easy ways around this, but I would suggest that you
rather embed the commands into your script or use a helper like
'keychain' and then source it's file from your script.

Read the 'INVOCATION' section of bash(1) for more details.

Okay...a little more research and I will know for sure in about 1/2 hour if it really works but:  in rsnapshot.conf under cmd_preexec instead of writing the source /root/.keychain/someone@somewhere.com-sh right there.  You need to point to a shell script with that command written in it.
I did a shell script called keychain.sh 
#!/bin/bash
source /root/.keychain/someone@somewhere.com-sh

and under cmd_preexec /usr/local/bin/keychain.sh

That didn't work you need to follow the instructions here:
# ~/.bashrc: executed by bash(1) for non-login shells.
# see /usr/share/doc/bash/examples/startup-files (in the package bash-doc)
# for examples

Does Anyone Know how to invoke bash(1) for non interactive shell scripting?

---

### Post by wanye on 2009-11-16
I'm getting the same problem. using 9.10 32 bit. googling came up with the "Read the 'INVOCATION' section of bash(1) for more details" stuff, and all i could find that helped was to set the BASH_ENV variable in my crontab. which didnt help...


anyone?

------

me@babydweezil:~$ crontab -l
BASH_ENV=/home/me/.bashrc
# m h  dom mon dow   command
*/2 * * * * /home/me/watchcopy.sh
me@babydweezil:~$


watchcopy.sh:
#!/bin/sh
rsync -ave ssh --delete --include "*.filetype1" --include "*.filetype2" --exclude "*.*" --log-file=/home/me/watchrsync.log /media/1tb/downloads/chromedownloads/ user@externalbox:/data/me/watch


watchrsync.log:
2009/11/15 22:36:04 [6155] rsync: connection unexpectedly closed (0 bytes received so far) [sender]
2009/11/15 22:36:04 [6155] rsync error: unexplained error (code 255) at io.c(600) [sender=3.0.6]
2009/11/15 22:38:04 [6166] rsync: connection unexpectedly closed (0 bytes received so far) [sender]
2009/11/15 22:38:04 [6166] rsync error: unexplained error (code 255) at io.c(600) [sender=3.0.6]
and so on..... (repeated every 2 mins)

---

### Post by M20554443 on 2009-12-07
Hi, this is probably because you are using ssh agent (having protected your ssh key with a password). You may want to make sure you set the environment variable SSH_AUTH_LOCK when starting the script via cron. For me this solution works fine (thanks to the author):

[http://www.codealpha.net/163/cron-ssh-and-rsync-and-key-with-passphrase-ubuntu/](http://www.codealpha.net/163/cron-ssh-and-rsync-and-key-with-passphrase-ubuntu/)

Set it via cron ...

```

# m h  dom mon dow   command
00 04 * * *     SSH_AUTH_SOCK=$(find /tmp/keyring*/ -perm 0755 -type s -user matthias -group matthias -name 'socket.ssh' | head -1) /home/matthias/bin/backup.sh

```... or within your backup script ...

```

#!/bin/sh

export SSH_AUTH_SOCK=$(find /tmp/keyring*/ -perm 0755 -type s -user matthias -group matthias -name 'socket.ssh' | head -1)

rsync -av --delete-after --log-file=/home/matthias/.rsync.log \
        ~/dir1 \
        ~/dir2 \
        ~/dir3 \
        matthias@somewhere.com:backup/

```

---

