---
title: "Special Reverse SSH - VNC?"
date: 2008-06-04
forum: Networking &amp; Wireless
---

### Post by Skerit on 2008-06-04
I've got quite a situation:

At one place, I have a computer (Computer A - Windows XP) behind a regular squid proxy. Most ports are closed, except the ssl one, 443 (And regular ports for surfing, of course)

At home I configured my router to forward port 443 to my main computer, Computer B - Ubuntu Hardy, to the port my SSH server is listening on.

I have no problems establishing an SSH connection from Computer A to Computer B.

I know I can not create a link FROM computer B to A but:

When I initiate an SSH session from computer A to B isn't there some way I can create a tunnel which will grant me access on computer A from Computer B? (So, using the connection established on A)

I've created several tunnels, forwarding B's 5900 port to A's 5900, which makes me able to use VNC at computer A to watch computer B's screen, but I can't seem to get the reverse to work.

I tried setting up a "remote" tunnel instead of a local one, but it didn't work.

---

### Post by kevdog on 2008-06-04
So lets just draw this out

 
Computer (A) <------> Squid Proxy (port 443) <--Internet-->Home Router <---> Computer (B)

Really what your goal is to be able to make a connection from B-A, although you know you can go from A->B.  So B at a minimum must be running the openssh server and A the client.  


Assmuming B is running the openssh server over port 22

At computer A
ssh -q -N -R <remote_port>:localhost:22 <Computer B IP_Addess>


At computer B
ssh -p <remote_port> localhost

Try first if we can get the ssh part working, and then we will add vnc ontop of ssh.

---

### Post by Skerit on 2008-06-04
Not quite, the squid proxy is running on port 8080, the only open port is 443, through which I'm sending SSH to my home router, which forwards port 443 to my computer (B) at port 22.

I'm not running any SSH server on computer A, though. It's windows, after all! I can use SSH from cygwin, but oterwise I'm using putty.

Btw: I'm always getting an error regarding the remote port forward, which could be the cause of this all: 

Warning: remote port forwarding failed for listen port 5900 (or any port, really)

---

### Post by kevdog on 2008-06-04
You only need the ssh server on computer B

Ok, Im still a little confused.

If you are sitting at work on Computer A, how do you ssh to Computer B?

---

### Post by Skerit on 2008-06-05
I was using putty, which worked like a charm, except for setting up reverse tunnels. 

This is proof a CLI is, yet again, handier then a GUI application! 

I'm using this to get VNC on my home computer:

ssh -N -R 3701:localhost:5900 home.ip -l login

Now, I need it to reconnect after a disconnect..

---

