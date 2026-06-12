---
title: "ftp localuser@localhost login problem"
date: 2008-10-09
forum: Networking &amp; Wireless
---

### Post by tuathan on 2008-10-09
I am using a program that requires you to login in to ftp with command: 

```
ftp username@ftpserverip
```

I have set up my local machine as a ftp server and can connect to it fine like this:

```
ftp localftpserverip
```

```
 ~$ ftp *.*.*.*
Connected to *.*.*.*
220 (vsFTPd 2.0.6)
Name (*.*.*.*:*******): *******
331 Please specify the password.
Password:
230 Login successful.
Remote system type is UNIX.
Using binary mode to transfer files.
ftp> 
```

when i try this however:

```
ftp localuser@localftpserverip
```

it doesn't work:

```
ftp *******@**.*.*.*
ftp: *******@**.*.*.*: Unknown host
ftp> ls
Not connected.
ftp>
```

how can i fix this?

---

