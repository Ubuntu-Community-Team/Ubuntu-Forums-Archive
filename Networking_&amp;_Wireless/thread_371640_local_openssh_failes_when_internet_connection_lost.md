---
title: "local openssh failes when internet connection lost"
date: 2007-02-27
forum: Networking &amp; Wireless
---

### Post by byenary on 2007-02-27
Hello,

I have a network with a few ubuntu servers, I use openssh to connect to them for configuring/monitoring/changing, is use the shell or nautilus.
Now we have a router wich is connected to cable, the cablecompany is doing some work on the infrastructure so sometimes connection is lost, the strange thing is, when connection is lost i cannot connect via openssh to my local servers.... ?? When using windows ssh secure shell it does work but i takes a while to get connected.... anybody a explanation or even better a solution for this weird event ?

---

### Post by lkagan on 2007-02-27
When a client connects to a server via ssh, the ssh server tries to identify the client via DNS by default.  Add the following to your /etc/ssh/sshd_config and restart the sshd:

```
UseDNS No
```

That will probably fix it.

Larry Kagan

---

### Post by byenary on 2007-02-28
I added to NoDNS line but does not do the trick for me

---

### Post by lkagan on 2007-02-28
It's not noDNS, it's 'UseDNS no'.  And make sure you restart the sshd service with:

```
/etc/init.d/sshd reload
```

---

### Post by byenary on 2007-03-01
Sorry i was not clear, i did ad UseDNS No
and restarted the computer to be sure, booted with internet connection and than released the wan ip, and local ssh did not work again, and i'm using ip-addresses while doing ssh so it should not be a dns issue

---

