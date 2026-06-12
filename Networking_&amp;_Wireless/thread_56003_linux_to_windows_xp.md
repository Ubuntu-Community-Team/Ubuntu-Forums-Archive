---
title: "linux to windows xp"
date: 2005-08-11
forum: Networking &amp; Wireless
---

### Post by kobix on 2005-08-11
Hi

I want to copy files from one machine which runs ubuntu to another which runs xp.
I managed to see the shared folders of the xp using Places -> Network Servers. I even managed to see the specific folder I want to copy to. I dont know how to make a line/mount this folder in my ubuntu file system so I can do a simple cp? Should I try rcp?

Thanks.

---

### Post by blind0wl on 2005-08-11
Try this:

[http://www.ubuntuguide.org/#mountunmountnetworkfoldersall](http://www.ubuntuguide.org/#mountunmountnetworkfoldersall)

---

### Post by kobix on 2005-08-11
It does not work. The linux does not recognize windows.

Thanks, Koby

---

### Post by blind0wl on 2005-08-11
Maybe try this first [http://www.ubuntuguide.org/#installsamba](http://www.ubuntuguide.org/#installsamba)

---

### Post by kobix on 2005-08-11
Thanks. I get 
mount: special device //192.168.0.0/Docs does not exist

---

### Post by blind0wl on 2005-08-11
What is 192.168.0.0??  You cant use that as an IP address.  Can you ping that address?

```
ping 192.168.0.0
```

---

### Post by kobix on 2005-08-11
It is not the true one. I just was too lazy to copy the true one.

Thanks.

---

### Post by varunus on 2005-08-11
If you can see the folder in places->network servers, can't you open it there?  If so, can't you just drag the files you want to copy over?

---

### Post by tread on 2005-08-11
Just share the windows xp as writable, then connect to it through linux.

---

### Post by kobix on 2005-08-12
Tried that. The natilus stops in the middle with a message that an error occured.

Thanks.

---

