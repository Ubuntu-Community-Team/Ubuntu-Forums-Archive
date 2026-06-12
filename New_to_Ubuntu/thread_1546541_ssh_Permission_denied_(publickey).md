---
title: "ssh Permission denied (publickey)"
date: 2010-08-05
forum: New to Ubuntu
---

### Post by furialis on 2010-08-05
Per title. I had this working yesterday, I don't know what happened. I tried a few thing then completely removed the ssh server and reinstalled it. I changed allowrootlogins to no and changed password authentication to no. I generated a new key and copied it to a thumb drive, moved it to my laptop and put the key in the authorized_keys folder. I also tried
```

chmod go-w ~/
chmod 700 ~/.ssh
chmod 600 ~/.ssh/authorized_keys

```

This is over a LAN for now.

Any suggestions?

---

### Post by Joeb454 on 2010-08-05
Which key did you put on the laptop? id_rsa or id_rsa.pub?

---

### Post by furialis on 2010-08-05
First I tried id_rsa.pub. Then I put the other one, just plain id_rsa to see if it'd work. It still didn't and I deleted the id_rsa.

---

### Post by Joeb454 on 2010-08-05
you should have id_rsa.pub on the remote server. This is your public key.

ida_rsa is your private key, this matches the public key and should only ever be on your local machine :)

Here's the permissions I have on my server for the .ssh directory:
```
drwx------ 2 joe  joe      4096 2010-05-31 23:14 .ssh
```
And it's contents:
```
joe@tatooine:~$ ls -l .ssh/
total 16
-rw-r--r-- 1 joe joe 1581 2010-05-31 22:50 authorized_keys
-rw-r--r-- 1 joe joe  137 2010-05-31 22:50 config
-rw-r--r-- 1 joe joe 4862 2010-05-31 23:14 known_hosts

```

Try setting yours to the same, and see if it works then.

---

### Post by furialis on 2010-08-05
Maybe I'm confused about terminology, so please bear with me.

The remote machine, my laptop, does not have the server on it, only the client. In the authorized_keys folder there is only one file - id_rsa.pub.
```

r@r:~$ ls -l .ssh/
total 8
drw------- 2 r r 4096 2010-08-05 14:35 authorized_keys
-rw-r--r-- 1 r r  442 2010-08-05 14:35 known_hosts

```

On my local machine, my desktop, I have the server installed. This is the machine where the keys were generated. 
```

c@c:~$ ls -l .ssh/
total 8
-rw------- 1 c c 3311 2010-08-05 14:33 id_rsa
-rw-r--r-- 1 c c  725 2010-08-05 14:33 id_rsa.pub

```

If I need to change permissions, would you mind a little spoon feeding?

---

### Post by Joeb454 on 2010-08-05
You need the ssh server application installed on whichever PC you're trying to log into. As for changing your permissions, on the laptop, run ```
chmod og+r .ssh/authorized_keys
```

As above - make sure the server application is installed on the PC you're trying to connect to.

---

### Post by furialis on 2010-08-05
Thanks for the quick replies.

The server application is installed on my desktop via Synaptic. I have also restarted the computer. I am using my laptop to try and connect to my desktop. On my laptop I run:
```

ssh c@192.168.1.149

```
I also ran the command from your previous post on my laptop. Still getting the same error.

---

### Post by furialis on 2010-08-05
Bump with more info.

I also tried creating a dsa key with the same results. Not sure if this will help; it's the verbose output from the ssh command on my laptop when trying to connect to my desktop.
```

r@r:~$ ssh -l c -v 192.168.1.149
OpenSSH_5.3p1 Debian-3ubuntu4, OpenSSL 0.9.8k 25 Mar 2009
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 192.168.1.149 [192.168.1.149] port 22.
debug1: Connection established.
debug1: identity file /home/r/.ssh/identity type -1
debug1: identity file /home/r/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-4096
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-4096
debug1: identity file /home/r/.ssh/id_dsa type 2
debug1: Checking blacklist file /usr/share/ssh/blacklist.DSA-1024
debug1: Checking blacklist file /etc/ssh/blacklist.DSA-1024
debug1: Remote protocol version 2.0, remote software version OpenSSH_5.3p1 Debian-3ubuntu4
debug1: match: OpenSSH_5.3p1 Debian-3ubuntu4 pat OpenSSH*
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_5.3p1 Debian-3ubuntu4
debug1: SSH2_MSG_KEXINIT sent
debug1: SSH2_MSG_KEXINIT received
debug1: kex: server->client aes128-ctr hmac-md5 none
debug1: kex: client->server aes128-ctr hmac-md5 none
debug1: SSH2_MSG_KEX_DH_GEX_REQUEST(1024<1024<8192) sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_GROUP
debug1: SSH2_MSG_KEX_DH_GEX_INIT sent
debug1: expecting SSH2_MSG_KEX_DH_GEX_REPLY
debug1: Host '192.168.1.149' is known and matches the RSA host key.
debug1: Found key in /home/r/.ssh/known_hosts:1
debug1: ssh_rsa_verify: signature correct
debug1: SSH2_MSG_NEWKEYS sent
debug1: expecting SSH2_MSG_NEWKEYS
debug1: SSH2_MSG_NEWKEYS received
debug1: SSH2_MSG_SERVICE_REQUEST sent
debug1: SSH2_MSG_SERVICE_ACCEPT received
debug1: Authentications that can continue: publickey
debug1: Next authentication method: publickey
debug1: Trying private key: /home/r/.ssh/identity
debug1: Offering public key: /home/r/.ssh/id_rsa
debug1: Authentications that can continue: publickey
debug1: Offering public key: /home/r/.ssh/id_dsa
debug1: Authentications that can continue: publickey
debug1: No more authentication methods to try.
Permission denied (publickey).
r@r:~$ 

```

---

### Post by furialis on 2010-08-05
OK, I feel stupid. 

Just in case anyone else runs into this problem, I had Nautilus opened as root because I was editing the config file. I copied the key file as root onto the thumb drive. When I used my normal user to copy the key file, it worked just fine. 

Thanks for the help.

---

### Post by Joeb454 on 2010-08-06
Glad you got it resolved in the end :)

---

