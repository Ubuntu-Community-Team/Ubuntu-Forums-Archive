---
title: "ssh listening on wrong adapter"
date: 2008-10-15
forum: Networking &amp; Wireless
---

### Post by lsutiger on 2008-10-15
I am having a problem with ssh.
I believe it is listening on the wrong adapter.
I had eth0 which is not active and wlan0 which is active.
output of /usr/sbin/sshd -d```
debug1: sshd version OpenSSH_4.7p1 Debian-8ubuntu1.2
debug1: read PEM private key done: type RSA
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: private host key: #0 type 1 RSA
debug1: read PEM private key done: type DSA
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: private host key: #1 type 2 DSA
debug1: rexec_argv[0]='/usr/sbin/sshd'
debug1: rexec_argv[1]='-d'
debug1: Bind to port 5970 on 0.0.0.0.
Bind to port 5970 on 0.0.0.0 failed: Address already in use.
socket: Address family not supported by protocol
Cannot bind any address.

```

output of  sudo netstat -tulpn```
tcp        0      0 0.0.0.0:5970            0.0.0.0:*               LISTEN      5586/sshd 
```

how do I change this?

---

### Post by nixscripter on 2008-10-15
The problem appears to be not in the adapter, but that some other process is already listening on port 22.

Make sure you stop the sshd service first if you want to run it manually:

```
sudo /etc/init.d/ssh stop
```

---

### Post by lsutiger on 2008-10-15
I have ssh configuration set to listen to port 5970.

---

### Post by nixscripter on 2008-10-15
Whoops, minor jump to conclusion on my part. But the error message still refers to another process already listening on port 5970 with the "address" of 0.0.0.0 (connect to anyone).

That netstat command has identified the target process (job id 5586) as an already running sshd instance. Stop the service as I suggested, or if that doesn't do it, just **kill** the process (and wait a while for the socket to close).

---

### Post by lsutiger on 2008-10-15
Thanx for the input. I stopped the ssh service, ran netstat and it was not listed.
I restarted the service, and I am still getting:
```
Active Internet connections (only servers)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name
tcp        0      0 127.0.0.1:3306          0.0.0.0:*               LISTEN      5349/mysqld     
tcp        0      0 0.0.0.0:139             0.0.0.0:*               LISTEN      5536/smbd       
tcp        0      0 127.0.0.1:783           0.0.0.0:*               LISTEN      5414/spamd.pid  
tcp        0      0 0.0.0.0:5970            0.0.0.0:*               LISTEN      5892/sshd       
tcp        0      0 127.0.0.1:631           0.0.0.0:*               LISTEN      5471/cupsd      
tcp        0      0 0.0.0.0:445             0.0.0.0:*               LISTEN      5536/smbd       

```

---

### Post by lsutiger on 2008-10-15
OK...now I have ssh working, but the netstat command still gives the same output.
I am having a problem on top of ssh though.
I am using NX Nomachine for remote. NX uses ssh for authentication. But from the client to the host, I am getting an "authentication has failed for user <user>", with no details available.

Sooo..I can ssh into the machine but NX fails authentication, but uses ssh for authentication.......](*,)

---

### Post by nixscripter on 2008-10-16
I'm afraid I don't know about Nomachine NX... but the first thing on google was this (sorry if it seems a little obvious):

[http://ubuntuforums.org/showthread.php?t=606150](http://ubuntuforums.org/showthread.php?t=606150)

---

