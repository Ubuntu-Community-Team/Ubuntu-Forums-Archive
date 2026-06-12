---
title: "what does a deamon do?"
date: 2011-05-09
forum: New to Ubuntu
---

### Post by wlraider70 on 2011-05-09
So I'm a little confused on the topic of a daemon. I;m thinking specifically of the sshd. I've been messing with the conf of both ssh_server.conf and sshd_server.conf.
In side both files are almost identically options for using passwords vs rsa/dsa

So what does the Daemon do, why does it have the same options as the conf file. (I think i have noticed such similarity in other services too) Does one have priority over the other?

---

### Post by el_koraco on 2011-05-09
deamons wait for a function which they are designed to fulfill. the sshd waits for incoming ssh connections, if i'm not mistaken. don't use ssh, so i'm not an expert in the field. i'd suppose it is handled through the ssh config files, as well as its own config.

---

### Post by compmodder26 on 2011-05-09
Are you sure those files aren't ssh_config and sshd_config?  None of my ssh servers have ssh_server.conf and sshd_server.conf.  

In relation to the files I have above, ssh_config is the ssh client configuration file, while sshd_config is the ssh server configuration file.

Wiki has a more detailed answer on a daemon for you:

[http://en.wikipedia.org/wiki/Daemon_(computing](http://en.wikipedia.org/wiki/Daemon_(computing))

---

### Post by wlraider70 on 2011-05-09
Yeah i think those are the file names. oops

Ok that makes sense. THANKS

---

