---
title: "Secure Remote Desktop Solution Wanted"
date: 2008-11-13
forum: Networking &amp; Wireless
---

### Post by weemee on 2008-11-13
Hi all,

I'm new to Ubuntu :), I've recently purchased a small machine to act as a little server and installed the latest version of Ubuntu (all worked out of the box!).  

It will be screenless, so I'm looking for a good, secure remote desktop solution to run.  I will be accessing via the LAN and internet.

I don't mind paying for a good solution, but ideally not zillions of Pounds/Euro's/Dollars!  I will connect from varying different OS' (mainly windows).

In a perfect world the solution would not require the services of an outside server, I'd like it to be point to point if possible.

Any ideas or suggestions?

Thanks

---

### Post by sefs on 2008-11-13
One way that I access over the machine is with ...

OpenSSH and vnc4server both of which are in the repos.

then on the client I use putty to open a connection and a secure tunnel to the remote machines ssh server and then use the vncviewer on the client to connect to the remote machine via that secure tunnel.

Go into google and type "vnc over ssh" and you will find a list of articles that gives directions on this.

If you are behind a nat router and firewall ect...you will have to open and foward appropriate ports on the remote side.


A second way to do this is to use nomachines.com nx server and client which of which there is a free version.  Again Openssh server must be insalled on the remote machine.  You can get the details on nomachines.com website.

---

