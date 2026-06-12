---
title: "open port without a process linked to it, and bad TCP reclen"
date: 2008-06-12
forum: Networking &amp; Wireless
---

### Post by dbeaart on 2008-06-12
Hi,

When I just did a netstat -tap on my system, I got the following output : 
```

Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 *:54587                 *:*                     LISTEN     -                   

```
Normally, the last column would include the process which listens on this port.
I tried to locate what it was, but I'm not able to find it.

When I telnet from a remote machine to this port, I get a terminal, and I get disconnected when I type something.

When I did a tail /var/log/syslog, I found this : 
```

Jun 12 19:18:51 Hostname kernel: [1014373.619361] RPC: bad TCP reclen 0x4d4f5620 (non-terminal)
<etc>

```
for every time I did a telnet to that port, and entered some random txt.

I'm not sure what conclusions I should be making of this. Can someone please help me understand this issue ? 

When I did a google-search on the "RPC: bad TCP reclen"-string, I found some pages about NFS. The server is connected to a NFS server, although this is on the internet network of the server, and not on the public side.

It feels very bad to me that there is a port open to the whole wold, with direct access to the kernel (I'm not sure it is like that, but I guess it is).

Thank you for your time & advice

---

### Post by dbeaart on 2008-06-16
No one any idea ?

I don't really know what to do next. I don't think the server is hacked, so a reinstall would be a bit stupid. I'd like to learn what the problem is, and how it happened, and how I can fix it.
Also, I have no idea what the implications of this open port are. 

Does this mean someone can give the kernel direct commands ? And if so, what does it mean?

Really hoping on some bright ideas here...

---

### Post by phylae on 2011-04-02
I know this is a super old thread, but I'm seeing the exact same behaviour on my Ubuntu 8.04 server.

```

$ nc -z -v -w1 127.0.0.1 12345
localhost [127.0.0.1] 12345 (?) open
$ netstat -tulpn | grep 12345
tcp        0      0 0.0.0.0:12345           0.0.0.0:*               LISTEN      -               
$ lsof -i | grep 12345
# Returns nothing

```

When I run the same ```
nc
``` command from another box on the same network, the port also shows as open. All of the above commands were run as root.

---

### Post by dbeaart on 2011-04-04
Do you also have an NFS server running? 

Viva la super old threads!

---

### Post by phylae on 2011-04-04
> **dbeaart said:**
> Do you also have an NFS server running? 

I think so. I set up samba, and I'm guess that turned on NFS.

```

$ pgrep -fl nfs
6025 nfsd4
6026 nfsd
6027 nfsd
6028 nfsd
6029 nfsd
6030 nfsd
6031 nfsd
6032 nfsd
6033 nfsd

$ pgrep -fl smb
6054 /usr/sbin/smbd -D
6070 /usr/sbin/smbd -D
29117 /usr/sbin/smbd -D
29910 /usr/sbin/smbd -D

```

So if this is NFS, why would lsof and netstat not be able to figure that out and give me a PID?

---

