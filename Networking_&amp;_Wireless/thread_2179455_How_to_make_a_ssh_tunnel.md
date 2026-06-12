---
title: "How to make a ssh tunnel"
date: 2013-10-08
forum: Networking &amp; Wireless
---

### Post by TheOnlyChosenOne on 2013-10-08
Hi all

I'm trying to make a ssh tunnel, but it doesn't seem to work.
Here is the set up:
There are two servers that are important. One server can be reached from the outside (let's say server 1). One is an internal server (let's say server 2), which can be reached once you are on server 1.
There is an LDAP service I have to bind to on server 2. Now, when I put my php script on server 1, I can bind to server 2 without any problems (running apache on server 1).
Now, I'm trying to run this script locally while forwarding the LDAP service to my pc here. What I'm trying to do is this:
ssh -L [local port]:[user]@[server 1]:389 localhost
389 is the port for LDAP.
I've tried a lot of things. But nothing seems to work :(. Tutorials about ssh tunneling are confusing and contradict each other.
I've also tried [two hop solutions]("http://superuser.com/questions/96489/ssh-tunnel-via-multiple-hops"), which none of them seemed to work.

I hope someone has a solution here.

---

### Post by Lars Noodén on 2013-10-08
Here is a short description of one way to do it:

[http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Proxies_and_Jump_Hosts#Port_Forwarding_via_an_Intermediate_Host](http://en.wikibooks.org/wiki/OpenSSH/Cookbook/Proxies_and_Jump_Hosts#Port_Forwarding_via_an_Intermediate_Host)

Does that make sense?  If you substitute the ports, it should allow you to connect to LDAP on the local host which is really on machine2 via machine1.  Both machines have to have an SSH server running.

---

### Post by TheOnlyChosenOne on 2013-10-10
Thank you for your reply.
The document you gave me is not 100% complete.
It says
```
 ssh -L 2222:machine2.example.org:22 machine1.example.org
```
while it actually shoud say
```
ssh -L 2222:machine2.example.org:22 user@machine1.example.org
```
Anyway. The example works.

Still, I cannot make my php script work.
The ssh tunnel:
```
 ssh -L 1337:server2:389 user@server1
```
Then I run this script:
```
<?php
echo "start";
$host = 'localhost';
$port = '1337';
$ds = ldap_connect($host, $port);
echo "success!";
?>
```
On my local pc, only 'start' is printed, while on server1, 'startsuccess!' is printed.

Do I have to forward more ports?

Thanks

---

### Post by Lars Noodén on 2013-10-10
Hmm.  The example works for me both for forwarding SSH and HTTP.  Maybe the user is different on machine2 and machine1?  

About tunneling LDAP, when you make the tunnel does it complain at all?  If port 1337 is in use already, then it will say something like "bind: Address already in use"

---

### Post by TheOnlyChosenOne on 2013-10-10
It is the same user for both servers.
No message is shown, other than 'welcome...' which is always the case if you connect to this shell server.

---

