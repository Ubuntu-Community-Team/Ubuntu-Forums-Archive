---
title: "FTP client with Scheduler"
date: 2011-04-14
forum: New to Ubuntu
---

### Post by boldhoof on 2011-04-14
Hi

I am looking for an ftp client that has a scheduler, so I can set it to download files over night, which is free time from my ISP. Used to use Flashfxp under windows, so anything as easy to setup and run as that would be excellent.

---

### Post by Nickjpost on 2011-04-14
I haven't used one before, but this one may work for you, [http://www.hiteksoftware.com/ablef/](http://www.hiteksoftware.com/ablef/)

---

### Post by rosencrantz on 2011-04-14
Does it have to be GUI?
How about using the cron scheduler daemon to execute a shell script - let's call it wgetlist.sh
```
#!/bin/bash
while read line 
do 
   wget $line 
done < $1
```
Make it executable: chmod a+x wgetlist.sh
Set up cron as described in this thread ([http://ubuntuforums.org/showthread.php?t=102626](http://ubuntuforums.org/showthread.php?t=102626)) to execute '/<absolute path>/wgetlist.sh listfile.txt' every night, with listfile.txt containing the file urls (one per line)

Schedulable FTP clients seem to cost actual money.
Edit: e.g. AbleFTP is only free for a 30 day trial...

---

### Post by boldhoof on 2011-04-15
thanks for the replies, will try both out see how I get on.

---

