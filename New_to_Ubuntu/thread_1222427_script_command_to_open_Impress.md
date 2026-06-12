---
title: "script command to open Impress?"
date: 2009-07-24
forum: New to Ubuntu
---

### Post by kenmac2 on 2009-07-24
I need to auto-open Impress (Open Office Presentation) using a Crontab line.
What  Command text is required to achieve this?

Ken Mac

---

### Post by niteshifter on 2009-07-24
Hi,

```
ooimpress
```
or
```
ooimpress *options* *filename*
```

For details on options, etc.:
```
man openoffice
```

---

### Post by kenmac2 on 2009-07-25
Thanks for the pointer to the Options.
I can open Impress via the Terminal OK.
However, Crontab doesn't react to the same command.
I've tried both User and root Crontabs, same result.
Looked for **/etc/cron.allow** and **/etc/cron.deny** and it says they don't exist.
This is the code used: 
```
25 12 * * * ooimpress
```The time used is a few minutes after creating the Crontab.
Maybe it is expecting the full Path?

kenmac2

---

### Post by llamabr on 2009-07-25
Full path wouldn't kill you.  How are you editing your cron?

---

### Post by kenmac2 on 2009-07-25
I'm using nano and when exited it says "installing new Crontab".
Hmmm ... what is the full Path to Impress?
I'm still getting to terms with the file system.

kenmac2

---

### Post by kenmac2 on 2009-07-25
Well, I know that Crontab actually works - I can program a shutdown and it happens.
However, I cannot get it to open Impress, whatever I use for the Command.

kenmac2

---

### Post by kpkeerthi on 2009-07-25
When used in crontab, you should refer to an executable file using absolute path. You can find the absolute path of ooimpress using
```

which ooimpress

```
Most likely it would be /usr/bin/ooimpress

Also when lauching GUI application from cron, you need to set the DISPLAY variable. Refer to the [wiki page]("https://help.ubuntu.com/community/CronHowto") for detailts on how to set this variable.

---

### Post by kenmac2 on 2009-07-25
So, we just add the display variable before the actual command path?
I tried this:
```
12 15 * * * env DISPLAY=:0 /usr/bin/ooimpress
``` but it didn't work.

kenmac2

---

### Post by kpkeerthi on 2009-07-25
When you enter **/usr/bin/ooimpress** at the command prompt, does it 
launch?
If it did, the below cron entry should work:
```

12 15 * * * export DISPLAY=:0 && /usr/bin/ooimpress

```

EDIT:
You may redirect the output to a file so you can check what went wrong when the cron triggered

```

12 15 * * * export DISPLAY=:0 && /usr/bin/ooimpress > /home/[COLOR="Red"]<your-user-id>[/COLOR]/cron.log 2>&1

```

---

### Post by kenmac2 on 2009-07-25
Yes, it works from the Terminal command.
No luck - your suggested command didn't work.
Also, I couldn't find that file cron.log.
Incidentally, I'm using the root crontab.

kenmac2

---

### Post by kpkeerthi on 2009-07-25
> **kenmac2 said:**
> 
Incidentally, I'm using the root crontab.

Why do you want to run a GUI app as a root? Run it from user's crontab.

---

### Post by kpkeerthi on 2009-07-25
> **kenmac2 said:**
> 
Also, I couldn't find that file cron.log.

If you followed my post and can't find the log file, it could mean that cron is probably not working for you. The log file should be created if the cron triggered successfully.

---

### Post by kenmac2 on 2009-07-25
When called from the Terminal it does open the program OK and it works, but it reports the following in the Terminal:
> **Javaldx**: Could not find a Java Runtime Environment!
Please ensure that the package openoffice.org - java - common is installed. If it is already installed then try removing ~/.openoffice.org3/user/config /javasettings_Linux_*.xmlThen it says:
> (soffice:9658) : WARNING **: unable to get gail version numberI haven't a clue as to what all that means, but Impress does open OK.

I used the root crontab because I thought there would be more chance of it working.

The Crontab worked OK for the shutdown.
Does that file get deleted after the action?


kenmac2

---

### Post by kenmac2 on 2009-07-25
I'll try the shutdown again and see if the file is generated.

kenmac2

---

### Post by kpkeerthi on 2009-07-25
The shutdown command requires super-user privileges. So it should be in root's crontab.

---

### Post by kenmac2 on 2009-07-25
The shutdown still works OK but didn't generate a file - I think I stuffed up the command there.
Too tired to continue now, been on this a couple of days, so taking a break until next week.

kenmac2

---

### Post by niteshifter on 2009-07-25
Hi,

When you get back 'round to it ...

This:
> Javaldx: Could not find a Java Runtime Environment!
Please ensure that the package openoffice.org - java - common is installed. If it is already installed then try removing ~/.openoffice.org3/user/config /javasettings_Linux_*.xml

is a warning from OO that Java is not enabled. This can mean nothing or it can mean things aren't going to work, like macros and perhaps some wizard applets within OO. It means nothing if you've not installed Java Runtime (JRE) or Java Development Kit (JDK) and have no intention of doing so. If you do mean to have Java with OO and have installed a JRE or JDK this warning most likely means that you haven't selected it in OO yet.

---

### Post by kenmac2 on 2009-07-26
OK, I'm resuming my attempt to open Impress automatically.
I entered the following in the user Crontab :
```
12 13 * * * export DISPLAY=:0 && /usr/bin/ooimpress > /home/ahm/cron.log
```[ Note: username is "ahm" ]
As usual, it didn't run.
So, I then looked at the Cron.log.
It repeated the error message that I previously mentioned re Java.
I couldn't find the files etc that it quoted.
It seems that this doesn't stop manually opening Impress, but Crontab doesn't like it.
This is a standard 9.04 new installation, with no  programs added/removed.
Expert advice required - has anyone successfully auto-opened Impress in Ubuntu 9.04?

kenmac2

---

### Post by kenmac2 on 2009-07-27
Success!
I went into the program OpenOffice's Options, and found that Java is indeed installed and selected.
So, I turned it off, and reset the Crontab and hey presto!, up came Impress at the prescribed time.
Having achieved that I can now proceed with fine tuning the setup.

Thanks for your help folks.
kenmac2

---

