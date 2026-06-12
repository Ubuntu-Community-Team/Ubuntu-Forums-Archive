---
title: "Xterm remote issues"
date: 2007-03-15
forum: Networking &amp; Wireless
---

### Post by spiritflare on 2007-03-15
hello

I'm trying to display an xterm from my redhat server onto my Ubuntu desktop.. 

when i test it to a windowz box running Exceed, it works, but not to the Ubuntu. 

On the redhat server (mq), i have:

setenv DISPLAY ubuntu:0.0; export DISPLAY
xhost +
xterm &

But ont he Ubuntu, i see this:

"Warning: Tried to connect to session manager, Authentication Rejected,
reason : None of the authentication protocols specified are supported
and host-based authentication failed"

I typed "xhost +" on my Ubuntu, and I also tried to put the hostname of the Redhat server in my .rhosts file - neither helps.

When I use the IP of the windows pc running Exceed, it works.

Not sure what I am missing... any advice would be appreciated

tx

~k

---

### Post by netztier on 2007-03-15
> **spiritflare said:**
> 
setenv DISPLAY ubuntu:0.0; export DISPLAY
xhost +
xterm &

But ont he Ubuntu, i see this:

"Warning: Tried to connect to session manager, Authentication Rejected,
reason : None of the authentication protocols specified are supported
and host-based authentication failed"


If you do it like that, you do "classical" X over tcp/6000. This is the "native" but IMHO "old" and insecure way, and firewall admins don't really like it either. The error message you show says something about authentication - I can't tell what this actually means. I'd also have to investigate to find out where exactly the option/restriction intervenes to stop incoming X connections. xhost+ is one thing,  hosts.allow and hosts.deny is something else to think of - I don't even know if they are being used with X.org/X11. 

But here's a **workaround** that might help:

Can you **ssh** into the remote box? Does the remote ssh server allow X11 forwarding? Check **/etc/ssh/sshd_config** (or whatever configuration file the sshd on the remote system uses) if the option "X11Forwarding" is set to "yes". If not, enable, uncomment or add the line
```
X11Forwarding yes
```
and restart the ssh server.

Then start the ssh connection with the -X option: **ssh -X <remote host>**. This will configure the $DISPLAY variable on the remote system to use the existing SSH connection as output - and your local system will see a new X client connecting from "localhost" to the local X server, instead of the remote IP address. Most probably, this connection will not be considered "dangerous" and therefore won't be subject to stiff authentication mechanisms - and will terefore probably work.

best regards

Marc

---

### Post by spiritflare on 2007-03-15
Marc

Thank-you - worked perfectly.   Much appreciated.

rgds

~k

---

