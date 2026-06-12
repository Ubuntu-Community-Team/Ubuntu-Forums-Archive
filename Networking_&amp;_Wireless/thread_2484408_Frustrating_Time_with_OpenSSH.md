---
title: "Frustrating Time with OpenSSH"
date: 2023-02-25
forum: Networking &amp; Wireless
---

### Post by Quarkrad on 2023-02-25
I have two ubuntu machines on a home lan.  One has the openssh client and the other openssh server.  I'm trying to copy the ssh key across from the client to the server but I cannot get around the permission denied re the password despite making changes to the sshd_config file on the server machine.  Any advice appreciated.

```
ssh-copy-id -i ~/.ssh/id_ecdsa.pub -p xxxxx 192.168.1.165
/usr/bin/ssh-copy-id: INFO: Source of key(s) to be installed: "/home/dad/.ssh/id_ecdsa.pub"
/usr/bin/ssh-copy-id: INFO: attempting to log in with the new key(s), to filter out any that are already installed
/usr/bin/ssh-copy-id: INFO: 1 key(s) remain to be installed -- if you are prompted now it is to install the new keys
dad@192.168.1.165's password: 
Permission denied, please try again.
dad@192.168.1.165's password:
```

---

### Post by Quarkrad on 2023-02-25
Doh .....  I was using the incorrect address:  I was using:

ssh-copy-id -i ~/.ssh/id_ecdsa.pub -p xxxxx 192.168.1.165

but I should have included the user name of the machine I was connecting to.

ssh-copy-id -i ~/.ssh/id_ecdsa.pub -p xxxxx liz@192.168.1.165

---

### Post by TheFu on 2023-02-25
To prevent issues like this, you might want to check out ~/.ssh/config settings.  You'll never need to remember an IP address, username or non-standard port again.  Plus, it is a good way to track when non-standard settings are needed for remote connections.

```
host xubu-2210
  user deploy2295
  hostname 172.22.22.250

host ubu-2204
  user u4497
  port 60022
  hostname 172.22.22.246

```
So, when any ssh-based tool uses 'ubu-2204', the IP, username and port will be automatically used.
```
$ ssh ubu-2204
$ rsync  ....... ubu-2204:
$ ssh-copy-id  ubu-2204
$ rdiff-backup ubu-2204:~/   /media/backups/ubu-2204
```
x2go, remote vim editing, sshfs, whatever.  Very handy, especially if you don't want to add the host and IP do your LAN DNS.

Other settings can be added, as documented in the ssh_config manpage. This is a client-side config file.

---

