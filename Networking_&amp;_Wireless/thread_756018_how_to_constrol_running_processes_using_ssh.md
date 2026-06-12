---
title: "how to constrol running processes using ssh"
date: 2008-04-15
forum: Networking &amp; Wireless
---

### Post by residentevil on 2008-04-15
I want to ask you how to control processes that are already running. Example:
user ren listen to misuc using amarok and user asd is logged in the ssh server, how user asd can start/stop.... amarok(asd has root password), and can i start kget or ktorrent to download and when i logout ssh from ssh sever ktorrent countinues to downloading.
sorry for mu awful english.

---

### Post by chili555 on 2008-04-15
You can stop a process with:```
killall amarok
```The *at* command will start or stop any process at a given time. Learn about it with:```
man at
```To start a process and have it keep running after you close ssh, add the & symbol:```
amarok &
```Amarok is a bad example, because you need to see the user interface to know what song to play. You can, however, forward user interfaces across ssh with the -X command:```
ssh -X -l chili 192.168.1.101
```Torrents are easy:```
ktorrent your_file.torrent &
```I would probably use rtorrent and wget instead, since they do not require a graphical user interface.

Post back if you need more help. Your English is plenty good enough.

---

