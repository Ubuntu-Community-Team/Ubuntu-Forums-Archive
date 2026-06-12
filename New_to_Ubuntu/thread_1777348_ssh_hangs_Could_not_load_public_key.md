---
title: "ssh hangs: Could not load public key"
date: 2011-06-07
forum: New to Ubuntu
---

### Post by DSn0wMan on 2011-06-07
ssh connections always hang. It doesn't seem like ssh can load public keys from my home directory. How can I fix this?


grayjo@asg-jp95yc1:~/ec2$ ssh -vvv [email]ec2-user@ec2-50-19-171-111.compute-1.amazonaws.com[/email]
OpenSSH_5.8p1 Debian-1ubuntu3, OpenSSL 0.9.8o 01 Jun 2010
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to ec2-50-19-171-111.compute-1.amazonaws.com [50.19.171.111] port 22.
debug1: Connection established.
debug3: Incorrect RSA1 identifier
debug3: Could not load "/home/grayjo/.ssh/id_rsa" as a RSA1 public key
debug2: key_type_from_name: unknown key type '-----BEGIN'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'Proc-Type:'
debug3: key_read: missing keytype
debug2: key_type_from_name: unknown key type 'DEK-Info:'
debug3: key_read: missing keytype
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug3: key_read: missing whitespace
debug2: key_type_from_name: unknown key type '-----END'
debug3: key_read: missing keytype
debug1: identity file /home/grayjo/.ssh/id_rsa type 1
debug1: Checking blacklist file /usr/share/ssh/blacklist.RSA-2048
debug1: Checking blacklist file /etc/ssh/blacklist.RSA-2048
debug1: identity file /home/grayjo/.ssh/id_rsa-cert type -1
debug1: identity file /home/grayjo/.ssh/id_dsa type -1
debug1: identity file /home/grayjo/.ssh/id_dsa-cert type -1
debug1: identity file /home/grayjo/.ssh/id_ecdsa type -1
debug1: identity file /home/grayjo/.ssh/id_ecdsa-cert type -1

grayjo@asg-jp95yc1:~/ec2$ ls -ltr /home/grayjo/.ssh/id_rsa
-rw------- 1 grayjo grayjo 1766 2011-06-07 11:07 /home/grayjo/.ssh/id_rsa

---

### Post by lkraemer on 2011-06-08
First thing is your key really needs to be a Version 2 key, not Version 1,
but Amazon uses Version 1

Next, view your key and see what is wrong with this command:
```

cat ~/.ssh/id_rsa

```
which should have some format such as:  (I know i posted a dsa example)
```

-----BEGIN DSA PRIVATE KEY-----
MIIBuwIBAAKBgQD0CYNYzf1nsz5d6qPCoh7NJEVp39Jph8Yq9eWiLmOekL1tIy5u
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxx.WHY ME!!.xxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
WBtBZtPqMRT5cgvh4url
-----END DSA PRIVATE KEY-----

```
and your ERROR message states this is incorrect.  How was your ssh-keygen
generated.  I'd review the man pages on ssh-keygen generation.
```

    ssh-keygen -t rsa

```
and type a password, or press enter. (If you use a password, make sure you remember it!)
Two keys will be generated, Private & Public for rsa which will be Version 2 keys,
located at /home/loginuser/.ssh   For Version 1 Keys use ```
ssh-keygen -1 -t rsa
```
```

    ~/.ssh/id_rsa
    ~/.ssh/id_rsa.pub

```
Permissions, as generated, should be:
> 
-rw-------   1 larry larry   668 May 29 20:42 id_rsa      (= PRIVATE)
-rw-r--r--   1 larry larry   602 May 29 20:42 id_rsa.pub  (= PUBLIC)

Also, your Public Key needs to be copied to your Server, and placed at
the proper subdirectory, as per your Server info.  See their Forum.....

Also, your Keys can be generated on Server or Client, then copied to the
proper places.

PROTECT your KEYS!!!!  REF: Your Server Forum!


REF:
[http://bodhizazen.net/Tutorials/SSH_overview](http://bodhizazen.net/Tutorials/SSH_overview)

lk

---

### Post by DSn0wMan on 2011-06-08
I am generating the keys properly, but what I am concerned about is why can't ssh load it?

debug3: Could not load "/home/grayjo/ec2/aws_key.pub" as a RSA1 public key

---

### Post by lkraemer on 2011-06-08
Well, if you are 100% sure that the keys are generated properly,
then there are only four things left to verify.  Why are you using
Version 1 Keys instead of Version 2 keys?  Version 2 is more secure.
Can you now cat ~/.ssh/your_rsa_key ??????

1.  Permissions of Both Keys
2.  Placed at the correct subdirectory on Server
3.  Correct Subdirectory Permissions on Server
4.  Disable keyboard-interactive Password Authentication on Server

And you will be able to access your Server via ssh.

lk

---

### Post by DSn0wMan on 2011-06-08
This is for an ec2 instance on amazon aws. They provide you the private the key from a web interface, or you can generate your own (which I did) and upload the public key. So until the ssh command works I have no way of verifying anything on the server side.

I generated the key with...

ssh-keygen -t rsa

[email]grayjo@asg-jp95yc1:~/.ec[/email]2$ cat ~/.ssh/id_rsa
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEA2XLjeMxtzDa6Pt+04805beh5mY8vq2gN2EXvrB/eZsXfn619
FKi029RAajrTSteJJaivYuc2xoNmsMI4Q8NZrd2d+6rxo/EnhFeYd5uvlSAr8k/8
N8sEqTbjLGy57S14ang4Z3jW0dxQVABdM6/Nyu9JrbsY9jia5jpG2wgKDbAhIWq1
5H/GjFu5GjbXyUIRQyhRx7FVAKW/b5XHC0zE1NPQyKT7ZBP847Jpa3Taxdpu5Not
THCDStz2nCMm5TKbgeQmUi3zRQBO/RCbesH7dfQdW4xBTPMnUVYgJH+yv5CwvozC
3Lsf7Ma5FgljITrb2xRk4i3K3UCkL0iekMc3FwIDAQABAoIBABXNYidbf+rI1fW1
4mIw0oBFneOaqrHp9fFoWbaNX3Q4hMpyz6bBn5im+GpuSX8oizS+bA9jlWdkB2jT
oGaS8KvxG4T/R8kjRc4MJlpfvsQZ/K4H/QbvESGSQkbTA/VW6MrsEOO3Bvr1twwl
GTM0flLJmT6VEtSlKkrJLw+JB9EFV4zH0L9pUuEyxiL6VtweSxSjB+mBhXF3SYrT
MZnTVvvzW+/NFUal1tWji2MewvsTp10kA8twSls0jXUT0Y5ySYQ9C9xhQf/jEJQN
UnP2MYWgveioQ++9UBY/P/Y13xpfMqX6eKqc8rNO/+0lzxCaYl1rqRgyuhugZLDH
QlDlsjkCgYEA7SPwNgzMRYM2dWYGZFhwkkH+huAIOnEkDJUJuuXFC7MTzgEeeuak
q8+0v2NY6Njl+jlDfK+/WUajvPfBkS4W/gjETpOIKx9SgIfi1Oc5UiUC4UON0qsf
LFtMJIw4MLHg8QQdugHNZBdK7R9xS3CSFnA7fALBZpYF0lJGyjnIj4UCgYEA6r4J
9wxo9snjuOcDJdr5z50StRsbzRxGttyzOUKsgghL4Nb9yqO6I2ZB9VpEnUYbg7dq
3Qv0sCwVC5te8yrwcy6c28ekezyBpdGh7pOCNtyFucyP9cfrmKVDhGaw4UyECTy1
Sqdco1GUctuvB/k49bv1hkXajlcbBE8A2g+LGOsCgYEAhyxeJ6Eh61nA+CiA6kAT
YvtlR6J6bj3B674kvrlsmZ+pYVr38dx470rFX/cUXh4M8ZYkpvVTIGOIwBWF6+iW
yJVcuOGV0+bV01gh73QiE3Xvb1JfjD9o1JLyEz8uZGtwqlHLVBTk6/HvDr1GilcP
nuS4s5aqgXxwsxOdMHbBoTUCgYEAwWafOS69UA7YEuApxMecKARGhHX4Os5AKKq+
8r9O97c0JOOcp5arZjz6vNWJUHaRdrzoS4RtLbS0BiMVYI0RHCTcUWszxeD9BAwq
OTDJCMA5YPH77civ/8yxSuV8d7Md2aptxzsKZPhysQr0M0KPPk6EpALrZXi4pp0c
m4xQ0s8CgYAewMkmKfhoI1eD0Qd+foTwv/bAhd0mX2teXBGnssk46TMZn2VC0fko
lmEWYnzjv1PVucYpgpI0Z42yCLo1np6W52Kvk7JCWLoSFwkMxKn+REM6rgixGRUu
SpcWrLLQN52/ZmxEqYeE+XRF7Hf83AzmLb0IzzicT9BUKBgXCyw6Pg==
-----END RSA PRIVATE KEY-----
[email]grayjo@asg-jp95yc1:~/.ec[/email]2$ ls -ltr ~/.ssh
total 12
-rw-r--r-- 1 grayjo grayjo 3510 2011-05-12 10:35 known_hosts
-rw-r--r-- 1 grayjo grayjo  400 2011-06-08 12:25 id_rsa.pub
-rw------- 1 grayjo grayjo 1679 2011-06-08 12:25 id_rsa

I am sure it boils down to some config on the local ssh client, but I really have no idea what it might be.

---

### Post by lkraemer on 2011-06-09
For Version 1 Keys use:
```

ssh-keygen -1 -t rsa

```

OK, I think here is what needs to be done... Assuming Port 22 and
a Version 1 Private Key.
```

ssh -v -i ~/.ssh/identity -p 22 loginuser@hostname.domain
**OR**
ssh -v -i ~/.ssh/identity -p 22 loginuser@Server_IP_Address

```

Once you get it working just use:
```

ssh loginuser@hostname.Domain

```

Since the default is ~/.ssh/identity for protocol version 1......as
per the man page of ssh
```

man ssh

```

ie.......

 -i identity_file
Selects a file from which the identity (private key) for RSA or
DSA authentication is read.  The default is ~/.ssh/identity for
protocol version 1, and ~/.ssh/id_rsa and ~/.ssh/id_dsa for
protocol version 2.  Identity files may also be specified on a
perhost basis in the configuration file.  It is possible to have
multiple -i options (and multiple identities specified in
configuration files).  ssh will also try to load certificate
information from the filename obtained by appending -cert.pub
to identity filenames.

Also, if you posted the Private Key, please generate it again and
upload to the server keeping it under lock and key.  Don't post
it for others to use.  And if you generated with a Password, make sure
you always retain that Password.

Somewhere I read that Version 2 is DEFAULT, but I can't locate it now.
It's got to be on the man page......  FOUND IT!

[http://unixhelp.ed.ac.uk/CGI/man-cgi?ssh+1](http://unixhelp.ed.ac.uk/CGI/man-cgi?ssh+1)


lk

---

### Post by DSn0wMan on 2011-06-09
Looks like the problem is port 22 being blocked on inbound connections. So I can connect as you see in the debug output, but I can't get the public key response from the server.

Oddly enough a successful connection produces pretty much the same debug messages, only it doesn't hang halfway through.

---

