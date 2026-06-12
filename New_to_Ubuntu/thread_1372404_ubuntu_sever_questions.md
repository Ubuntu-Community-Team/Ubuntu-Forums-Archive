---
title: "ubuntu sever questions"
date: 2010-01-04
forum: New to Ubuntu
---

### Post by pyrofreak99 on 2010-01-04
[B][IMG]http://www.ubuntu.com/files/masthead/910/dl/round1.png[/IMG]i have this computer in the living room that im installing ubuntu server  9.10 on to well im just wondering how would i connect that one to my laptop thats running 9.08    and transfer files from there and such
[/B]

---

### Post by Stormspace on 2010-01-04
> **pyrofreak99 said:**
> [B][IMG]http://www.ubuntu.com/files/masthead/910/dl/round1.png[/IMG]i have this computer in the living room that im installing ubuntu server  9.10 on to well im just wondering how would i connect that one to my laptop thats running 9.08    and transfer files from there and such
[/B]

I've done it, but had to resort to using Samba to set up a windows share for the other Ubuntu machines to connect to. I've had limited success and sometimes have permission issues connecting via Ubuntu, but no problems connecting via windows.

---

### Post by Cheesemill on 2010-01-04
You can share files between Ubuntu machines by setting up NFS:
[http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html](http://www.ubuntugeek.com/nfs-server-and-client-configuration-in-ubuntu.html)

BTW - There is no such thing as Ubuntu 9.08

---

### Post by mkoehler on 2010-01-04
8.10 maybe :P  Anyhow, I'd just use scp (secure copy) - it's basically a way to copy files via ssh (so a CLI).

---

### Post by Charlietje on 2010-01-04
for transfering files i would go with scp.

what do you mean by 'and such'?

---

### Post by bodhi.zazen on 2010-01-04
> **pyrofreak99 said:**
> [B][IMG]http://www.ubuntu.com/files/masthead/910/dl/round1.png[/IMG]i have this computer in the living room that im installing ubuntu server  9.10 on to well im just wondering how would i connect that one to my laptop thats running 9.08    and transfer files from there and such
[/B]

Please use the default font size without bold. If you are having problems seeing please adjust your browser (Ctrl + and Ctrl - ).

There are many ways of transferring files from sneakerware (flash drives, CD)  to network protocols (NFS, Samba, FTP, SCP (sftp), http).

On a LAN I would use Samba, ssh (SCP/sftp) over the internet.

---

### Post by Maheriano on 2010-01-04
To transfer files just use the Connect To Server in the menu. That's how I do it, and I I remote desktop with NXClient.

---

