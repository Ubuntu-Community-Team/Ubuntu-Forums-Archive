---
title: "uploading files and directories"
date: 2008-11-17
forum: Networking &amp; Wireless
---

### Post by Red-Shield on 2008-11-17
can any one out there help me find a way to upload i want to send my secretary a file or folder in the mornings of things i want here to do for me for the day i want to do this in a terminal i use SSH and SCP and SFTP all the time to get files and directory's but i want to send them to her desktop can any one help?????

---

### Post by sirjoebob on 2008-11-17
Found [this site]("http://www.felixgers.de/teaching/internet/rpc.html") about rcp (remote copy):

rcp (remote copy), scp (secure copy):
These two commands copy files from one machine
to another using a similar notation to cp.
scp is the secure version from the ssh package.

rcp [-r] [uesr@host1:]file1 [user@host2:]file2

scp [-r] [[user@]host1:]file1 [...] [[user@]host2:]fil

I have never used this but believe this is how you would achieve this goal.

---

