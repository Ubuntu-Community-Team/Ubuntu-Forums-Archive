---
title: "SSH  can't open /dev/tty: No such device or address"
date: 2014-10-17
forum: Networking &amp; Wireless
---

### Post by dazz100 on 2014-10-17
Hi

I had this error message when I was trying to automate an SSH connection. If found a lot of others with similar problems.  It took me a lot of surfing to find bad advice and semi-OK answers.  So here is my attempt to help those who follow.

The problem I was trying to solve was to auto run (auto)SSH with upstart.
For testing purposes, I ran SSH from the CLI.  It worked.
I ran SSH from a script.  It worked.
I ran SSH from upstart (the same script) and got the error message "can't open /dev/tty: No such device or address".

I fixed this problem by studying the logs.

So this was the log for SSH run from the command line.  No problems.
```
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 01:ff:79:dc:e2:b0:4c:52:11:
debug1: Host '[dazz.no-ip.biz]:24836' is known and matches the RSA host key.
debug1: Found key in /home/darren/.ssh/known_hosts:11
debug2: bits set: 502/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
debug2: set_newkeys: mode 1
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug2: set_newkeys: mode 0
debug1: SSH2_MSG_NEWKEYS received
```

This is the log from running SSH as [sudo] user.
It logs a warning due to the different location the key is found in.
```
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 01:ff:79:dc:e2:b0:4c:52:11:07:
debug1: Host '[dazz.no-ip.biz]:24836' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:2
Warning: the RSA host key for '[dazz.no-ip.biz]:24836' differs from the key for the IP address '[122.57.125.74]:24836'
Offending key for IP in /root/.ssh/known_hosts:1
Matching host key in /root/.ssh/known_hosts:2
Are you sure you want to continue connecting (yes/no)? yes
debug2: bits set: 516/1024
debug1: ssh_rsa_verify: signature correct
debug2: kex_derive_keys
```

What follows is the same command run from upstart.   Upstart always runs as root.   The connection fails.

```
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Server host key: RSA 01:ff:79:dc:e2:b0:4c:52:11:07:
debug1: Host '[dazz.no-ip.biz]:12345' is known and matches the RSA host key.
debug1: Found key in /root/.ssh/known_hosts:2
debug1: read_passphrase: can't open /dev/tty: No such device or address
Host key verification failed.
OpenSSH_5.9p1 Debian-5ubuntu1, OpenSSL 1.0.1 14 Mar 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to dazz.no-ip.biz [122.57.125.70] port 12345.
debug1: Connection established.
```

The first thing to know is that the /dev/tty error is not the root cause.  What is happening is that the SSH command is trying to send an error message to a terminal.  If there isn't one open, it errors out. In my case, the error message is: 
```
Host key verification failed.
```

The root cause whatever is generating the error message. 
In my case the problem was that when run as root, it tried to find the keys in the /root/.ssh directory.  The keys in that directory didn't match so authentication failed.  Nothing to do with tty.

I fixed the problem by copying the contents of /home/foouser/.ssh/ to /root/.ssh.  

I found this by doing a line by line comparison of the log files.  Nothing radical in that approach.  

So I hope this is of help to others.

---

### Post by Lars Noodén on 2014-10-17
Or you could have your upstart script use sudo to launch ssh as the user 'darren', or pass the path to the key explicitly using -i

```

sudo -u darren ssh -i ....
```

There are several ways out.

---

