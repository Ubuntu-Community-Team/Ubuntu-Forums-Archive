---
title: "&quot;at&quot; command"
date: 2009-05-24
forum: New to Ubuntu
---

### Post by H.om on 2009-05-24
I did the following command
"at now +2 min"
warning: commands will be executed using /bin/sh
"at> shutdown" 
at> <EOT>
job 8 at Sun May 24 23:02:00 2009

But it didn't shut down my pc.Please help.
can u please give me a working example of this command

---

### Post by MockY on 2009-05-24
To shut down your computer, use the following
```
sudo shutdown -h now
```
or simply
```
sudo halt
```

---

