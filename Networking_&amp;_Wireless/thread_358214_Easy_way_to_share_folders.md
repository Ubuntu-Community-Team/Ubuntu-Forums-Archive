---
title: "Easy way to share folders?"
date: 2007-02-10
forum: Networking &amp; Wireless
---

### Post by erissiva on 2007-02-10
I am now frustrated.

I installed Xubuntu 6.10 a while ago and everything has been working perfectly. I finally convinced my roomate to switch and he's now running Ubuntu 6.10. Now he has a whole drive of our music, and I have a whole drive of our movies.

Now, I've searched around the forums for help, and keep running into these difficult setups. I don't want that. I want simple. All I need is to share 1 folder with everyone on our network and he needs to do the same.

Here's our setup:
Both computers are connected to a WRT54G wireless router. Everything is working fine...no network problems. We had a similar share set up when we were running XP.

Wireless router ip: 192.168.1.1
My IP                 : 192.168.1.230
His IP                 : 192.168.1.231

All I need is share Xubuntu to Ubuntu, and over a local network.

Is this possible to do without going crazy? It seems like such a simple task. Thanks in advance for any help I can get! :)

---

### Post by bionnaki on 2007-02-10
[http://ubuntuforums.org/showthread.php?t=202605&highlight=howto+smb+kde](http://ubuntuforums.org/showthread.php?t=202605&highlight=howto+smb+kde)

---

### Post by erissiva on 2007-02-11
Ok, I have samba working and a folder shared with both NFS and SMB. My roomate has one shared as well (same way). He has no problems viewing mine from his Ubuntu Network browser. So, I tried to viewing his from Firefox and it works without passwords or anything. 

However, when I try to mount the directory to a folder, I get "Permission denied". He has the folder set to 777. As far as we know, my username has no password on his network.

I tried following the directions here:
[http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing](http://czarism.com/easy-peasy-ubuntu-linux-nfs-file-sharing)

Still same problems. Permission denied.
I don't get it. It works by just going to the address in firefox (smb://), but I can't get it to work anywhere else. Is there any easy way to browse the network on Xubuntu? Or an app I can download and install?
v.v

---

