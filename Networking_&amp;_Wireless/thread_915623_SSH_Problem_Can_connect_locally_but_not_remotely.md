---
title: "SSH Problem: Can connect locally but not remotely"
date: 2008-09-10
forum: Networking &amp; Wireless
---

### Post by Trip-dot on 2008-09-10
I am having a problem with my SSH connections. 

I have 2 desktops with Ubuntu 8.04 and running openSSH, and no firewalls installed.

I can access each locally by typing in the location bar:
     sftp://<username>@<local IPaddress>
and everything works fine.

But I cannot connect remotely to either computer either by typing in the location bar:
     sftp://<username>@<actual IPaddress>:<forwarded port>
and I can also not connect via filezilla on a windows computer.

I cannot come up with a reason why I cannot access these two PCs remotely, especially since I could yesterday and nothing should have changed on them since then.

I am grateful for any help.

---

### Post by kevdog on 2008-09-10
Just a few points of clarification

1. Are both machines running Ubuntu?  a combination of Ubuntu/Windows?

2. Are the two machines separated by a router?

3. You are always running a firewall (iptables/netfilter), however if you did not configure it, it just doesn't have any rules and passes all traffic -- iptables -L  will list the rules

4. Have you tried ssh -vvv user@remotehost  (3 v's) to provide debugging output?

5. Could it be a DNS resolving problem?  Can you ping the server?

6. How are you authenticating? Password, Keys?

Thanks, its probably an easy problem.

---

### Post by Trip-dot on 2008-09-10
1.  Both machines that I cannot connect remotely to are running ubuntu, I had also tried to connect with a windows machine and no success.

2. They are separated by a linksys router.

3. iptables -L gives me the following output:

   Chain INPUT (policy ACCEPT)
   target     prot opt source               destination         

   Chain FORWARD (policy ACCEPT)
   target     prot opt source               destination         

   Chain OUTPUT (policy ACCEPT)
   target     prot opt source               destination      

4.  ssh -vvv returns the following:

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
<key>.
Please contact your system administrator.
Add correct host key in /home/<user>/.ssh/known_hosts to get rid of this message.
Offending key in /home/<user>/.ssh/known_hosts:2
RSA host key for <ipaddress> has changed and you have requested strict checking.
Host key verification failed.

5. I can ping the server i get messages of bytes sent.

6. I authenticate with passwords.

The error window that pops up when I try to connect says:

Couldn't display "sftp://<user>@<ipaddress>/".
Error: Host key verification failed
Please select another viewer and try again.


I hope this is enough information to help. 
Thanks very much

---

### Post by Trip-dot on 2008-09-11
Apparently the problem was that I needed to empty out the known_hosts file in home/<user>/.ssh

i deleted that file and everything was back to working.

---

