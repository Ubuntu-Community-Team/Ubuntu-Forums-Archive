---
title: "SSH Tunneling and terminal on remote machine"
date: 2009-12-01
forum: New to Ubuntu
---

### Post by daffy_dowden on 2009-12-01
Hi all,

I'm trying to connect a server (called PrivateServer) through ssh on my machine from home. This server isn't connected directly to the internet. At present I SSH to a gateway machine (PublicServer) which is connected to the internet and the network with the PrivateServer on it, and then open up an ssh connection from there. 

So the commands are roughly as follows:

home# ssh username1@PublicServer
PublicServer# ssh username2@PrivateServer
PrivateServer#

Note that the username is different between the two servers. Is it possible to roll the two commands into one? Will I be able to use my public key with this command?

Finally, I've heard of port forwarding, but I'm not really sure how to go about setting this up. PrivateServer is a webserver, so it'd be handy to forward port 80 to another port on my home machine to view internal webpages. Could anyone help me with the command for this?

Many thanks in advance!
Daf

---

### Post by Bachstelze on 2009-12-01
Do something like:

```
ssh -L 8080:private_server:80 username1@public_server
```

You can now connect to private_server from your home machine with [http://127.0.0.1:8080](http://127.0.0.1:8080)

---

### Post by daffy_dowden on 2009-12-01
Hi Bachstelze, thanks for the reply.

This works great for viewing the websites, but is there anyway to roll the two SSH connection commands into one?

Daf

---

### Post by bodhi.zazen on 2009-12-01
you can do it with ssh keys with the option called forced commands.

Make a key for connecting, and force the command to connect to the second server in the 
key.

A potential alternate solution is to use screen, keep the second ssh session running in a detached screen and then ssh into the screen session.

Here is a link to get you started with screen : [http://blog.bodhizazen.net/linux/shared-ssh-sessions-update-for-jaunty-ubuntu-904/](http://blog.bodhizazen.net/linux/shared-ssh-sessions-update-for-jaunty-ubuntu-904/)

---

### Post by daffy_dowden on 2009-12-03
Thanks bodhi and Bachstelze, think I'll just stick with screen. Shame though, I really wanted to create a quick shortcut for when I was outside of the network. 

Thanks again for your help!

---

