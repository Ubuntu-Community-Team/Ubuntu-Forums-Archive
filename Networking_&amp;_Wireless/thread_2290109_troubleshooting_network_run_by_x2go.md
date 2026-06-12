---
title: "troubleshooting network run by x2go"
date: 2015-08-09
forum: Networking &amp; Wireless
---

### Post by tjk on 2015-08-09
I have setup a network that is using x2goserver and x2goclient, with SSH tunneling.  I've had to learn a lot of new things to understand the processes involve with networking.  I've read a lot about network setups and there are many good tutorials online that have helped me.  But there are a number of questions / bugs in my system that I need to work out, and I have been unable to find the answers.

Some are specific to x2go, and others are more general.  For instance, my first question is:
It appears that when I shut down the server remotely, ***the session does not terminate properly***.  Is there something specific that I need to setup on the server so that the client will consider it a "proper" termination, as I get error messages from the client when I try to connect the client to the server. (Let me briefly describe what I do and what happens during this process:  While my client is connected to the server - which is running xfce - I just logout by clicking on the shutdown button. The server desktop disappears from view, but the x2gp window-frame stays open.  The window does not close even after the server has powered-off.  I have to go into x2goclient window and terminate the session manually or close the x2goclient window -- which closed the x2goserver window-title/frame.)

Another question that I have is: ***I have not been able to get file sharing working***, what can I try to troubleshoot this issue?  I'm thinking that this problem has multiple issues, because I know that I need a port open to allow file sharing -- but allowing all incoming (only tried briefly) does not solve this problem.  I'm not clear if file sharing would also use the SSH tunnel.

One last, very annoying and worrysome problem:  ***When terminating a session, about 10% of the time, my client computer will seize***.  No keystrokes will work, so I have to do a hard-boot with the power button.  I'm hoping that this might be related to my first question...

There are a few more questions, but if I get these two problems solved it would solve the majority of my networking issues.

  - Tim

---

### Post by TheFu on 2015-08-10
c) Nothing should cause the client to seize.  I don't think that is an x2go issue.  Look for failing hardware inside the client PC.  What do the system log files show?  You'll need to boot off some other media, mount the normal /var storage and look at the logs, since some of the logs which will show HW issues will be overwritten at boot if you boot the OS that failed.

b) I don't use the built-in file sharing. Just treat the two system like normal physical servers and setup whatever transfers you want between them.  sftp is my favorite - it works over the same ssh port(s) depending on which direction you treat as the "client" and the "server" for ssh. I don't know of any Linux file managers that do not support sftp:// URLs.  Of course, the "server" side of the sftp connection must be running openssh-server already.  There are nice sftp clients for Windows.

a) x2go is funny.  Just because there are 2 Windows, doesn't mean there are 2 separate processes.  If you want to close the remote session - inside the remote sessions, just logout. That should do it.  Then close the smaller window were the remote connection was made on the client side.

---

