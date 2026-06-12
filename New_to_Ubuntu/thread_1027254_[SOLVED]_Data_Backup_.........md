---
title: "[SOLVED] Data Backup ........"
date: 2009-01-01
forum: New to Ubuntu
---

### Post by expatCM on 2009-01-01
My server just crashed again and for the second time in the same number of weeks I managed to save my neck with minimal effort and a lot of uncertainty during the process.  The users were not exactly impressed but they did not hear the full story (best approach).  Since there is no data backup it is a bit like playing with fire.

So it is now a New Years resolution to do something for data backup.  What I am planning to do is to back up data to the individual client machines.  Nice and easy.  However there are a couple of areas where I am looking for ideas.

First is which backup solution to use.  I want to keep a backup of each users data (only data and files rather than an image) on each users machine but to minimize network traffic I only want to refresh the back up where files that have changed.  I also want to fully automate this.  But which package, there is sbackup, rsync, flyback and no doubt lots of others …......    It looks like some packages make it less easy to restore individual files or directories ..  but that is based on my looking at the solutions rather than testing them.  Any suggestions?

Second ….  the automation.  Most of these packages seem to use a scheduled / cron event to work.  I have unpredictable users.  If  I schedule to backup at 11:00 it is reasonably certain that they will not be on-line and therefore miss the backup.  If I schedule to run as Ubuntu is loaded I am not sure that this will be such a good idea since the network traffic is likely to slow down the machine performance just when they want to use it.  So how to you schedule a back up to run each day at say 30 minutes after first logon?

---

### Post by blueridgedog on 2009-01-01
What OS are your workstations?

If I read you right, you want to backup the server to the workstations, using extra disk space on the workstations as storage for backups of the server.

Unison comes to mind.

However, given a 1T external USB drive is now $100, I think you are about to start a task that could be accomplished cheaper (counting man hours) and better via another approach.

---

### Post by superprash2003 on 2009-01-01
rsync is not a bad option
> So how to you schedule a back up to run each day at say 30 minutes after first logon?
you could do some programming for this.. maybe launch a java program at startup..put it to sleep for 30 min.. and then tell it to launch rsync..

---

### Post by expatCM on 2009-01-01
blueridgedog -- the clients run Ubuntu 8.10, the server 7.10 (upgrade when 9.04 is out).

I had forgotten that Unison exists.  I remember trying it in the days I dual booted (long time back) but if I recall there was a problem for me at that time since Unison did not accept backing up from ntfs to ext3.  Obviously this is not an issue now but I overlooked Unison ....

Using an external hard drive.  Well yes, that is not a bad idea in that it gets the job done but I have to then remember to do it which is a big weakness and also I have to buy a drive.  What I know is that the client machines all have lots of unused storage, the o/s takes little space which leaves lots of unused space so backing up the data to the client machine may be an efficient use of that space.  Perhaps I should consider also saving the data on the local machines and backing up to the server since if the server were to go down again big time then it is easy to change the network to get the clients  working quickly.


superprash2003 -- do you know of any program that exists in the repositories that does this since I am in no position to write a program..?

---

### Post by hyper_ch on 2009-01-02
if all are linux, then use rsync :)

---

### Post by expatCM on 2009-01-02
rsync sounds to be interesting from the description on a couple of sites.  I will go digging to find a tutorial .....

I see that a new release was issued on December 28th ....

---

### Post by hyper_ch on 2009-01-02
rsync is simple to use. basic syntax is:

rsync OPTIONS FROM TO

to auto-sync you will need to exchange ssh keys and then you could use:

```

rsync  -avzp -e ssh /home/user remote_user@remote_host:/backup/user/

```

---

### Post by expatCM on 2009-01-02
I have been looking at the man pages.  There is such a lot there it is almost terrifying.  Good to receive your short to the point summary though, thank you.  There appear to be a couple of good pages found though google, many links point here (but there are other pages)
[http://ubuntuforums.org/showthread.php?t=15082](http://ubuntuforums.org/showthread.php?t=15082)

Thinking about this I am starting to get firmly out of depth.  Consider this ....  I run rsync from the server, let us suppose that I keep the live data on the clients and the backup on the server...  that is easy.

So all I would need do is add the IP of the client to your code to make it certain and repeat for each client to be backed up.

But my confusion comes with how to automate this.  What I would like to do is to have rsync run say 10 minutes after a user has logged in.  I cannot use cron since that requires a specific time to be stated and if you miss the time the command does not run.

Is there a trusted program that automates events in this manner?

---

### Post by mapes12 on 2009-01-02
> **expatCM said:**
> rsync sounds to be interesting from the description on a couple of sites.  I will go digging to find a tutorial .....

I see that a new release was issued on December 28th ....[Grsync]("http://www.opbyte.it/grsync/") adds a GUI to it. It can be installed via Package Manager. If memory serves my right you can also use it over ssh.

---

### Post by blueridgedog on 2009-01-02
> **expatCM said:**
> But my confusion comes with how to automate this.  What I would like to do is to have rsync run say 10 minutes after a user has logged in.  I cannot use cron since that requires a specific time to be stated and if you miss the time the command does not run.

Is there a trusted program that automates events in this manner?

I assume that the clients currently keep their data on the server and that the server has some other services running that give it a reason to exist.  Typically data is stored on a server because it has redundant disks and a backup mechanism so data is "safer" there than on a workstation.

If your server is not on server grade hardware, then concentrating all of your eggs in that basket actually increases your chance of failure versus leaving all data on the workstations (as you have learned).

If you are not interested in getting more hardware resources for the server, then you could flip the equasion around, as you have suggested, and keep the data on the workstation and use the server as a backup.  I would use eitehr rsync or tar with a simple command in the users' .bashrc file.  When the log in, the command will backup their home directory to the server.

If they have a mounted share of some sort (NFS or samba) from the server local, then you can tar and zip to that point.  If not, then rsync would be just a command away.

I can help with the syntax if you tell me more about your structure and now the workstations see the server from a mount point stand.

---

### Post by k_aneda on 2009-01-02
Question's a bit vague as there's lots of directions you can go, here's off the top of my head:

_**Option one:**_
If clients are Windows-based but server is windows OR linux, you could opt for this strategy:

1) Use Active Directory to redirect user Documents folder (or create a mapped drive on file server) where users *must* store documents - this drive would be on file server

2) Perform either/or file-level and image-level backups of the file server on a scheduled basis

3) For even faster recovery (or real-time protection of user data) - look at file-level replication to a DR server either via commerical or free product (r1soft CDP, robocopy, rsync, CommVault CDR, etc etc.)


_**Option two:**_
Failing that, if you had to perform backups from the workstations where access would be hard, I would have a rsync job (or robocopy for Vista clients, can be downloaded for XP) so that when users login/logout it quickly copies any changed files only (not the entire lot) back to the file server.


That said, I do not like hacked approaches for retaining user data - especially when it's the CEOs.   You need an accepted/management-backed approach where you centrally store the data - get it off the workstations.

Or at least tell your users, if it's not on their "shared drive", then it won't be protected.. works for most of my clients and other IT firms..

---

### Post by expatCM on 2009-01-02
Blueridgedog, thank you for your response.

The server was set up originally as a learning experience …  never done it before so I wanted to find out what it was all about.  It is not possible to buy server grade quality hardware here unless you place a special order and pay plenty.  So I narrowed down on Gigabyte for the motherboard which seemed to be the best option in the market (better than Asus which is 95% of the market here).  I put on a decent power supply and Seagate drives.  

The power supply blew some time ago and messed things up a bit, took out a nic but fsck fortunately sorted out the boot problems that appeared.  Not sure what caused the second failure, still got  to look at that carefully,  but fsck also fixed that....  eventually.

There are 4 clients at present. All Ubuntu 8.10.  The server (7.10) holds a music collection and some movies as well as the data of one user.  I will add another client shortly which will be for playing movies and music.  I will keep most of the movies locally on that machine.  Of  the other users, I keep my data on my machine at present, my children have minimal data which seems to get backed up to a gmail account or forgotten as homework assignments are presented.

Yes, it is a mess.   My wife is the user with live data on the server.  It is done this way since she has a great aptitude for crashing her machine.  No idea why but if any machine is not working in part for any reason it is hers.

Movies / music and photographs go out as nfs shares to all.  My wife also gets her data by nfs but only to her.

The use of the server will change a bit when I build it again.  At present apart from file storage it runs squid (in an attempt to help our bad Internet connection), shares the printers, runs the firewall and simplifies updates.  Two nics, one to the router and one to the hub.

When it is rebuilt (something like May or June) I will look to getting squid set up to more efficiently save bandwidth, work out how to manage podcasts on the server and figure out how to set up a raid 5.  Perhaps  more experiments with hosting a local only cms but who knows.  I will also do something about keeping an updated image of the server so that if that goes crash again and I cannot fix it then at least there will be something to restore.

I know I have to do something sensible about this situation.  I note your comments about the probability that the server could go down again and do not disagree.  The best strategy may well be to keep all live data on the client machines and put a backup on the server on a separate drive which is possible.  Doing it automatically is the key, I know that my wife would never do it manually.  

You mention adding a simple command in the users' .bashrc file.  I just had a look at the file and it does not look very friendly.  Could you please tell me what you have in mind?

---

### Post by blueridgedog on 2009-01-02
> **expatCM said:**
> Blueridgedog, thank you for your response.


You mention adding a simple command in the users' .bashrc file.  I just had a look at the file and it does not look very friendly.  Could you please tell me what you have in mind?

If you know DOS, then think of each users' .bashrc as their own autoexec.bat.  You can place commands at the end of the file that you want to run at login.  For example, to test how it might work, log in to a workstation and edit your .bashrc with:

```
gedit .bashrc
```

As a test, put a line at the end to run a program such as:

```
xcalc
```

Or, relative to your example of a back, assume you have files in /home that you want to backup to the server.  Though I don't know, lets assume the server is running samba as a file sharing tool and you have a share on the server called backup.  So, the .barshrc could include the lines:
```

smbmount //server/backup /backup -o username=user,password=pass,uid=500,gid=500
tar cvfz /backup/mybackup.tgz /home
```

As an aside, I recommend you debug and develop your backup process from the terminal prior to trying to automate it via an entry into .bashrc.  The above example could just as easily be done with rsync.

---

### Post by handydan918 on 2009-01-02
> **expatCM said:**
> I have been looking at the man pages.  There is such a lot there it is almost terrifying.  Good to receive your short to the point summary though, thank you.  There appear to be a couple of good pages found though google, many links point here (but there are other pages)
[http://ubuntuforums.org/showthread.php?t=15082](http://ubuntuforums.org/showthread.php?t=15082)

Thinking about this I am starting to get firmly out of depth.  Consider this ....  I run rsync from the server, let us suppose that I keep the live data on the clients and the backup on the server...  that is easy.

So all I would need do is add the IP of the client to your code to make it certain and repeat for each client to be backed up.

But my confusion comes with how to automate this.  What I would like to do is to have rsync run say 10 minutes after a user has logged in.  I cannot use cron since that requires a specific time to be stated and if you miss the time the command does not run.

Is there a trusted program that automates events in this manner?

check out anacron. I believe it is installed by default.

---

### Post by expatCM on 2009-01-02
Thanks for the messages ...

blueridgedog - I will work on this all tomorrow and try to get it sorted.  I will post back so that you know what I have done :)

handydan918 - anacron - well I had never heard of it but I just read through the man pages and that certainly seems to be very helpful :)

---

### Post by expatCM on 2009-01-04
I tried to backup from my machine to the server.  I used this command syntax

 rsync  -avzp -e ssh /home/user auser@server:/backup/user/home/


I stopped this running when I noticed that the nfs shares (like /home/user/music) were also being backed up. 

I need to work out how to run this but to exclude the two nfs shares, or do I need to relocate the shares?

The other question is that most of the data is not at the /home directory, it is in another location. It is best to backup both locations.  Should I simply extend the command or have a fresh command for the new location?

The command also prompts for the remote password every time it is run.  I have read somewhere that this can be fixed but I need to iron that out as well ..  I also need to look at the options carefully so that the destination will delete files that have been deleted on the source.

---

### Post by expatCM on 2009-01-04
I have made some progress with sorting out the ssh keys so there is no password prompt and also looking at the rsync options to add  the --del switch.

So far so good.

What I need to understand now is who to tell rsync to skip the two directories which are with the nfs shares but appearing in the /home hierarchy.

I also need to figure out how to tell rsync to look in two locations, the /home directory and the /data directory and process both.  I guess if there were some sort of link in the /home directory from the /data directory that would solve that if it worked in the same sort of way as the nfs shares ...

---

### Post by expatCM on 2009-01-04
The --exclude option helps such that if I add 

--exclude "Music/”

and this then skips the Music directory (nfs share) but if I add 

--exclude "Music/”  “Pictures/"

the command does not exclude Pictures.  Sadly the syntax is not well documented in the man pages.

---

### Post by blueridgedog on 2009-01-04
Since you will no doubt be doing this in a script, why not simply specify the directories you do want?

If you want to do it with one command, then look at the rsync man page and read about --exclude=PATTERN       exclude files matching PATTERN

---

### Post by expatCM on 2009-01-04
In a script?   I had not quite got that far with my thinking.  I have not written any sort of script since DOS (edited many of course).

So you are telling me to put this all in a file and then call the file from the .bashrc ?   Sounds like I will be on a learning curve .... but that is really not an issue.

If anyone else is reading this and noted my earlier comments about two folders after --exclude will not work, I have just found out that if you put --exclude before each directory it will work.

Since I appear to have solved the problem of the nfs shares (if not stating it nicely), what I am wondering now is if the --include command is going to be right to include the /home directory and the /data directory in the same command.

Just reading the man section on pattern rules.  There is a LOT of information there .........

---

### Post by blueridgedog on 2009-01-04
A simple approach would be to use the exclude file (make a file ~/.rsync/exclude) and put the patterns inside it you want to exclude.  Right now you only have two, Music and Pictures.  Put them one on a line and test until you have it working.

There is a more detailed example here:

[http://sial.org/howto/rsync/](http://sial.org/howto/rsync/)

---

### Post by expatCM on 2009-01-06
The learning is in progress ….  really not clear at the present but never mind …...

I have found a few problems like the exclude directories do not exclude (even though they did the very first time I tried this).  So I decided to try and make things clearer with an exclude file (just like you suggested).

So I have prepared this very simple script.  

```
#!/bin/sh
# rsync.sh
#
rsync -avR --exclude-from=$exclude.txt --include-from=$include.txt --log-file $rsynclog.txt --del -e ssh user@serverIP://network/backup/user/
```

Can I put this in the /opt directory together with the exclude, include and log files?

I am getting an error when I run the command from the terminal (without the separate files).  The error appears and then the command runs.  The error says something to the effect of .subversion/auth failed.    Permission denied (13). Google does not seem to help much but I was wondering if this is something to do with the permissions of the “.” files in /home/user?  If so there has to be a way round this …..... 

If not it may of course be a problem with ssh since I have got that wrong along the way with the need to unlock the keyring at every boot.  I will sort that out next …........

---

### Post by lswest on 2009-01-06
If you run the script from a folder outside of your home folder, add the full path to the exclude directories, otherwise it will look in the current folder.

Not sure about the exclude.txt file.

---

### Post by blueridgedog on 2009-01-06
First, double check that you are using -e correctly.  I bet ssh is complaining.

Note the following from the man page for rsync:

```
       If you need to specify a different remote-shell user, keep in mind that
       the  user@  prefix  in  front  of the host is specifying the rsync-user
       value (for a module that  requires  user-based  authentication).   This
       means  that  you  must give the ’-l user’ option to ssh when specifying
       the remote-shell, as in this example that uses the short version of the
       --rsh option:

           rsync -av -e "ssh -l ssh-user" rsync-user@host::module /dest

       The  “ssh-user” will be used at the ssh level; the “rsync-user” will be
       used to log-in to the “module”.
```

Also, I am not certain you want $ in front of your file names as that implies they are variables.

```
       --exclude-from=FILE
              This option is related to the --exclude option, but it specifies
              a  FILE  that  contains  exclude patterns (one per line).  Blank
              lines in the file  and  lines  starting  with  ‘;’  or  ‘#’  are
              ignored.   If  FILE  is  -,  the list will be read from standard
              input.
```


I suggest you debug this by doing it on the command line and going from simple to complex.  Get all of the basics working (ssh) then get an include file working then an exclude.  Test each addition carefully so you get the syntax right.

---

### Post by expatCM on 2009-01-08
I see through google that there are a lot of people with the same challenge as me.  Sadly the threads do not present solutions.

rtfm is often suggested.  I suspect the people suggesting this have not followed their own advice ......

I have simplified this to look at the source files only (no excludes). What happens is that use of the following command 

```
rsync -avn -e ssh --del /path/to/directory/ user@serverIP://path/to/backup

```

works without a hitch.

But as soon as I change it to 

```
rsync -avn -e ssh --del --include-from=/opt/include.txt  user@serverIP://path/to/backup

```

the way the command then works is to look to the remote location as the 
source, not the destination.

I have tried to write the include line in include.txt in three different ways (with "include, " with "+ " and just the line) but I get the idea that the file is not being read or at least not the line.

The man page tells you --include-from=FILE and does not mention path to file and then file.  So I put the file in /user/bin/ to see what happened (since locate says rsync is there) but it does not help.

The man pages tell you about the filters and the include / exclude files but give no examples of syntax in the command.  

It is amazing the number of web sites that are "authorities" that simply put a font round the man pages and present that as a solution ....

This is quite a challenge.

---

### Post by hyper_ch on 2009-01-08
> **expatCM said:**
> 
```
#!/bin/sh
# rsync.sh
#
rsync -avR --exclude-from=$exclude.txt --include-from=$include.txt --log-file $rsynclog.txt --del -e ssh user@serverIP://network/backup/user/
```


The "include" portion doesn't help much. I refer hereby to the "exclude/include" section in the manpages.

Also, in that script you did not define the variables. I'd change it to:

```

#!/bin/bash

from=user@serverIP://network/backup
to=/user/
exclude_file=/path/to/exclude.txt


# RUN RSYNC
rsync                                                 \
        -avR -e ssh --delete --delete-excluded        \
        --exclude-from="$exclude_file"                \
        $from                                         \
        $to;

```

---

### Post by expatCM on 2009-01-08
Hi hyper_ch, thank you for your interest.

I have to explore your amendments to the script file and try it out :)  It looks like you are suggesting to transfer from the remote location to the local.

What I want to do is to transfer two locations on local to the remote. Swapping the locations round is easy but how do you add different local directories, do you separate by comma or list on new lines?

I would like to learn about this and you said ...

> The "include" portion doesn't help much. I refer hereby to the "exclude/include" section in the manpages.

I was just wondering what you mean.  I have looked at the section on the man pages and really do not understand the problem.   I  thought the include file could include patterns to be included but is a directory path not also a pattern?  So what do I not understand (it has to be very basic)?

---

### Post by hyper_ch on 2009-01-08
yeah, just change from/to accordingly... it's always

rsync from_this to_this...

As for the include/exclude I think that the simplest way so to sync from the root folder and just exclude what you don't want to sync:

e.g.
```

/backup/
/bin/
/boot/
/cdrom/
/dev/
/initrd/
/initrd.img
/ionitrd.img.old
/lib/
/lost+found/
/mnt/
/opt/
/proc/
/sbin/
/srv/
/sys/
/tmp/
/usr/
/var/

```

---

### Post by blueridgedog on 2009-01-08
I think one of the core problems here is you want to log in on the workstation and trigger and rsync from the server to the workstation.  I don't have another box to mock this up, but I may bring one home tonight.

You will ultimately work out the syntax though.  Have you tried:

rsync -avn -e ssh --del --exclude-from=exclude.txt user@serverIP://servershare/userfiles/ /path/to/local/backup

Note I am specifying the source as remote (per your plan).

In the directory where you run this command must exist a file called excluded.txt which will have lines such as:

/home/user/music/
/home/user/.*/

---

### Post by hyper_ch on 2009-01-08
if you want to automatically sync to or from a remote computer you will need to setup key-based logins.

This means, from whichever computer you want to run rsync you will need to run:

```

ssh-keygen -t dsa

```
as user that shall then run the rsync cronjob

then
```

cat ~/.ssh/id_dsa.pub | ssh -l user server 'cat >> ~/.ssh/authorized_keys'

```
user = remote username to login by ssh
server = remote computer

If (successfully) done, you can then login into the remote computer just with:

```

ssh user@remote

```

If you have setup that, then you can simply use rsync over ssh an login at the remote computer.

---

### Post by expatCM on 2009-01-08
I appear to have made progress ..amazing really...

The lesson  I have learned here is to stop thinking of separate include and exclude files and to put everything in an exclude file. In that list think include first and then exclude for each directory.  Then on the terminal to simply backup /home/ and the exclude file takes care of the rest.

I ran this in the test mode and the log file indicated that the appropriate files were listed. Some very minor tweaking and I should be good ... 

The next step has to be sorting out the ssh permissions.  I think the easiest way will be to start this off fresh.

Then automation, complete on all the other machines and done :)

---

### Post by expatCM on 2009-01-11
Time to close this thread ....

Many thanks to everyone who has contributed here.

At the end of the day I have rsync working well.  I know how to automate but since ssh is prompting for a passphrase (and I have been unable to get rid of that) I need to keep it as a manual operation.  I have only done this on one machine and so perhaps the others will behave differently.

---

### Post by hyper_ch on 2009-01-11
have a look here:  [http://ubuntuforums.org/showthread.php?t=1034740](http://ubuntuforums.org/showthread.php?t=1034740)

---

### Post by blueridgedog on 2009-01-11
As hyper mentioned via his link, ssh can easily be automated by creating a key on the initiating system (in this case your workstation) and placing it authorized keys list of the server so that when they attempt to to connect, it will not ask for authentication.  

For the benefit of others, can you post your final rsync work up?  Perhaps after you get ssh working...

---

