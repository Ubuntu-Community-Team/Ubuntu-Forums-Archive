---
title: "SSH Trick"
date: 2007-12-13
forum: Networking &amp; Wireless
---

### Post by jobmo on 2007-12-13
Hi, I would wondering if someone out there could maybe help me come up with a little trick for ssh.
What I would like to do is run an ssh server from behind a firewall. Unfortunately I have no control over the firewall so I cannot do port forwarding or anything of the sort.
I know this sounds impossible at first, but is there any way I can setup ssh to constantly try and open connections to a server, and then have the server listen for these connections, and if it hears them open up an ssh connection. The tricky part to this is I would like the sshd (ssh server) connecting to the ssh client. And the ssh client to listen for the server.

Heres a little diagram

[SSH Server] ------->(Firewall)----->[ssh.client.com]

---

### Post by jcostom on 2007-12-13
No, what you're asking for just isn't possible with the standard openssh packages.

To do what you want, you'll need to write a considerable amount of custom code.

Why not take this up with the firewall people?  It's not an unreasonable request, unless it's a violation of your organization's security policy, in which case, circumventing policy is NOT the way to accomplish your goals.  The thing to do is work to change the policy to something that provides appropriate intrusion countermeasures, while permitting the level of access you need.

---

### Post by Junglizer on 2007-12-13
Do you know what ports are open on the firewall? If you were to forward through 80 or 21?

---

### Post by Lostincyberspace on 2007-12-13
it is pretty easy to setup ssh to run through another port. making it find the port is not feasible goal, but it is possible.

---

