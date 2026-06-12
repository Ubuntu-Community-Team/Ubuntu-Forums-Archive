---
title: "Cannot access home dir of other computer using nfs"
date: 2007-03-28
forum: Networking &amp; Wireless
---

### Post by williammanda on 2007-03-28
I setup nfs server and client on two computers. When I use the client to access the server I can access all the directories except for the home directory. I have this in my /etc/export file on the server:
/ 192.168.1.1/24(rw,no_root_squash,sync) (i believe this is correct)

When I try to access the home directory on the server, it shows an empty directory.
Thanks

---

### Post by williammanda on 2007-03-30
I'm wondering if I have place this in the right area? If not, where should I?
Thanks

---

### Post by williammanda on 2007-04-02
I'll give this one more try to get a response.
Thanks

---

### Post by netztier on 2007-04-02
> **williammanda said:**
> I'll give this one more try to get a response.
Thanks

File/Directory perimissions? 
Do UID/GID match for your current user on both systems? 
Are home directories on the remote system readable/browseable for everyone?

That's a few things to check.

best regards

Marc

---

### Post by williammanda on 2007-04-10
[I][I]File/Directory perimissions? 
Do UID/GID match for your current user on both systems?[/I] 
Yes
*Are home directories on the remote system readable/browseable for everyone?*
Yes
These were the first things addressed.

I can't seem to get a good reason why this is an issue. If anyone else has an idea, please post.

I ended up changing the export file entry to:
/home 192.168.1.1/24(rw,no_root_squash,sync)

Thanks

---

