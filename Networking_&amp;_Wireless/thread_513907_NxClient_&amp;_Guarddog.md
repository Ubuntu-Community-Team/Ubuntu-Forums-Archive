---
title: "NxClient &amp; Guarddog"
date: 2007-07-31
forum: Networking &amp; Wireless
---

### Post by DapperMe17 on 2007-07-31
Hello,

I'm running Guarddog firewall on a Kubuntu machine which is also running a NoMachine NxServer to allow secure(ssh), remote desktop sharing.

Can someone tell me what protocols I will have to allow in the firewall for a remote NxClient to access the above indicated NxServer system?


Thanks!

---

### Post by kevdog on 2007-07-31
Since you are using ssh -- you only need port 22 open.  If perhaps you changed the port in the sshd_config file from 22 to something else, you only need to open that port.

---

### Post by DapperMe17 on 2007-07-31
Sorry, that didn't work.

I created new rules in Guarddog's "advanced" tab, to allow bi-directional traffic of port 22, both TCP & UDP.

However, this doesn't allow NxClient to communicate with the NxServer.

---

### Post by kevdog on 2007-07-31
Strange -- I dont have to open up any more ports ---

Another idea, since Im at a loss

Turn off the firewall,

Allow client server to connect,

Then type netstat -n to see what ports are open

You are using freenx seveas server with a nomachine nx client?

---

### Post by DapperMe17 on 2007-08-08
I'm using the latest version of NoMachine Server on the Ubuntu machine. This machine is behind a wireless router, where port 22 is open & communication is all & well from a remote NoMachine Client PC.

Connection halts once I install GuardDog, or Firestarter, on the server machine.


Anyone with the correct settings for port 22 connection using wither firewall would be greatly appreciated.

Thanks 

:guitar:

---

### Post by kevdog on 2007-08-08
If I new how to setup the Iptables manually I would tell you.  

Its obviiously a firewall problem.  Im using Guarddog.

In your guarddog settings, what zones do you have?

Assuming the you are on the server working with guarddog:

If you only have internet and local, you want to go under the protocol tab and then select local (under defined internet zones).  Click on Interactive Sessions, and then put a check mark under the row ssh remote login session with the column name of Internet.

One thing you want to check is the port ssh_d is listening on.  This can best be found in the /etc/ssh/sshd_config file, with the port statement.  If your port is 22, then the above should work for you.  If using a different port number, you will need to configure a custom port with guarddog.

---

### Post by DapperMe17 on 2007-08-08
Thanks!

I'll give that a try.

---

