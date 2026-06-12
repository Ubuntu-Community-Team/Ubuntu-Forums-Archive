---
title: "[NFS] export directory where subdir is on different harddisk"
date: 2007-06-11
forum: Networking &amp; Wireless
---

### Post by TakeshiKovacs on 2007-06-11
Well, the title says it all somehow, but I´ll give you some more details.

Server running NFS has 3 different harddisks
hdc mounted at /mnt/data/music
hdd mounted at /mnt/data/video
sda mounted at /mnt/data/video/Series

hdc and hdd can be mounted without any problems, but sda won´t show up on the client side.

Either if I export Series seperatly or not, the subdir on the client side will be empty.

/mnt/data/video 192.168.0.0/255.255.255.0(rw,sync)
/mnt/data/music 192.168.0.0/255.255.255.0(rw,sync)
/mnt/data/video/Series 192.168.0.0/255.255.255.0(rw,sync)

Any hints you guys can give me, because it´s kind of hard to google for this problem with words like nfs, mount, subdir and harddisk ;)

Reminded me of that classic [bash.org]("http://bash.org") quote:

> <Insomniak`> Stupid ******* Google
<Insomniak`> "The" is a common word, and was not included in your search
<Insomniak`> "Who" is a common word, and was not included in your search

Thanks in advance.

---

### Post by kidders on 2007-06-12
Hi there,

> **TakeshiKovacs said:**
> hdc and hdd can be mounted without any problems, but sda won´t show up on the client side.What do you mean by "won't show up"? For instance, is there an error when you try to mount /mnt/data/video/Series?

---

### Post by netztier on 2007-06-12
> **TakeshiKovacs said:**
> 
Any hints you guys can give me, because it´s kind of hard to google for this problem with words like nfs, mount, subdir and harddisk ;)


Well my googling for *NFS exports subdirectories* came up with quite a few references that say that you can't export a subdirectory if the parent dir is already exported.
For instance: [NFS FAQ ]("http://mleahu.web.cern.ch/mleahu/doc/unix/net/nfs%20faq.htm#nfs19").

Check **dmesg** and/or **/var/log/messages**, **/var/log/syslog** and the likes after you restart the nfs server - I bet there's messages that point to this error.

best regards

Marc

---

### Post by TakeshiKovacs on 2007-06-28
Sorry guys, I had absolutely no time to look after the problem. 

Anyway, I just read that:

> If an exported directory has mount points under it, files under those mount points will not be accessible by NFS clients. So if you exported the root directory / and has a separate filesystem mounted at /home , you would need to also export /home and clients would need to mount it in order to see the files under it.

Well, it's not what I wanted, but I guess I can live that. I mounted /mnt/data/video/Series into another directory.

Thx for the help though. :)

---

