---
title: "SSH very slow.."
date: 2010-09-10
forum: New to Ubuntu
---

### Post by putu.sundika on 2010-09-10
dear all, 

i build LAMP server with FedoraCore9 on 2 server. all settings totally same.(local area)
then i connect to each server from my ubuntu netbook through ssh.
why ssh (connecting or authentification?) is very slow on 1 server, but very fast on others.
is it something wrong with my ubuntu, might be need setup something ? or must be on server, but server setting totally same and i turn off the firewall. Server hardware is same.

but when i connect through SSH from M$Windows to both server, both are fast.

please help....

---

### Post by BugBuster on 2010-09-10
try this on your client machine...ie the ubuntu machine from where you are connecting to the ssh server.

```
 sudo nano /etc/ssh/ssh_config 
```

Now look for a line that says:
```
GSSAPIAuthentication yes
```

and change it to :
```
GSSAPIAuthentication no
```

If that works you could also change this setting on the ssh server by editing the same option in /etc/ssh/sshd_config

---

### Post by putu.sundika on 2010-09-13
great.... that's works !!!
thanks :popcorn:

---

