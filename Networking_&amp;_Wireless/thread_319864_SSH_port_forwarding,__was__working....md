---
title: "SSH port forwarding, _was_ working..."
date: 2006-12-16
forum: Networking &amp; Wireless
---

### Post by sptkrishnan on 2006-12-16
Hi,

To start off, I had a working ssh port forwarding in 5.10.  From 6.06 and 6.10, the port forwarding is partially working with the same command line.

Let me explain.  I am using the following syntax to create a tunnel from my home system to a server on the net so that I can reach my home system via ssh.

ssh -R 6022:localhost:22 [email]chris@server.com[/email] -Nq

This command worked and created a tunnel without opening a session in 5.10.  Yes, I want only a tunnel and _no_ interactive shell... ie., once the tunnel is established I should be able to use the bash shell for other purposes...

From ubuntu 6.06 onwards, the command succeeds... I tested by using the ssh and it works... but the bash does not return to the command prompt and I have to ctrl+c to get it back, at which time the tunnel is destroyed.

I read in these forums and elsewhere and used '-4' to force IPV4.  Next, I used '-v' and observed that the tunnel is established.  However, I also noticed a line that says "debug1: Entering interactive session."

I wondering if this indicates some likelihood of where the problem could be ?

Also, I experimented with combinations of 'N' and 'q' to get it working and finally for the 'command' portion of ssh I also used '-' with no success.

Overall, I want to establish a tunnel and get the shell back for other uses.  I am aware of "ctrl+z" and "bg" approach.  However, I want the (previously working) ssh command line to directly do this instead of me doing the suspend+bg all the time.

thanks for your time.

--Kris

---

