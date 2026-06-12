---
title: "using FTP"
date: 2013-12-29
forum: Networking &amp; Wireless
---

### Post by akash_metu21 on 2013-12-29
hey folks,

I am trying to get an image from a remote desktop using ftp. but i dont want to insert the password everytime i run the sftp protocol, so is there a way to edit the .bashrc file so that i dont have to insert the password everytime i run this command.

thank you.

---

### Post by papampi on 2013-12-30
you should create public/private key pair by using ssh-keygen to use with sftp.

---

### Post by Lars Noodén on 2013-12-30
And once you have the key pair (with a strong passphrase) you can load it into the agent with [ssh-add](http://manpages.ubuntu.com/manpages/saucy/en/man1/ssh-add.1.html)

```

ssh-add /home/akash_metu21/.ssh/some_key_rsa

``` 

You only need to enter the passphrase when loading the key into the agent.  Once the key is loaded, you can then connect with sftp and it will try the key automatically.

---

