---
title: "I can't get SSH tunnel (socks 5 proxy) to work, even though I am connecting over SSH."
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by xamox on 2007-09-10
I am using:
ssh -D 8000 [email]remoteuser@my.machines.ip.addr[/email]ess -p 1234

now I'm using 1234 on the remote machine via port forwarding done by the router (my server running SSH is behind this router).  The SSH server machine runs on standard port 22.  I am able to SSH in remotely, but my problem is that when I go into firefox and setup my proxy settings to:
localhost 8000

and then I try to visit any sites the page is just blank.

If I add -v for verbose to the ssh command it says ports are forwarding and get a bind.  So I am unsure of why it isn't working. I am using SOCKSv5 to connect to it.

I am connecting from a Macbook G4 running Ubuntu 6.06 (dapper drake) and using Firefox 1.5. The remote server is running Ubuntu 7.04 (fiesty fawn) and the latest version of SSH server in the repositories.

Also I am smart enough to know not to close the terminal window and that the SSH connection has to stay live. So any ideas why this might be occuring?

---

### Post by crazy.forky on 2007-11-01
Yes, maybe you are very smart but still had a mistake ^^
I think you are only able to use **localhost** for setting up your proxy when you have installed a web server (such as Apache or anything like that ^^). 
So until you've done that, you can only use your local IP address (I mean **127.0.0.1**) to setup your proxy. Your OS without a web server will not understand what is localhost, it just only knows **127.0.0.1**.
Hope this will help and good luck to you.

---

### Post by xamox on 2007-11-01
That actually could very well have been the problem.  Sadly now my server has died so I'm kind of SOL, but I will keep that in mind for the future.

---

