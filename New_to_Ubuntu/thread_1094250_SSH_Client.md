---
title: "SSH Client"
date: 2009-03-12
forum: New to Ubuntu
---

### Post by BDNiner on 2009-03-12
there is a version of putty on linux, you can also just shh from the terminal.

---

### Post by ptn107 on 2009-03-12
On the server install: openssh-server, openssh-blacklist, openssh-blacklist-extra

On the client this should already be installed: openssh-client

Now to connect from a client machine open a terminal and type:
[HTML]ssh <ip address of server>[/HTML]

Just make sure your user account exists on the server as well as the client.

* Give [_this_]("http://it.toolbox.com/blogs/locutus/shh-securing-ssh-howto-10640") a read for a more in-depth how-to on making your ssh more secure.  I recommend doing away with passwords and using passkeys only.

---

