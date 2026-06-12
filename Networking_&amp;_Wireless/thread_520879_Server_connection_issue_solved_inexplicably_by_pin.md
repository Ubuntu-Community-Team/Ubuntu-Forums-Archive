---
title: "Server connection issue solved inexplicably by ping out"
date: 2007-08-08
forum: Networking &amp; Wireless
---

### Post by donnoit on 2007-08-08
[This post is NOT related to wireless networking :-)]

I have an Ubuntu 7.04 server in a hosted VMWare instance (the base OS is some other flavor of Linux).

My Ubuntu server is running sshd, proftpd and apache2.  I find that that all 3 kinds of access to this server (ssh, ftp and http) from other machines on the network fail simultaneously from time to time, though ping is still successful to this server.  There is no firewall running and 'netstat -tap' seems to show everything is well (all the servers are listening) and ifconfig does not show any error packets or other obvious abnormality.  I can also still do local ssh and ftp (from the server console to itself), besides a ping to this server from a remote machine.

Not knowing any better, I had been restarting the networking interfaces (/etc/init.d/networking restart) and found that it restored the connectivity to this server in all 3 ways (ssh, ftp, http).  Or, if I wait long enough (some random length of time greater than 15 mins) the ssh/ftp/http connectivity to this server is restored by itself.

More intriguingly, I also discovered that instead of doing a networking restart or waiting around, if I simply do a ping FROM this server TO any other machine on the network, then the ssh/ftp/http connectivity to this server is restored instantly.  

To debug the connectivity issues, I tried to run the sshd in debug mode but found no log info when external access is attempted.

Would appreciate any ideas to explain how a ping out could restore incoming TCP connectivity (via ssh/ftp/http), or how to debug this connectivity issue.

---

