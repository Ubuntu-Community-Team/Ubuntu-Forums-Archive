---
title: "Passwordless ssh?"
date: 2008-02-16
forum: Networking &amp; Wireless
---

### Post by sammydee on 2008-02-16
Hi all.

A few weeks ago I had a pretty much default install of sshd on a server and ssh on a laptop.

Automatic passwordless logins just sort of worked automagicall - I'd type in my password once for the first time but all the other times it wouldn't ask.

I'm not sure what I changed but it suddenly stopped working like that. Now I have to put my password in every time. I've tried setting it up with public key signing instead but it just asks me for my key password every time which isn't any better.

Is there a way of making ubuntu unlock the ssh key on login, like it does with the wireless password?

Sam

---

### Post by kevdog on 2008-02-16
If you set the server to not allow password athentication (something like this in the sshd_config file on the server):

PasswordAuthentication no

The server will not accept any passwords


In the ssh_config file on the client, if you specify the following:
IdentityFile ~/.ssh/id_rsa

Then automatically the program will look for the private key to log into the ssh server at the above location.

---

### Post by Lars Noodén on 2008-02-16
What kevdog wrote above is good.  Maybe, though, you were using [ssh-agent]("http://linux.die.net/man/1/ssh-agent") that first time?  That's one way of entering the password just once.

---

### Post by Dr Small on 2008-02-16
Here is my guide on a passwordless ssh login with ssh keys:
[http://php.8ez.com/drsmall/blog/?p=218](http://php.8ez.com/drsmall/blog/?p=218)

---

### Post by sammydee on 2008-02-16
Hi all

Fiddled around a bit with seahorse keyring manager and it's magically working again! Yay!

thanks anyway though

Sam

---

