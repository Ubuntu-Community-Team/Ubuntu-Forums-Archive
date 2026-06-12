---
title: "SSH Connection refused"
date: 2014-02-03
forum: Networking &amp; Wireless
---

### Post by khurtsiya on 2014-02-03
Hi!

I was able to connect to this dedicated server, but after some "coding" it says Connection refused...

I believe I not edited any important config.

Please, help where to look first?

---

### Post by Lars Noodén on 2014-02-03
Can you post the full error message?

---

### Post by khurtsiya on 2014-02-03
That was full> ssh: connect to host 92.222.136.30 port 22: Connection refused


---

### Post by khurtsiya on 2014-02-03
a little more if this helps

> :~$ ssh -vvvvv mihail@92.222.136.30
OpenSSH_6.1p1 Debian-4, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 92.222.136.30 [91.222.136.30] port 22.
debug1: connect to address 92.222.136.30 port 22: Connection refused
ssh: connect to host 92.222.136.30 port 22: Connection refused


---

### Post by Lars Noodén on 2014-02-03
Can you connect out of band (not via SSH) via the console or something?  It seems that the ssh server might not be running, or that if it is then it is listening to a different port.  The first thing to check is if sshd is running on the remote host.

---

### Post by khurtsiya on 2014-02-03
I will have KVM tomorrow I think, but I rebooted server from my ISPManager and I think sshd should be restarted with it. And as I remember - I did not changed port.

---

### Post by Lars Noodén on 2014-02-03
Then it may not be running.  You can check when you do get out of band access.

```

sudo service ssh status

```

Or maybe the firewall on the host is blocking port 22.  If you activated UFW, you have to also allow ssh.

```

sudo ufw allow ssh

```

---

### Post by khurtsiya on 2014-02-03
I can not check on server because I do not have SSH access, but nmap says port 22 is closed.
I guess this happened after I rebooted server.

---

### Post by Lars Noodén on 2014-02-03
Can your ISPManager check on or restart sshd?

---

### Post by khurtsiya on 2014-02-03
I do not use ufw

---

### Post by khurtsiya on 2014-02-03
Solved. I deleted accidentaly some letters in config...

---

### Post by Lars Noodén on 2014-02-04
It's also possible to do a quick test of the syntax of the configuration file using the **-T** option after making changes and before logging out.

```

sudo sshd -T

```

That won't catch everything but it will catch most typos.

---

