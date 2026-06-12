---
title: "Can anyone point me to instructions for setting NFS over TCP?"
date: 2007-12-17
forum: Networking &amp; Wireless
---

### Post by williammanda on 2007-12-17
Can anyone point me to instructions for setting NFS over TCP? Right now I'm setup with NFS over UDP. I used this link to originally set it up:
[http://ubuntuforums.org/showthread.php?t=249889](http://ubuntuforums.org/showthread.php?t=249889)
Thanks

---

### Post by williammanda on 2007-12-18
Is the default for gusty nfs udp or tcp?
Thanks

---

### Post by williammanda on 2007-12-18
This is info from man for fstab:

**Version 3 is the default protocol version for the nfs file system type when nfsvers= is not specified on  the  mount  command  and both client and server support it.**

I don't specify any version so I would think I'm using nfs version 3. This is the next bit of info from man fstab:
[B]
Here is an example from an /etc/fstab file for an NFSv3 mount over TCP.
server:/usr/local/pub    /pub   nfs    rsize=32768,wsize=32768,timeo=14,intr[/B]

Based on that info, I don't have to add "tcp" since it is default. Is this correct? How can I verify nfs version 3 is using tcp?
Thanks

---

### Post by williammanda on 2007-12-19
Bump!

---

### Post by netztier on 2007-12-19
> **williammanda said:**
> This is info from man for fstab:

**Version 3 is the default protocol version for the nfs file system type when nfsvers= is not specified on  the  mount  command  and both client and server support it.**

I don't specify any version so I would think I'm using nfs version 3. This is the next bit of info from man fstab:
[B]
Here is an example from an /etc/fstab file for an NFSv3 mount over TCP.
server:/usr/local/pub    /pub   nfs    rsize=32768,wsize=32768,timeo=14,intr[/B]

Based on that info, I don't have to add "tcp" since it is default. Is this correct? How can I verify nfs version 3 is using tcp?
Thanks

As far as I know, NFS on Linux is v3 by default. NFSv3 defaults to UDP, but on Ubuntu, TCP support is available on both NFS server and NFS client. Hence you have to specify *proto=tcp* in the mount options in order to have TCP. 

The quick check is to look at the output of **sudo netstat -napt**.
[LIST]
[*] On the *client*, you should see a tcp/2049 connection to the server's ip address in "ESTABLISHED" state once the mount is successful
[*] On the *server*, you should see a socket like this:

```
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                  

```

regardless if a client has done a successful mount or not - like this you know that the server is accepting incoming tcp mount requests. Once a client has done a mount, you should of course also see it's tcp session in "ESTABLISHED" state when you look at netstat -napt. 
[/LIST]

NFSv4 swaps TCP and UDP as defaults, and many v4 servers only support TCP. So I assume that it is no longer needed to specify it explicitely -  provided you have other means to ensure v4 is being used.

I'm not sure which version of **man fstab** you've been looking at, but I can't find these statements in mine (Ubuntu 7.04 server). However, i find them in **man nfs**:

```
Here is an example from an /etc/fstab file for an NFSv2 mount over UDP.

       server:/usr/local/pub    /pub   nfs    rsize=8192,wsize=8192,timeo=14,intr

       Here is an example for an NFSv4 mount over TCP using Kerberos 5 mutual authentication.

       server:/usr/local/pub    /pub   nfs4   proto=tcp,sec=krb5,hard,intr
```


regards

Marc

---

### Post by williammanda on 2007-12-19
This is the output from netstat:

william@AMD:~$ sudo netstat -napt
[sudo] password for william:
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address           Foreign Address         State       PID/Program name   
**tcp        0      0 0.0.0.0:2049            0.0.0.0:*               LISTEN     -                   **
tcp        0      0 0.0.0.0:41772           0.0.0.0:*               LISTEN     3862/rpc.statd      
tcp        0      0 0.0.0.0:58733           0.0.0.0:*               LISTEN     -                   
tcp        0      0 0.0.0.0:6543            0.0.0.0:*               LISTEN     5398/mythbackend    
tcp        0      0 0.0.0.0:111             0.0.0.0:*               LISTEN     3268/portmap        
tcp        0      0 0.0.0.0:6544            0.0.0.0:*               LISTEN     5398/mythbackend    
tcp        0      0 0.0.0.0:39601           0.0.0.0:*               LISTEN     5211/rpc.mountd     
tcp        0      0 0.0.0.0:631             0.0.0.0:*               LISTEN     5097/cupsd          
tcp        0      0 192.168.1.101:54047     192.168.1.100:3306      ESTABLISHED5398/mythbackend    
tcp        0      0 192.168.1.101:60418     64.161.254.20:6667      ESTABLISHED11376/xchat-gnome   
tcp        0      0 192.168.1.101:43633     192.168.1.100:3306      ESTABLISHED5398/mythbackend    
tcp        0      0 192.168.1.101:58285     208.71.169.36:6667      ESTABLISHED11376/xchat-gnome   
tcp        0      0 192.168.1.101:35522     192.168.1.100:6543      ESTABLISHED5398/mythbackend    
**tcp        0      0 192.168.1.101:2049      192.168.1.100:761       ESTABLISHED-                   **
tcp6       0      0 :::631                  :::*                    LISTEN     5097/cupsd          
william@AMD:~$ 

It looks like I have both tcp for server & client since I have both setup. So apparently tcp is default and I have nothing else to do.

I'm using gusty 7.10, which gave me the man info for fstab.
Thanks for your help.

---

