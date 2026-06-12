---
title: "ssh: connect to host xxx.xxx.xxx port 22: Connection timed out"
date: 2015-10-15
forum: Networking &amp; Wireless
---

### Post by cybermecano on 2015-10-15
Hi,

I am facing which appears to me to be a weird problem. Actually, I am trying to access a remote server from my local machine through ssh and it worked well for me at the very first time so I succeeded one single file transfer from my local to the remote then I couldn't transfer a second file and all my attempts to connect to the server returned with:

```
ssh: connect to host xxxxxxxx port 22: Connection timed out
```

I tried hard to resolve this and I ended up by configuring a NAT port triggering for the port 22 on my router configuration panel as shown in the screenshot attached. Thus, I succeeded to connect again to the remote and to transfer a couple of files before I get the same problem again...

Now I'm running over ideas and I almost give up !

---

### Post by Hadaka on 2015-10-15
Hi, if you are copying you should get a  SCP error if there is a problem not a SSH message,
check here for a possible solution,
[https://help.ubuntu.com/community/SSH/TransferFiles](https://help.ubuntu.com/community/SSH/TransferFiles)
thanks

---

### Post by cybermecano on 2015-10-16
Hi,

Thank you for your reply Hadaka. However, it happens that I get:

```
ssh: connect to host remote.server.org port 22: Connection timed out
lost connection
```

even with:

```
scp local_file user@remote.server.org:/destination/path
```

Weird, isn't it ?

---

### Post by Hadaka on 2015-10-16
if you did one of 2 things you may have locked up the remote, if you first..
```
ssh user@remote.server.org
scp local_file user@remote.server.org:/destination/path
```
or just,,
```
ssh local_file user@remote.server.org:/destination/path
```
can you ping the remote server router?
Exmple:
```
ping -c3 93.21.5.0
```
if so, the remote computer is clutching its little chest and needs cpr
(computer power reset)

---

### Post by papibe on 2015-10-16
Hi cybermecano.

For what I can read on your screenshot, 'Port Triggering' is not what you need. That looks like a simplified version of UPnP, except only for port number management.

You need either proper **'Port Forwarding'**: public port number to same port number in a LAN machine, or **'Virtual Servers'**: public port number to different port number in a LAN machine.

Hope it helps. Let us know if that helps.
Regards.

---

### Post by cybermecano on 2015-10-17
Hi,

Hadaka, you're right. Connection is timed out because I both connect via ssh and copy using scp simultaneously !

I am now using sftp via FileZilla which is more efficient and handy.

Thanks everybody.

Cheers

---

### Post by Hadaka on 2015-10-17
Great, glad you figured it out !

---

