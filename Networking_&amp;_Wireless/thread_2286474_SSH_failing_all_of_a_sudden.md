---
title: "SSH failing all of a sudden"
date: 2015-07-12
forum: Networking &amp; Wireless
---

### Post by ray field on 2015-07-12
For a year or so, I've been happily using Unison via SSH to sync between my Chromebook running Crouton and main desktop. A couple of weeks ago, Unison stopped being able to sync, throwing up "Fatal error: Lost connection with the server." At first I thought it might have had something to do with my having recently implemented the Ubuntu firewall using ufw, except I'd successfully used Unison/SSH for at least a couple of months since putting it up.

when I try to SSH directly, here's what I get on the server side's auth.log:

```
Jul 12 12:13:13 Swann sshd[30905]: Set /proc/self/oom_score_adj to 0
Jul 12 12:13:13 Swann sshd[30905]: Connection from 192.168.1.146 port 39458 on 192.168.1.145 port 2223
Jul 12 12:13:13 Swann sshd[30905]: Authentication refused: bad ownership or modes for directory /home/raphael
Jul 12 12:13:13 Swann sshd[30905]: Failed publickey for raphael from 192.168.1.146 port 39458 ssh2: RSA 6b:31:3f:1a:4a:e5:6e:3e:13:2c:03:99:a2:d3:2a:48
Jul 12 12:13:13 Swann sshd[30905]: Connection closed by 192.168.1.146 [preauth]
```

here is the verbose result from the laptop:

```
ssh -v -p 2223 raphael@192.168.1.145
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to 192.168.1.145 [192.168.1.145] port 2223.
debug1: Connection established.
debug1: identity file /home/raphael/.ssh/id_rsa type 1
debug1: identity file /home/raphael/.ssh/id_rsa-cert type -1
debug1: identity file /home/raphael/.ssh/id_dsa type -1
debug1: identity file /home/raphael/.ssh/id_dsa-cert type -1
debug1: identity file /home/raphael/.ssh/id_ecdsa type -1
debug1: identity file /home/raphael/.ssh/id_ecdsa-cert type -1
debug1: identity file /home/raphael/.ssh/id_ed25519 type -1
debug1: identity file /home/raphael/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.6.1p1 Ubuntu-2ubuntu2
debug1: match: OpenSSH_6.6.1p1 Ubuntu-2ubuntu2 pat OpenSSH_6.6.1* compat 0x04000000
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5-etm@openssh.com none
debug1: kex: client->server aes128-ctr hmac-md5-etm@openssh.com none
debug1: sending SSH2_MSG_KEX_ECDH_INIT
debug1: expecting SSH2_MSG_KEX_ECDH_REPLY
debug1: Server host key: ECDSA b9:10:74:fa:55:6e:16:c0:9b:70:4f:2b:04:f6:bd:7d
debug1: Host '[192.168.1.145]:2223' is known and matches the ECDSA host key.
debug1: Found key in /home/raphael/.ssh/known_hosts:1
debug1: ssh_ecdsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: Roaming not allowed by server
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
Ubuntu 14.04.2 LTS

		hey buddy
		good to see ya!



debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Offering RSA public key: /home/raphael/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Trying private key: /home/raphael/.ssh/id_dsa
debug1: Trying private key: /home/raphael/.ssh/id_ecdsa
debug1: Trying private key: /home/raphael/.ssh/id_ed25519
debug1: No more authentication methods to try.
Permission denied (publickey).
```

Googling gave me [this note suggesting permissions needed changing]("http://www.daveperrett.com/articles/2010/09/14/ssh-authentication-refused/") but I'm not sure it's pertinent -- then again, much as I enjoy using Linux my MO tends to be to gather the bare minimum info/expertise I need to complete a task and then forget all about what little I learned.

---

### Post by steeldriver on 2015-07-12
Yes it's pertinent I think: what are the permissions on those files/dirs in your case?

```

ls -ld ~/{,.ssh,.ssh/id_rsa}

```

---

### Post by ray field on 2015-07-12
This is where I start to get confused (or I guess maybe in the middle of where I get confused) on the desktop or the client? 

Desktop:

```
raphael@Swann:~$ ls -ld ~/{,.ssh,.ssh/id_rsa}
drwxrwxrwx 240 raphael raphael 20480 Jul 12 12:08 /home/raphael/
drwx------   2 raphael raphael  4096 Jul 22  2014 /home/raphael/.ssh
-rw-------   1 raphael raphael  1679 Jul 22  2014 /home/raphael/.ssh/id_rsa
```

Notebook:

```
(trusty)raphael@localhost:~$ ls -ld ~/{,.ssh,.ssh/id_rsa}
drwxr-xr-x 64 raphael raphael 4096 Jul 12 13:55 /home/raphael/
drwx------  2 raphael raphael 4096 Apr 16 11:13 /home/raphael/.ssh
-rw-------  1 raphael raphael 1675 Mar 25 09:27 /home/raphael/.ssh/id_rsa

```

---

### Post by ray field on 2015-07-12
I ran the commands as the article suggested -- on the server tree -- 

```
drwxr-xrwx 240 raphael raphael 20480 Jul 12 16:18 /home/raphael/
drwx------   2 raphael raphael  4096 Jul 22  2014 /home/raphael/.ssh
-rw-------   1 raphael raphael  1679 Jul 22  2014 /home/raphael/.ssh/id_rsa
```

unfortunately, still same result.

---

### Post by ray field on 2015-07-13
Also, weirdly, I couldn't reboot after changing those permissions -- very likely unrelated, since the same thing had been happening from time to time up until a few months ago. Running Boot-Repair from CD got me back up and running.

Still hoping to diagnose and fix this issue.

---

### Post by steeldriver on 2015-07-13
The overpermissive permissions on /home/raphael may have been a problem - on the server side you probably need to look at the permissions of the *public key* file (usually id_rsa.pub) rather than the private key id_rsa (which doesn't really need to be present on the remote side at all)

---

### Post by Lars Noodén on 2015-07-13
The error shows that the home directory has too loose permissions:
```

Jul 12 12:13:13 Swann sshd[30905]: Authentication refused: bad ownership or modes for directory /home/raphael

```
> **ray field said:**
> I ran the commands as the article suggested -- on the server tree -- 

```
drwxr-xrwx 240 raphael raphael 20480 Jul 12 16:18 /home/raphael/
drwx------   2 raphael raphael  4096 Jul 22  2014 /home/raphael/.ssh
-rw-------   1 raphael raphael  1679 Jul 22  2014 /home/raphael/.ssh/id_rsa
```

unfortunately, still same result.

It looks like you may have transposed a number when setting the directory permissions.  Try taking away universal write permission:

```

sudo chmod 755 /home/rafael/

```

Or

```

sudo chmod 750 /home/rafael/

```

---

### Post by ray field on 2015-07-13
> **Lars Noodén said:**
> ...
It looks like you may have transposed a number when setting the directory permissions.  Try taking away universal write permission:

```

sudo chmod 755 /home/rafael/

```


That did the trick! Many thanks, Lars, and steeldriver.

---

