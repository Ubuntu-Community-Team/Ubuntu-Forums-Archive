---
title: "strange open ports"
date: 2007-01-15
forum: Networking &amp; Wireless
---

### Post by corax on 2007-01-15
Hi everyone !

I have a little question but I cant find the answer anywhere. I scanned through this forum and the whole internet :-) here is the problem:

if i run :
```
sudo nc -z -v -w 1 127.0.0.1 1-65535
```

i get this :
```
localhost [127.0.0.1] 55081 (?) open
localhost [127.0.0.1] 42712 (?) open
localhost [127.0.0.1] 2049 (nfs) open
localhost [127.0.0.1] 767 (?) open
localhost [127.0.0.1] 445 (microsoft-ds) open
localhost [127.0.0.1] 139 (netbios-ssn) open
localhost [127.0.0.1] 111 (sunrpc) open
localhost [127.0.0.1] 22 (ssh) open
```

if i run this:
```
sudo netstat -natp
```

i get this:
```
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0               0.0.0.0:2049          0.0.0.0:*                        LISTEN     -                   
tcp        0      0               0.0.0.0:55081        0.0.0.0:*                       LISTEN     4518/rpc.statd      
tcp        0      0               0.0.0.0:139             0.0.0.0:*                       LISTEN     4441/smbd           
tcp        0      0               0.0.0.0:111             0.0.0.0:*                       LISTEN     3523/portmap        
tcp        0      0               0.0.0.0:42712        0.0.0.0:*                       LISTEN     -                   
tcp        0      0               0.0.0.0:445             0.0.0.0:*                       LISTEN     4441/smbd           
tcp        0      0               0.0.0.0:767             0.0.0.0:*                       LISTEN     4404/rpc.mountd     
tcp6      0      0               :::22                         :::*                                 LISTEN     4462/sshd 
```

I figured out most of them (it wasn't hard i can read :-) ) but i still don't know what does port 42712 does (as i scanned it many times it is not a constant port it is hopping at least every time i restart/start my machine and maybe during use :-)  ). So don't focus on the port but focus on the program using it :-). How can i get the name of the program or PID ...
When i stop samba and nfs sometimes it (currently 42712) disappears. 
(And the following ports always disappear : 767, 445, 139, 2049. Because they are the samba and nfs ports.)

The other one is port 55081 it says rpc.statd. It is also hopping, every time I start my machine it is different.  What is this port ? :-)

Thanks for the answers and please forgive me for my English ;-)

---

### Post by scrooge_74 on 2007-01-15
Are you using any Firewall config utility like Firestarter?

ARe you using some game that need those ports?

---

### Post by corax on 2007-01-16
Hi Scrooge !

No, I don't use firewall I installed some games from the repository but I haven't started single one of them :-) I closed all the services (Samba, NFS, CUPS, ...) I know except ssh and portmap. Thanks for the quick reply !

I scanned today the results are :
```

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0            0         0.0.0.0:36228           0.0.0.0:*               LISTEN     4499/rpc.statd      
tcp        0            0         0.0.0.0:111                0.0.0.0:*               LISTEN     3497/portmap          
tcp6      0            0         :::22                           :::*                         LISTEN     4443/sshd           

```

As you see rpc.statd changed port randomly, yesterday it was on port 55081. If it were a game port shouldn't it remain static so the clients can join, or at least stay in a little range for example 29000-29008 ? But this port is jumping like a kangaroo. :-)

Anyway have you made a portscan on your machine ? Don't you have a port like this ?

Thanks, corax

---

### Post by corax on 2007-01-16
Hi,

It's me again I have found it. I' m sorry I was too tired yesterday I found the process it is a network monitor for nfs i can disable it if I stop nfs-common.  ](*,) Sorry to bother the forum with this. I feel like a spammer but maybe these information will be useful for someone. 

Thanks, and sorry :-)

---

