---
title: "How to CP to network share"
date: 2008-12-19
forum: New to Ubuntu
---

### Post by AnimalMagic on 2008-12-19
On windows I use xcopy to copy any changed files to a server on a regular basis. It would appear that CP can do the same thing, but I am unable to figure out how. CP doesn't like smb: type addresses.

can anyone enlighten me :-)

---

### Post by hyper_ch on 2008-12-19
what filesystem is used by that network share? Is it a windows machine?

---

### Post by AnimalMagic on 2008-12-19
Sorry no, it's linux based, not sure which version (ReadyNas NV+). It is set up as a windows share as most of our machines are windows.

---

### Post by ichbinesderelch on 2008-12-19
you could mount the server hdd with smbmnt on the linux machine, don't sure if it will work but maybe give it a try!

---

### Post by sdennie on 2008-12-19
Are you able to see the network share in Nautilus?  If so, that means that you can probably find the network share on the command line in ~/.gvfs and use it as if it were any other directory.

---

### Post by Locke_99GS on 2008-12-19
You could mount the share as mentioned and use Nautilus or cp, or you could use scp, sftp, rsync, &c...

(rsync is my one of my favourite tools to use when moving lots of stuff on the LAN, especially backups.)

---

### Post by AnimalMagic on 2008-12-20
Thanks for the suggestions.

smbmount appeared to work, but I got an IO error when attempting anything e.g. ls

I can see the share in nautilus and drag items across, though I discovered last lite that it didn't work completely. a 3.4gig folder only copied 2.3 gig! Have to check 400+ folders now :-(

I will have a look at ~/.gvfs

In windows we use xcopy to regularly copy changed files and folders to the server. I want to set something similar up in linux and cp seems to have the appropriate flags. I did have a look at rsync, but can't quite work out how to use it. ReadyNas has an rsync server, but it doesn't seem to copy to the default home drive of the user. Perhaps with a little more time I will figure it out :-)

Regards

---

