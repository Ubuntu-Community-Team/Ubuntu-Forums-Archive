---
title: "ssh_exchange_identification: Connection closed by remote host"
date: 2016-05-30
forum: Networking &amp; Wireless
---

### Post by Harsh_Singh on 2016-05-30
Sorry if already posted..
I am new to Linux and SSH..

I have installed ssh using "** sudo apt-get install openssh-server**"

Then i tried to login to another user account of same machine from root using ssh command

[B]ssh user_name@ip_address

[/B]it is giving a single line error..
[B]
ssh_exchange_identification: Connection closed by remote host

[/B]Please help. I am stuck on this.[B]:(
[/B]

---

### Post by houstonbofh on 2016-05-30
That is osten from a hosts.allow / hosts.deny on the server side.  It can also be old ssl on one side or the other.  Try to ssh from your new machine to itself.  If it works, you know it is likely not on your client side.

---

### Post by Harsh_Singh on 2016-05-31
Thanks for reply...
I have tried that but it is giving the same error..
I just reinstalled ssh now i am getting
"ssh: connect to host 192.168.0.103 port 22: Connection refused" error please help.

---

### Post by houstonbofh on 2016-05-31
Show the output of "dpkg -l | grep ssh" so we know what you have installed.  It should show something like;
```

ii  libssh-4:amd64                              0.6.3-4.3                                           amd64        tiny C SSH library (OpenSSL flavor)
ii  libssh-gcrypt-4:amd64                       0.6.3-4.3                                           amd64        tiny C SSH library (gcrypt flavor)
ii  openssh-client                              1:7.2p2-4                                           amd64        secure shell (SSH) client, for secure access to remote machines
ii  openssh-server                              1:7.2p2-4                                           amd64        secure shell (SSH) server, for secure access from remote machines
ii  openssh-sftp-server                         1:7.2p2-4                                           amd64        secure shell (SSH) sftp server module, for SFTP access from remote machines
ii  ssh                                         1:7.2p2-4                                           all          secure shell client and server (metapackage)
ii  ssh-askpass-gnome                           1:7.2p2-4                                           amd64        interactive X program to prompt users for a passphrase for ssh-add
ii  ssh-import-id                               5.5-0ubuntu1                                        all          securely retrieve an SSH public key and install it locally

```

---

