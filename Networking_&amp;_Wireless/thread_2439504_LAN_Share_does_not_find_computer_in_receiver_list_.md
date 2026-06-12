---
title: "LAN Share does not find computer in receiver list 18.04LTS"
date: 2020-03-28
forum: Networking &amp; Wireless
---

### Post by pickelhaupt on 2020-03-28
I've recently bought a new laptop and had the intention of using LAN Share [https://github.com/abdularis/LAN-Share](https://github.com/abdularis/LAN-Share) to transfer files from my old laptop to the new. Both computers run Ubuntu 18.04 LTS.
LAN Share is installed on both machines and they are connected to my home wifi. 

The problem is that neither computer find each other in the "Receiver list" in the LAN Share app. I can't find any issues and solutions connected to this. Any thoughts?

---

### Post by TheFu on 2020-03-28
Backup the data using your normal backup method.
Restore the data using your normal restore method.

When else will you have such a good chance to test those methods AND your knowledge of them when it isn't really important or time sensitive?

But since that probably isn't your plan and we couldn't convince you that it should be, the really the easiest way to transfer data between systems is to use rsync or grsync.  Setup ssh between the systems first.  Run:
```
sudo apt install ssh fail2ban rsync
```
on both systems.
Then, look up the ip address for one and go to the other.  rsync can push or pull data, just change the source and the targets depending on which machine has the data currently.
To copy everything from the other system to your current HOME, use:
```
rsync -avz remote-ip:~/userid/  ~/
```
this assumes the usernames on both systems are the same. it will make a subdir with the username, /home/username/username/ and you can move any directories/files down 1-level as you desire.

---

