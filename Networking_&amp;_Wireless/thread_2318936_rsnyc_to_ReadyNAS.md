---
title: "rsnyc to ReadyNAS"
date: 2016-03-30
forum: Networking &amp; Wireless
---

### Post by lingpanda on 2016-03-30
Hello,

  I have a Ubuntu 12.04 LTS server. I would like to copy files from this server onto a ReadyNAS 204 using rysnc. I can't get this to work. Here are my current steps.


[LIST]
[*]Create folder on ReadyNAS  (pfms1backup)
[*]Given Everyone network access  (Just to test)
[*]Enabled SMB and RSYNC protocols
[*]Under file access. Given Everyone Read/Write
[/LIST]

From a windows machine I can browse and map the folder just fine. It's when I attempt to access from Ubuntu, I am having issues. Here are my steps.


```
rsync -rv /srv/testnas/ NAS1:pfms1backup/
root@nas1's password:
sending incremental file list
file
file1

sent 130 bytes  received 50 bytes  27.69 bytes/sec
total size is 0  speedup is 0.00
```

When I browse on the ReadyNAS or via. windows. I do not see the two files. Thanks for any help.

---

### Post by lingpanda on 2016-03-31
I need to use the absolute path.

```
NAS1:/data/pfms1backup
```

---

