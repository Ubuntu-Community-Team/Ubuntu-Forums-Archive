---
title: "Help deleting a file"
date: 2009-08-14
forum: New to Ubuntu
---

### Post by barnaclebill18 on 2009-08-14
Hello,

I am really new to this and don't have much computer experience.

I recently installed Ubuntu 9.04 and am trying to install the Sprint Air Card software.

I made a mistake after I downloaded the kppp packages and wanted to do it again, so I removed the drivers and downloaded them again.  

Everything was going good, I was following the instructions in the Sprint Guide but when I got to the page where I clicked "new" to create a new account, the program froze and a box came up:

kppp has detected a /home/bill/.kde/share/apps/kppp/kppp.pid file.Another instance of kppp seems to be running under process-ID 3,665. 
Please click Exit, make sure that you are not running another kppp, delete the pid file, and restart kppp.
Alternatively, if you have determined that there is no other kppp running, please click Continue to begin.

I really don't know how to do this.

I looked for the file, but could not find it. I ran a search for kppp and came up with a bunch of them but I could not find any with that name. I typed the whole file name in the search box and it did not find it. If it did I really don't know how to delete it.

Any help is appreciated, thanks,

---

### Post by sblunix on 2009-08-14
DON'T do this command until you recieve more feedback from the community, but you just need to kill the other process which I think is done in the terminal with something like ```
kill 3665
``` but I'm not sure, so wait for more feedback.

---

### Post by llamabr on 2009-08-14
Ya, that'll do.  run:

```
kill -9 3665
```

and try again.

---

### Post by barnaclebill18 on 2009-08-14
> **llamabr said:**
> Ya, that'll do.  run:

```
kill -9 3665
```

and try again.

Thanks for the replies.

When I started the computer this morning and went back to kppp, the number had changed, I used the new number and it worked.

Thank you, again.

---

### Post by harry2006 on 2009-08-14
yes, everytime the process is assigned a new processID. so you just have to find the ID and kill it. You can use "ps -aux|grep -i kppp" to get the process ID ...

---

