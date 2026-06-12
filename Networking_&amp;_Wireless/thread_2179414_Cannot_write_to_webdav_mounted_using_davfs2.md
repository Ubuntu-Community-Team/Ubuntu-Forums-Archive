---
title: "Cannot write to webdav mounted using davfs2"
date: 2013-10-08
forum: Networking &amp; Wireless
---

### Post by Rich_Stanton on 2013-10-08
I have a webdav mounted directory on ubuntu. It's worked fine for years. Recently I updated to Ubuntu 12.04 LTS (davfs2 1.4.5), and since then the webdav share hasn't worked. It's mounted in fstab as: 


[https://shared.xxx.uk/xxx/](https://shared.xxx.uk/xxx/) /mnt/SDrive davfs defaults 0 0 

I have my username/password in /etc/davfs2/secrets. The webdav share works fine when mounted from windows.

When I mount it in ubuntu, it appears to mount fine, and I can browse it readily. syslog shows: 
/sbin/mount.davfs [https://shared.xxx.uk/xxx/](https://shared.xxx.uk/xxx/) /mnt/SDrive/ -o rw 

But I cannot write to it. When I try, it just hangs. After leaving it for a while, I normally end up using kill -9 to kill the davfs process. I turned up logging, and posted on the developers website. They couldn't reproduce the bug on debian, and suggested I post over here. They said:


[LIST]
[*]after you issued the command to create the file davfs2 checks (with HEAD) whether a file like this already exixtx (no) and creates a new file node.
[*]davfs2 now tries to lock that filename on the server. To do this the Neon library has to send a LOCK-request. Before doing so it will close the connection to create a new one for this request (because the request is nonidempotent).
[*]but when neon tries to close the connection it hangs. The log messages are "req: Closing connection for non-idempotent request." and "sess: Closing connection.". The next message would be "sess: Connection closed.", but this message never appears. This is probably when the file system hung and you waited several minutes before killing the process.
[/LIST]


Any suggestions?

---

### Post by Rich_Stanton on 2013-10-11
Bump?

---

