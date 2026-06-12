---
title: "How do I use NFS?"
date: 2006-08-26
forum: Networking &amp; Wireless
---

### Post by Lorian on 2006-08-26
I have searched the forums and not found anything particularly helpful, and the wiki entry just confused me.

Ok, so I have my main computer (192.168.1.100) and my computer in my room (192.168.1.104). I want to be able to access my Music folder, which is located at /home/chris/Music on the main PC, at the same location on the computer in my room. I have used the shared folders thing to share it with NFS, but I have no idea how to connect to it from my PC.

Cheers.

---

### Post by v1ct0r on 2006-08-26
Maybe this :  [http://ubuntuguide.org/wiki/Dapper#How_to_share_folders_the_easy_way](http://ubuntuguide.org/wiki/Dapper#How_to_share_folders_the_easy_way)


Samba is a good choice too [in an internal network]:
[http://www.ubuntutorial.com/?p=5](http://www.ubuntutorial.com/?p=5)

ps. A very complete NFS-linux guide here [http://www.linux.com/howtos/NFS-HOWTO/](http://www.linux.com/howtos/NFS-HOWTO/)

---

### Post by Smokeless on 2006-08-26
I've no seen many references to Samba as an alternative to NFS.  Yes, it is if you wish to share with Windoze systems.  But -- and correct me if I'm wrong -- if you wish to retain Unix permissions and other Unix-specific file properties, NFS is the better choice.  

However, there are several gotcha's when using NFS.  (1) Permissions.  I always forget this -- or more accurately, I forget some of the subtler points when moving among different DHCP servers with different network IP's -- make sure your hosts.allow is set up correctly!  ](*,)   (2) UIDs and GIDs.  Make sure that users and groups share the same ID's on both systems.  Otherwise, files on the remote directories will appear to have ID's but no users!  Using NIS/YP is one way to accomplish this.  If there are few users, just make sure you assign the same UID's and GID's.

Here's another URL for the same HOW-TO, without the advertising, keyed to specifics of mounting remote drives.

[http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#REMOTEMOUNT](http://www.faqs.org/docs/Linux-HOWTO/NFS-HOWTO.html#REMOTEMOUNT)

Enjoy. :-\"

---

