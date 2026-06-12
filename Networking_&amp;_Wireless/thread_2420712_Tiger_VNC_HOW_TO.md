---
title: "Tiger VNC HOW TO?"
date: 2019-06-09
forum: Networking &amp; Wireless
---

### Post by aughey on 2019-06-09
Teamviewer for reasons best known to itself treats me as a commercial user so I can no longer use it. Someone recommended Tiger VNC instead. I need to connect from my laptop to an Imac. The laptop is dual boot running Ubuntu 19.04 on one partition and Windows 10 pro on the other. I am a total newbie to Tiger VNC so have no clue how to do this properly and get it to work. Any advice would be greatly appreciated

---

### Post by TheFu on 2019-06-10
Waited a day to respond hoping someone else would.

I can't help with remote connections into Windows or TigerVNC.  

I vaguely remember trying to get it working 18+ months ago and failing. Normally, I use remote X/Windows for local windows running on LAN systems and for full remote desktops, I use x2go from anywhere in the world.  The real issue is that x2go-server only runs on Linux systems, though clients work for Windows and Linux and OSX.  As for X/Windows, that is a client-server architecture with the server running local and the X-client being remote. There are good commercial X/Servers for Windows. I've used some, but I don't know about any programs on Windows that include X-client libraries.  I haven't a clue about OSX on that.

I'm fairly certain that OSX has an ssh server, so you can always use ssh clients to remote in.  95% of my remote work is over ssh. Don't know if that will work for you or not. Just an option.

ssh is enough for

    secure remote access to files via sftp
    secure remote filesystem access via sshfs
    secure remote CLI/shell access to systems with plain ssh
    secure remote desktops via x2go/freenx
    secure remote file replication with rsync (ssh is the default rsync protocol)
    secure port forwarding of selected ports
    secure remote editing with vim/gvim and other editors
    pseudo-VPN with sshuttle <&#8212; this may be helpful.

[http://matt.might.net/articles/ssh-hacks/](http://matt.might.net/articles/ssh-hacks/) and [http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html](http://blogs.perl.org/users/smylers/2011/08/ssh-productivity-tips.html) have more on ssh.

---

