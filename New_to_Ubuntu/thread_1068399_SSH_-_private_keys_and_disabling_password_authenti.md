---
title: "SSH - private keys and disabling password authentication"
date: 2009-02-12
forum: New to Ubuntu
---

### Post by Nixie Pixel on 2009-02-12
Hi, I am trying to set up a secure OpenSSH server accessible from the internet.  I have successfully set up a public/private key pair and been able to log in from one client to the server.  I have opened and forwarded the proper port on my firewall and tested from outside the network, and was successful connecting.

I have two questions now.  First, can I use the same private key on multiple clients, or do I need to generate a new private/public key pair on each client machine and copy over the public key for each to the server?

Also, how do I turn off the password authentication fallback, so no one can brute-force attack my server?

Thanks!

Edit:  Nevermind the second question, I found out how to turn off password authentication, by editing /etc/ssh/sshd_config

---

### Post by cerealtx on 2009-02-12
here found some info on it been playing around with this myself, its about 1/2 down the page at the "Distributing your public key" section
[http://toic.org/2008/11/17/ssh-basics/](http://toic.org/2008/11/17/ssh-basics/)

---

### Post by Nixie Pixel on 2009-02-12
Thanks, the answer is pretty simple.

Copy the private key file over to the other client, and chmod 600.  Voila!

Thanks!

---

