---
title: "Firefox locked up"
date: 2010-12-08
forum: New to Ubuntu
---

### Post by nu2this2 on 2010-12-08
Have 10.10 on a desktop and was noticing some strange behavior while browsing the web. First of all the loading of web pages was getting slower and slower.Now the browser is locked onto a website and now matter what I type in the search bar nothing happens.

Anyone have an idea?----------Thank you.

---

### Post by hwychld on 2010-12-08
Are you able to close the browser and open another one?  If not kill the current firefox process and then try to start a new one and see if the same thing happens.

```
ps aux | grep -v grep | grep -i firefox  
```

from the command line should give you a process listing(s) for firefox.  One of the items in the listing is the PID that can be used for killing the hung process

```
kill PID
``` 

where you replace PID with the number found above.  If that doesn't work you can do this:

```
kill -9 PID
``` 

to send a SIGKILL to the process (default as above is SIGTERM).

Or if you launched Firefox from a terminal you can run 'jobs' from that same terminal and get a PID for Firefox (if Firefox is in the foreground type Ctrl-Z and run jobs to get the job number and then run 'bg #' where # is the job number for firefox returned by the jobs command above.

---

