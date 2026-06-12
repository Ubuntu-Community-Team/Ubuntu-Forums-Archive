---
title: "FTP Client for connecting to Windows Server"
date: 2013-11-11
forum: Networking &amp; Wireless
---

### Post by titan21 on 2013-11-11
Hi,

I am using Filezilla to connect to an FTP site which works fine. Teh issue comes along when I try and change permissions on these files as I get the following error message:

```
500 'SITE CHMOD 644 someimage.png': command not understood
```

Can anyone point me in the right direction of an FTP client that supports Windoze commands. I would have thought FileZilla would have supported this so it may be a configuration issue in which case I still need help!

Thanks in advance.

Tim

---

### Post by TheFu on 2013-11-11
chmod is not a Windows command.  After re-reading the OP, it seems the client is Linux and the server is Windows, so chmod would be sent to the server.  

Running inside the Linux FTP client, ```

ftp> help chmod
chmod           change file permissions of remote file
```

To see the help on the remote system, use
```
ftp> help rhelp
rhelp           get help from remote server
```

Or am I misunderstanding completely?  Hope this helps.

---

