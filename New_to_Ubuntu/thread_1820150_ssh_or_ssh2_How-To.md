---
title: "ssh or ssh2 How-To?"
date: 2011-08-07
forum: New to Ubuntu
---

### Post by is kla. on 2011-08-07
Can somebody please explain to me how can I install ssh2 on my ubuntu 10.04, I need it for my game control panel. 

I couldn't find any tutorial about this that explains everything step by step.

I have installed LAMP on the server.

---

### Post by mendhak on 2011-08-07
I believe you may already have SSH2, in the sense that it provides SFTP, pubkey authentication, etc.  If you haven't already, 

sudo apt-get install ssh

That installs a client and server for you. 

You can read more here:

[https://help.ubuntu.com/community/SSH](https://help.ubuntu.com/community/SSH)

It has links that show you how to set up your private key/public key for connecting to a machine.

---

