---
title: "Use on Windows Server network"
date: 2009-10-04
forum: New to Ubuntu
---

### Post by mlsills on 2009-10-04
I would like to try Ubuntu as an alternative to MS Windows. However, our school network is Windows Server 2003. How do I make an Ubuntu computer a part of the Windwos Server 2003 network?

Thanks in advance!

Mark

---

### Post by sandyd on 2009-10-04
you don't need to.

just connect your computer into the network with a ethernet cable (or wireless)

you will only need to connect it to the domain if there are special shared folders on the server that you need to access

in that case,
```

sudo apt-get install system-config-samba samba
sudo system-config-samba

```
Then
Prefrences -> Server Settings
enter the name of the domain in as the workgroup.

Then, just open the network icon in ubuntu and you should see al the computers.

find the server and your done.

however, this does not work with a windows server 2003 R2 feature. The feature gives each user their own private storage drive.

---

