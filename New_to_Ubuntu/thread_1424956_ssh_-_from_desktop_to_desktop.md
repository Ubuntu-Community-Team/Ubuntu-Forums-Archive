---
title: "ssh - from desktop to desktop"
date: 2010-03-08
forum: New to Ubuntu
---

### Post by 0bliterator on 2010-03-08
I'd like to connect from one Ubuntu desktop to another using ssh.  What configuration needs to be done on the remote machine?  It is currently refusing connections.  Is this a hosts file issue? Could someone point me in the right direction?  VNC works...  I'm relatively new to Ubuntu.

Any assistance would be appreciated.

Obliterator
Network Engineer

---

### Post by Neezer on 2010-03-08
how are you trying to connect? in terminal? is openssh-server installed on the host computer? Are you using any kind of protection, password or rsa key?

Here is a great guide to ssh
[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

and

[https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/9.04/serverguide/C/openssh-server.html)

Good luck, and post any questions you may have along the way.

---

### Post by r-senior on 2010-03-08
If openssh-server is already installed and running, /var/log/auth.log might provide some clues as to what is going wrong?

---

### Post by 0bliterator on 2010-03-08
Thanks for the speedy replies!  I've been able to login from desktop to desktop using ssh.  I can login to a server beyond again with ssh.  

Now, how do I pass the -X parameter through the second desktop.  From desktop2, I can ssh -X username@server and then run the command startkde.  This invokes the server gui on the desktop.  I want to be able to ssh from desktop1 through desktop2 to the server and invoke the server GUI on desktop1.  To do this, I need to forward the -X parameters - how?

0bliterator

---

### Post by 0bliterator on 2010-03-08
I was able to modify the ssh_config file.  Remove the # for the entry ForwardX11 and change no to yes - save the file.  Start and stop the ssh service.  It works!  I can invoke the server gui on the 1st desktop using ssh.

Resolved...

0bliterator  :D

---

### Post by Iowan on 2010-03-08
I'm not fond of canned responses, but here goes, anyway...
[[SOLVED]]("https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads")?

---

