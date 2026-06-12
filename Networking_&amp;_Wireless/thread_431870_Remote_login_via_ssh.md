---
title: "Remote login via ssh"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by zenkaon on 2007-05-03
Hello all,

I need to log into my laptop, which is running kubuntu 7.04, from another PC via ssh. I am having problems doing so, can anybody help me?

I have got the firestarter firewall programme, when I ssh into my laptop from the remote machine, firestarter correctly flags that there is a serious event happening, then I poke a hole in in my firewall to allow connections from the remote host on port 22.

Now when I ssh into my laptop from the remote PC I get a:
ssh: connect to host xxx.xxx.xxx.xxx port 22: Connection refused
and firestarter doesn't flag a warning.

What do I have to do to my laptop to let me logon to it remotely?

Cheers

---

### Post by Churnd on 2007-05-03
Is SSH running?

```
ps -ax | grep sshd
```

Did it work before you installed Firestarter?

---

### Post by zenkaon on 2007-05-03
Hi,

No sshd is not running. In my old red hat system I used to be able to do:
service sshd
but the service command doesn't seem to exist on ubuntu. How do I start sshd?

I just removed firestarter to see what would happen. I still get connection refused, so I'm going to put firestarter back on.

---

### Post by milton1 on 2007-05-03
you will probably need to install openssh-server. It should auto-start after install.

---

### Post by Churnd on 2007-05-03
> **zenkaon said:**
> Hi,

No sshd is not running. In my old red hat system I used to be able to do:
service sshd
but the service command doesn't seem to exist on ubuntu. How do I start sshd?

I just removed firestarter to see what would happen. I still get connection refused, so I'm going to put firestarter back on.

```
sudo /etc/init.d/sshd start
```

If that doesn't work, it's not installed.

---

### Post by zenkaon on 2007-05-03
Thanks everybody,

I installed the openssh-server and can now happily logon to my laptop from my remote PC.

---

### Post by cvmostert on 2007-05-04
> **zenkaon said:**
> Thanks everybody,

I installed the openssh-server and can now happily logon to my laptop from my remote PC.

Thanks for this post, I also installed it and will test it the first opportunity i get.

---

