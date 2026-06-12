---
title: "Long startup and even longer shutdown w/ steady disk activity."
date: 2010-11-08
forum: New to Ubuntu
---

### Post by ubuntu1sttimer on 2010-11-08
Am running 10.04 on a few years old desktop. Has been going great until recently when something has changed. Most but not all boots now take five minutes or more. Then when I go to shut off the machine, it is ten minutes or more before the machine shuts down. All this time the hard drive light is lit steady. 

Might be indexing but not sure why it started or how to find out if that is it. Any ideas on how to determine what the cause is would be most helpful. After that, will need to know how to correct it. 

Have searched this sight but did not find it.

---

### Post by amauk on 2010-11-08
see if there is any obvious errors in your logs, particularly
/var/log/boot.log
/var/log/syslog
/var/log/messages

---

### Post by ubuntu1sttimer on 2010-11-08
Thanks for your reply. I rebooted the machine and it booted in 3 min. Not nearly how long it has taken. Shutdown was a couple min. 

Not sure if I did it correctly but think that I attached the logs files to this message. If not, will try again. 

Don't really know what I am looking for but did not see anything that appeared to apply. If you care to review them, you might see something that explains the problem.

---

### Post by ubuntu1sttimer on 2010-11-08
Tried log file attachments again but it didn't work. 

AMAUK, thanks for your help. The time it takes seems to very so maybe they will get shorter. If not, I will just have to get used to it or use something else.

---

### Post by amauk on 2010-11-08
Startup times do vary to some extent

There's a boot process called ureadahead that runs occasionally, and it logs what files are needed during boot, then rearranges the files on disk so that all the boot files are next to each other and so are accessed quicker

Anything over 2 mins though is almost certainly a problem, so if it happens again, file a bug on launchpad (people will tell you what logs to post, and how)

---

### Post by ubuntu1sttimer on 2010-11-08
amauk, thank you for your assistance. I will do that. First I will wait for one of the really bad cases and look at the log files. Then file a bug report.

---

