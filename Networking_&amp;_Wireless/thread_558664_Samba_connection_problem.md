---
title: "Samba connection problem"
date: 2007-09-24
forum: Networking &amp; Wireless
---

### Post by rdnk on 2007-09-24
Hi people.

I've had Ubuntu Server install for a few years now. I'm currently sharing drives into network with Samba. Samba and all the shares are accessible and reading performance is what it should be in 100Mbit ethernet, around ~10Mb/s. However, after running the clean Ubuntu install for a while, Samba connections become unstable. Network drive connections are disconnected when trying to write into the Samba share with these kind of log messages:

```

Sep 24 16:45:46 runonlaulaja smbd[22248]: [2007/09/24 16:45:46, 0] lib/util_sock.c:read_data(529)
Sep 24 16:45:46 runonlaulaja smbd[22248]:   read_data: read failure for 4 bytes to client 192.168.0.250. Error = Connection reset by peer
Sep 24 16:45:46 runonlaulaja smbd[22248]: [2007/09/24 16:45:46, 0] lib/util_sock.c:write_data(557)
Sep 24 16:45:46 runonlaulaja smbd[22248]:   write_data: write failure in writing to client 192.168.0.250. Error Broken pipe
Sep 24 16:45:46 runonlaulaja smbd[22248]: [2007/09/24 16:45:46, 0] lib/util_sock.c:send_smb(765)
Sep 24 16:45:46 runonlaulaja smbd[22248]:   Error writing 75 bytes to client. -1. (Broken pipe)

```

The writing performance is also very low, around 500kB/s. Now I've been searching the internet, but so far I have not been able to locate anyone with similar problems. I would be happy to get some ideas what could be wrong here.

---

### Post by ryawn on 2007-10-28
Bump



I'm having a similar problem; however I'm not even able to view my samba shares on my XP Pro machine. It continuously asks me to reauthenticate on the XP client and produces the :

```
[2007/09/13 16:38:42, 0] lib/util_sock.c:read_data(534)
  read_data: read failure for 4 bytes to client 192.168.1.137. Error = Connection reset by peer
```


in my samba logs. Any ideas?

---

### Post by rdnk on 2007-10-28
I didn't found the problem, however after I reinstalled Windows, the shares are working fine now and the problems are gone. I suspect it had something to do with possibly corrupted Windows installation(?)

---

### Post by ryawn on 2007-10-28
my question was already answered in

[http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+windows+xp](http://ubuntuforums.org/showthread.php?t=202605&highlight=samba+windows+xp)

I love this forum. Good luck finding your answer!

---

### Post by dlmj12 on 2008-06-16
> **rdnk said:**
> Hi people.

I've had Ubuntu Server install for a few years now. I'm currently sharing drives into network with Samba. Samba and all the shares are accessible and reading performance is what it should be in 100Mbit ethernet, around ~10Mb/s. However, after running the clean Ubuntu install for a while, Samba connections become unstable. Network drive connections are disconnected when trying to write into the Samba share with these kind of log messages:

```

Sep 24 16:45:46 runonlaulaja smbd[22248]: [2007/09/24 16:45:46, 0] lib/util_sock.c:read_data(529)
Sep 24 16:45:46 runonlaulaja smbd[22248]:   read_data: read failure for 4 bytes to client 192.168.0.250. Error = Connection reset by peer
Sep 24 16:45:46 runonlaulaja smbd[22248]: [2007/09/24 16:45:46, 0] lib/util_sock.c:write_data(557)
Sep 24 16:45:46 runonlaulaja smbd[22248]:   write_data: write failure in writing to client 192.168.0.250. Error Broken pipe
Sep 24 16:45:46 runonlaulaja smbd[22248]: [2007/09/24 16:45:46, 0] lib/util_sock.c:send_smb(765)
Sep 24 16:45:46 runonlaulaja smbd[22248]:   Error writing 75 bytes to client. -1. (Broken pipe)

```

The writing performance is also very low, around 500kB/s. Now I've been searching the internet, but so far I have not been able to locate anyone with similar problems. I would be happy to get some ideas what could be wrong here.
Did you ever find a resolution for this? We have 90 servers at various sites and are struggling to find an answer to this problem.

---

