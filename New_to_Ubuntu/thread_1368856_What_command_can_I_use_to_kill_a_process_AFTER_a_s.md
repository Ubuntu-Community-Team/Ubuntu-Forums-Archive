---
title: "What command can I use to kill a process AFTER a specified number of seconds/minutes?"
date: 2009-12-31
forum: New to Ubuntu
---

### Post by diablo75 on 2009-12-31
My internet connection is limited by a daily cap and I'm downloading a large file from my home server over the course of several days, but I'd like to cut the transfer off an hour after I've left my laptop running where I live right now.  I'm using gFTP to download the file, and I try to do about 100 MB per day, resuming the file where I left off each day.

I'd like to be able to type a command that will kill gFTP after, say, one hour after I enter the command.  That way I can leave my room, go to work, and know I'll still have a little bit of bandwidth left when I get back to browse the web and make skype phone calls before going to bed.

Any ideas on how to best do this?

---

### Post by s.fox on 2009-12-31
Hello,

The only thing I can think of is trying ulimit.  You can kill a process using [ulimit]("http://ss64.com/bash/ulimit.html") by specifying the resources it will have available. The -t option will allow you to specify the max cpu seconds any process run from your shell can use (after which time the process will be killed). 

Hope this helps you.

-Silver Fox

---

### Post by .nedberg on 2009-12-31
If you want to run gFTP for one hour you could create a launcher like this:
```

#!/bin/bash
gftp &
pid=$!
sleep 3600
kill $pid

```
(assuming gftp is the executable for gFTP).

sleep 3600 make the script wait one hour, adjust to your needs. gFTP will be killed after this period.

---

### Post by Joeb454 on 2009-12-31
> **.nedberg said:**
> If you want to run gFTP for one hour you could create a launcher like this:
```

#!/bin/bash
gftp &
pid=$!
sleep 3600
kill $pid

```
(assuming gftp is the executable for gFTP).

sleep 3600 make the script wait one hour, adjust to your needs. gFTP will be killed after this period.

That's what I was trying to figure out :) Just wasn't sure how to get the pid, but now I know...thanks!

It's worth mentioning that sleep works with seconds (hence the 3600 for 1 hour).

---

### Post by komputes on 2009-12-31
I'd use this easy one-liner command:

```
$ sleep 1h; killall gftp
```

Cheers!

---

### Post by .nedberg on 2009-12-31
> **komputes said:**
> I'd use this easy one-liner command:

```
$ sleep 1h; killall gftp
```

Cheers!

Not so good if you have other instances of gFTP running (but why would you if you are capped like this?). And you would need to start gFTP first, then run this script.

---

### Post by diablo75 on 2009-12-31
> **.nedberg said:**
> Not so good if you have other instances of gFTP running (but why would you if you are capped like this?). And you would need to start gFTP first, then run this script.

This one-liner will work perfect.  Thanks!

---

### Post by Captain_tux on 2009-12-31
And you can also stop (pause) gFTP after the desired time, instead of killing it (and re-starting it when you're back):

**kill -STOP [PID]**

---

