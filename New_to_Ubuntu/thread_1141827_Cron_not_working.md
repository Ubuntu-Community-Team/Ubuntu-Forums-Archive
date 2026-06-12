---
title: "Cron not working"
date: 2009-04-28
forum: New to Ubuntu
---

### Post by Red Rhino on 2009-04-28
I tried to set up a timed shutdown of my computer and created a cron.txt file which has this line:

00 01 * * * shutdown -P 

then I did a crontab cron.txt (which I believe enables it)

However, at 1am the computer did not shutdown. When I do a crontab -l I see the 00 01 * * * shutdown -P

any help would be appreciated.

---

### Post by wizard10000 on 2009-04-28
> **Red Rhino said:**
> I tried to set up a timed shutdown of my computer and created a cron.txt file which has this line:

00 01 * * * shutdown -P 

then I did a crontab cron.txt (which I believe enables it)

However, at 1am the computer did not shutdown. When I do a crontab -l I see the 00 01 * * * shutdown -P

any help would be appreciated.

You're missing a parameter - the time you want the machine to shut down.

Should be 00 01 * * * shutdown -P now

---

### Post by tricolorpoa on 2009-04-28
why not

```
# crontab -e
```


:confused:

---

### Post by supererki on 2009-04-28
The generic file /etc/crontab contains data that tells cron when to execute command
in /etc/cron.d you put your files or scripts that make s*it done.

---

### Post by llamabr on 2009-04-28
It's bad news trying to edit your cron file yourself.  You should always do so with the cron editor, with 

```
crontab -e
```

Did you add the extra *?  What happened?

---

### Post by Red Rhino on 2009-04-28
Thanks, I have used crontab -e to add NOW to my file. Much easier to use and we'll see if it works tonight.

---

### Post by Red Rhino on 2009-04-29
I checked this morning and the computer was still running. It did not shut down as I had hoped. 

Is there a log file of some type I can check to see why this cron job isn't kicking off?

I am also going to be changing the time from 1a to 7p or something I can test while I am in front of the computer.

---

### Post by tricolorpoa on 2009-04-29
Try to pass the full path to command

```
00 01 * * * /sbin/shutdown -P
```

Are there some messages in your syslog?

```
# cat /var/log/syslog | grep cron
```

---

### Post by Red Rhino on 2009-04-29
Here is the output from the syslog:

rhino@RhinoLinux:~$ cat /var/log/syslog | grep cron
Apr 29 07:41:44 RhinoLinux anacron[24873]: Job `cron.daily' terminated
Apr 29 07:41:44 RhinoLinux anacron[24873]: Normal exit (1 job run)
Apr 29 08:17:01 RhinoLinux /USR/SBIN/CRON[25655]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 09:17:01 RhinoLinux /USR/SBIN/CRON[26558]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 10:17:01 RhinoLinux /USR/SBIN/CRON[27348]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 11:17:02 RhinoLinux /USR/SBIN/CRON[28138]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
rhino@RhinoLinux:~$ 


I have also changed the cron file to 1pm to see if it will shutdown in the next hour or if I get any error messages as well as adding sbin/ to the shutdown command.

Here is the new cron job:

rhino@RhinoLinux:~$ crontab -e
crontab: installing new crontab
rhino@RhinoLinux:~$ crontab -l
00 13 * * * sbin/shutdown -P now
rhino@RhinoLinux:~$

---

### Post by kpkeerthi on 2009-04-29
its missing a slash / before sbin

```

00 13 * * * /sbin/shutdown -P now

```

---

### Post by Red Rhino on 2009-04-29
Ahh, thanks, I have updated. Thanks

Hopefully in about 15 minutes I'll see if works.

---

### Post by tricolorpoa on 2009-04-29
worked?

---

### Post by kpkeerthi on 2009-04-29
> **Red Rhino said:**
> Ahh, thanks, I have updated. Thanks

Hopefully in about 15 minutes I'll see if works.

Wait for 15 minutes... LOL!. Why not set the cron to trigger in 1 minute from now and test.

---

### Post by Red Rhino on 2009-04-29
Well 1pm came and went and nothing happened.

It appears the system is checking the cron file hourly, but at the specified time, it fails to launch.

rhino@RhinoLinux:~$ cat /var/log/syslog | grep cron
Apr 29 07:41:44 RhinoLinux anacron[24873]: Job `cron.daily' terminated
Apr 29 07:41:44 RhinoLinux anacron[24873]: Normal exit (1 job run)
Apr 29 08:17:01 RhinoLinux /USR/SBIN/CRON[25655]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 09:17:01 RhinoLinux /USR/SBIN/CRON[26558]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 10:17:01 RhinoLinux /USR/SBIN/CRON[27348]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 11:17:02 RhinoLinux /USR/SBIN/CRON[28138]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 12:07:25 RhinoLinux crontab[29165]: (rhino) BEGIN EDIT (rhino)
Apr 29 12:07:51 RhinoLinux crontab[29165]: (rhino) REPLACE (rhino)
Apr 29 12:07:51 RhinoLinux crontab[29165]: (rhino) END EDIT (rhino)
Apr 29 12:07:57 RhinoLinux crontab[29169]: (rhino) LIST (rhino)
Apr 29 12:08:01 RhinoLinux /usr/sbin/cron[2883]: (rhino) RELOAD (crontabs/rhino)
Apr 29 12:08:24 RhinoLinux crontab[29170]: (rhino) BEGIN EDIT (rhino)
Apr 29 12:08:34 RhinoLinux crontab[29170]: (rhino) REPLACE (rhino)
Apr 29 12:08:34 RhinoLinux crontab[29170]: (rhino) END EDIT (rhino)
Apr 29 12:08:36 RhinoLinux crontab[29174]: (rhino) LIST (rhino)
Apr 29 12:09:01 RhinoLinux /usr/sbin/cron[2883]: (rhino) RELOAD (crontabs/rhino)
Apr 29 12:17:01 RhinoLinux /USR/SBIN/CRON[29368]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 12:35:02 RhinoLinux anacron[2813]: Anacron 2.3 started on 2009-04-29
Apr 29 12:35:02 RhinoLinux anacron[2813]: Normal exit (0 jobs run)
Apr 29 12:35:03 RhinoLinux /usr/sbin/cron[2856]: (CRON) INFO (pidfile fd = 3)
Apr 29 12:35:03 RhinoLinux /usr/sbin/cron[2857]: (CRON) STARTUP (fork ok)
Apr 29 12:35:03 RhinoLinux /usr/sbin/cron[2857]: (CRON) INFO (Running @reboot jobs)
Apr 29 12:41:26 RhinoLinux crontab[3880]: (rhino) BEGIN EDIT (rhino)
Apr 29 12:41:38 RhinoLinux crontab[3880]: (rhino) REPLACE (rhino)
Apr 29 12:41:38 RhinoLinux crontab[3880]: (rhino) END EDIT (rhino)
Apr 29 12:41:41 RhinoLinux crontab[3884]: (rhino) LIST (rhino)
Apr 29 12:42:01 RhinoLinux /usr/sbin/cron[2857]: (rhino) RELOAD (crontabs/rhino)
Apr 29 13:17:01 RhinoLinux /USR/SBIN/CRON[4288]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 13:22:26 RhinoLinux anacron[2835]: Anacron 2.3 started on 2009-04-29
Apr 29 13:22:26 RhinoLinux anacron[2835]: Normal exit (0 jobs run)
Apr 29 13:22:26 RhinoLinux /usr/sbin/cron[2878]: (CRON) INFO (pidfile fd = 3)
Apr 29 13:22:26 RhinoLinux /usr/sbin/cron[2879]: (CRON) STARTUP (fork ok)
Apr 29 13:22:26 RhinoLinux /usr/sbin/cron[2879]: (CRON) INFO (Running @reboot jobs)
rhino@RhinoLinux:~$ 

At 13:22 I manually did a shutdown -P now, but noticed I had to have root priviledge to do this. It that what is keeping the cron job from executing?

This is the current cron job:

rhino@RhinoLinux:~$ crontab -l
00 13 * * * /sbin/shutdown -P now
rhino@RhinoLinux:~$

---

### Post by kpkeerthi on 2009-04-29
You need to put that command is super user's crontab:

```
sudo crontab -e
```

---

### Post by tricolorpoa on 2009-04-29
Please,

when post your syslog, tell what time was seted in your cron.

---

### Post by Red Rhino on 2009-04-29
I see now, I was creating a cron file under my own id, not sudo. When I did sudo crontab -e it brought up the original cron file I had at the beginning of all this. I have updated it now.

You can now see there are 2 cron jobs, one for me and one for sudo:

rhino@RhinoLinux:~$ sudo crontab -e
[sudo] password for rhino: 
crontab: installing new crontab
rhino@RhinoLinux:~$ sudo crontab -l
45 13 * * * /sbin/shutdown -P now 
rhino@RhinoLinux:~$ crontab -l
30 14 * * * /sbin/shutdown -P now
rhino@RhinoLinux:~$ 

I suspect we'll see something happen now!!!

I will delete mine if this works, since I don't need it.

---

### Post by kukibird1 on 2009-04-29
In a terminal type sudo visudo and add the following line at the end of the file and save it and reboot your machine.

%admin ALL=NOPASSWD: /sbin/shutdown /usr/sbin/pm-suspend


You might need to add DISPLAY=:0.0 to the top of your crontab file. 
here is mine. You still need to put sudo in front of shutdown command.

DISPLAY=:0.0
PATH= /home/kukibird1/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
# m h  dom mon dow   command
0 23 * * * sudo /usr/sbin/pm-suspend

the path part is optional run echo $PATH in a terminal to get yours .

---

### Post by Red Rhino on 2009-04-29
Modifying the right cron file worked!! :) 

The system shutdown at 13:45 as instructed. Thanks kpkeerthi and others for the help. While I'm sure the original responders may have implied the SUDO in their contrab -e responses, its the little things like this that gets us Noobs every time. Thank again!!

rhino@RhinoLinux:~$ cat /var/log/syslog | grep cron
Apr 29 07:41:44 RhinoLinux anacron[24873]: Job `cron.daily' terminated
Apr 29 07:41:44 RhinoLinux anacron[24873]: Normal exit (1 job run)
Apr 29 08:17:01 RhinoLinux /USR/SBIN/CRON[25655]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 09:17:01 RhinoLinux /USR/SBIN/CRON[26558]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 10:17:01 RhinoLinux /USR/SBIN/CRON[27348]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 11:17:02 RhinoLinux /USR/SBIN/CRON[28138]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 12:07:25 RhinoLinux crontab[29165]: (rhino) BEGIN EDIT (rhino)
Apr 29 12:07:51 RhinoLinux crontab[29165]: (rhino) REPLACE (rhino)
Apr 29 12:07:51 RhinoLinux crontab[29165]: (rhino) END EDIT (rhino)
Apr 29 12:07:57 RhinoLinux crontab[29169]: (rhino) LIST (rhino)
Apr 29 12:08:01 RhinoLinux /usr/sbin/cron[2883]: (rhino) RELOAD (crontabs/rhino)
Apr 29 12:08:24 RhinoLinux crontab[29170]: (rhino) BEGIN EDIT (rhino)
Apr 29 12:08:34 RhinoLinux crontab[29170]: (rhino) REPLACE (rhino)
Apr 29 12:08:34 RhinoLinux crontab[29170]: (rhino) END EDIT (rhino)
Apr 29 12:08:36 RhinoLinux crontab[29174]: (rhino) LIST (rhino)
Apr 29 12:09:01 RhinoLinux /usr/sbin/cron[2883]: (rhino) RELOAD (crontabs/rhino)
Apr 29 12:17:01 RhinoLinux /USR/SBIN/CRON[29368]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 12:35:02 RhinoLinux anacron[2813]: Anacron 2.3 started on 2009-04-29
Apr 29 12:35:02 RhinoLinux anacron[2813]: Normal exit (0 jobs run)
Apr 29 12:35:03 RhinoLinux /usr/sbin/cron[2856]: (CRON) INFO (pidfile fd = 3)
Apr 29 12:35:03 RhinoLinux /usr/sbin/cron[2857]: (CRON) STARTUP (fork ok)
Apr 29 12:35:03 RhinoLinux /usr/sbin/cron[2857]: (CRON) INFO (Running @reboot jobs)
Apr 29 12:41:26 RhinoLinux crontab[3880]: (rhino) BEGIN EDIT (rhino)
Apr 29 12:41:38 RhinoLinux crontab[3880]: (rhino) REPLACE (rhino)
Apr 29 12:41:38 RhinoLinux crontab[3880]: (rhino) END EDIT (rhino)
Apr 29 12:41:41 RhinoLinux crontab[3884]: (rhino) LIST (rhino)
Apr 29 12:42:01 RhinoLinux /usr/sbin/cron[2857]: (rhino) RELOAD (crontabs/rhino)
Apr 29 13:17:01 RhinoLinux /USR/SBIN/CRON[4288]: (root) CMD (   cd / && run-parts --report /etc/cron.hourly)
Apr 29 13:22:26 RhinoLinux anacron[2835]: Anacron 2.3 started on 2009-04-29
Apr 29 13:22:26 RhinoLinux anacron[2835]: Normal exit (0 jobs run)
Apr 29 13:22:26 RhinoLinux /usr/sbin/cron[2878]: (CRON) INFO (pidfile fd = 3)
Apr 29 13:22:26 RhinoLinux /usr/sbin/cron[2879]: (CRON) STARTUP (fork ok)
Apr 29 13:22:26 RhinoLinux /usr/sbin/cron[2879]: (CRON) INFO (Running @reboot jobs)
Apr 29 13:27:16 RhinoLinux crontab[3404]: (rhino) LIST (rhino)
Apr 29 13:29:33 RhinoLinux crontab[3405]: (rhino) BEGIN EDIT (rhino)
Apr 29 13:29:42 RhinoLinux crontab[3405]: (rhino) REPLACE (rhino)
Apr 29 13:29:42 RhinoLinux crontab[3405]: (rhino) END EDIT (rhino)
Apr 29 13:29:44 RhinoLinux crontab[3409]: (rhino) BEGIN EDIT (rhino)
Apr 29 13:29:52 RhinoLinux crontab[3409]: (rhino) REPLACE (rhino)
Apr 29 13:29:52 RhinoLinux crontab[3409]: (rhino) END EDIT (rhino)
Apr 29 13:29:58 RhinoLinux crontab[3413]: (rhino) LIST (rhino)
Apr 29 13:30:01 RhinoLinux /usr/sbin/cron[2879]: (rhino) RELOAD (crontabs/rhino)
Apr 29 13:30:11 RhinoLinux crontab[3596]: (rhino) BEGIN EDIT (rhino)
Apr 29 13:30:28 RhinoLinux crontab[3596]: (rhino) REPLACE (rhino)
Apr 29 13:30:28 RhinoLinux crontab[3596]: (rhino) END EDIT (rhino)
Apr 29 13:30:30 RhinoLinux crontab[3600]: (rhino) LIST (rhino)
Apr 29 13:31:01 RhinoLinux /usr/sbin/cron[2879]: (rhino) RELOAD (crontabs/rhino)
Apr 29 13:34:07 RhinoLinux crontab[3603]: (root) BEGIN EDIT (root)
Apr 29 13:34:38 RhinoLinux crontab[3603]: (root) REPLACE (root)
Apr 29 13:34:38 RhinoLinux crontab[3603]: (root) END EDIT (root)
Apr 29 13:34:53 RhinoLinux crontab[3607]: (root) LIST (root)
Apr 29 13:34:59 RhinoLinux crontab[3608]: (rhino) LIST (rhino)
Apr 29 13:35:01 RhinoLinux /usr/sbin/cron[2879]: (root) RELOAD (crontabs/root)
Apr 29 13:46:33 RhinoLinux anacron[2865]: Anacron 2.3 started on 2009-04-29
Apr 29 13:46:33 RhinoLinux anacron[2865]: Normal exit (0 jobs run)
Apr 29 13:46:33 RhinoLinux /usr/sbin/cron[2908]: (CRON) INFO (pidfile fd = 3)
Apr 29 13:46:33 RhinoLinux /usr/sbin/cron[2909]: (CRON) STARTUP (fork ok)
Apr 29 13:46:33 RhinoLinux /usr/sbin/cron[2909]: (CRON) INFO (Running @reboot jobs)
rhino@RhinoLinux:~$

---

### Post by tricolorpoa on 2009-04-29
> **tricolorpoa said:**
> why not

```
# crontab -e
```
:confused:


# < - this means a command as root user

---

### Post by Red Rhino on 2009-04-29
Thanks Tricolorpoa, I didn't catch that. All these new commands and symbols are taking a little getting used to.

I do have a follow up. If I change the command from NOW to +5 is there a way to get it to display the shutdown messages without being in terminal?

Thanks again!

---

