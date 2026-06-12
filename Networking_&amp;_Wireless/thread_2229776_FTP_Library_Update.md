---
title: "FTP Library Update"
date: 2014-06-15
forum: Networking &amp; Wireless
---

### Post by actionmystique on 2014-06-15
Hello guys,

I've installed **curlftpfs to mount FTP resources on my local Ubuntu Desktop 14.04 system using fstab**:


  ***curlftpfs#user: password@IP: port/ /mount-point  fuse noauto,user,uid=1000,gid=1000,umask=0022,ftp_method=singlecwd 0 0***

  
It works OK, except that the **network performances are extremely poor**. I have been cautious about the options to make sure that only one CWD is  done on the full target directory instead of one CWD per each folder as  described in the man entry (**ftp_method=singlecwd**). That precaution does not solve this issue.


  I have snooped around the network traffic and noticed that **many TCP resets are probably the cause of this problem**. Now I'm trying to locate which **dependency handles IP/TCP traffic** to be able to update it with a more recent version.

  Any suggestion?

---

### Post by actionmystique on 2014-06-16
An example of many TCP resets during a simple folder list:
[ATTACH=CONFIG]253976[/ATTACH]

---

### Post by actionmystique on 2014-06-18
I'd like to compare with another tool, maybe gvfs if it is possible or sshfs.

---

### Post by actionmystique on 2014-06-28
I successfully installed and used sshfs which works much better:
**sshfs -o idmap=user root@ssh-server-ip-address:/ /mount-point**

No TCP resets during the communication...

---

### Post by actionmystique on 2014-06-28
However, I"ve noticed that the TCP window used is only around 3000 bytes: 2 packets on Ethernet before waiting for an acknowledgement.
Does anybody know how to simply change this window size?

---

### Post by actionmystique on 2014-06-28
...only for local traffic, not for connections using the route with the default gateway?

---

### Post by actionmystique on 2014-06-28
Maybe I should launch another thread for this...

---

