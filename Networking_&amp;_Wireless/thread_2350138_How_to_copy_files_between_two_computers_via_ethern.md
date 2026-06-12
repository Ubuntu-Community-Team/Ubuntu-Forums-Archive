---
title: "How to copy files between two computers via ethernet cable"
date: 2017-01-21
forum: Networking &amp; Wireless
---

### Post by tevang2 on 2017-01-21
Greetings,

I followed the instructions in this page to connect my two laptops with an ethernet cable:

[http://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router](http://askubuntu.com/questions/22835/how-to-network-two-ubuntu-computers-using-ethernet-without-a-router)

Then I did:

$ ping 10.0.0.2
PING 10.0.0.2 (10.0.0.2) 56(84) bytes of data.
64 bytes from 10.0.0.2: icmp_seq=1 ttl=64 time=0.923 ms
64 bytes from 10.0.0.2: icmp_seq=2 ttl=64 time=0.539 ms

and everything looked fine. Now the important question: how can I copy the files from the second laptop (10.0.0.2) to the first (10.0.0.1)???

---

### Post by DuckHook on 2017-01-21
Although your two computers are now physically networked, one must still act as a server and the other as a client. Unlike Windows, Ubuntu does not come with any server software preloaded. So you must choose a server (and possibly client) protocol, add the server (and possibly client) package for that protocol, configure the server with an export point, then mount that export in the client as a networked share.

The server choices in Ubuntu are excellent. Almost too good because the wealth of choices is confusing. I will list some of the most popular and then recommend what I feel is the best:

[list=1]
[*]Samba is very popular because it uses the Microsoft network file protocol. A samba server can be read by a Windows machine.
[*]NFS is a very fast, robust and well-behaved protocol that is the go-to protocol for protected firewalled LANs. It is the one I use in my home network.
[*]FTP is a primitive, easy, quick-and-dirty protocol that has absolutely no security. One can harden it by adding various security protocols, but then it's no longer easy or quick-and-dirty.
[*]SSH is both secure and relatively easy to configure, and is beloved by Linux power-users. It is a workhorse protocol that allows safe remote access of computers.
[/list]
There are others, but any of the above four should get you where you want to go.

Of the four, I would recommend SSH for two reasons:

[list=1]
[*]It is relatively easy to install and get working,
[*]It has the additional benefit of giving you full and secure remote access to your other machine that is, frankly, a great security habit to cultivate.
[/list]

Instructions for installing openssh-server are here: [https://help.ubuntu.com/14.04/serverguide/openssh-server.html](https://help.ubuntu.com/14.04/serverguide/openssh-server.html)
Instructions for installing SSHFS are here: [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

If running Ubuntu, openssh-client should already be installed as part of your default install. If all you want to do is a one-time file copy, then it probably isn't necessary to create keys. But if you find SSH as useful as most Linux power-users, then it is a really good idea to create key-pairs and disable password access.

Note that there is a simpler option using SSH that doesn't require the installation of SSHFS at all. After installing openssh-server, you can use the command, *scp* to copy all files. Instructions here: [https://help.ubuntu.com/community/SSH/TransferFiles](https://help.ubuntu.com/community/SSH/TransferFiles)

There is a GUI interface for *scp* that I've heard about but never used, called *secpanel*:```
sudo apt install secpanel
```

---

### Post by SeijiSensei on 2017-01-21
If you run openssh-server on both machines, you can copy files with the scp command:

```
scp /path/to/source server_ip:/path/to/target
```

It works just the same way cp works on the local machine.  If you [create keys]("https://help.ubuntu.com/community/SSH/OpenSSH/Keys") as DuckHook suggests, you won't need to enter a password just to copy a file.

For bulk copies, I recommend rsync which also uses SSH:

```
cd /
rsync -av home server_ip:/path/to/target/

```

will create an image of a machine's /home directory as /path/to/target/home on the other machine. If you add "n" to the options list ("sudo rsync -avn") rsync will report the files it will transfer but not copy them.

---

### Post by justincase2 on 2017-01-21
For a beginner, the `scp` command seems the easiest for me at least.

---

### Post by SeijiSensei on 2017-01-21
One other thing.... If the user on the source machine is not the same as the user on the target, you'll need to use
```
scp /path/to/source remote_user@server:/path/to/target
```
You'll need to authenticate as remote_user by some means, either a password on the target or via SSH keys.

---

### Post by tevang2 on 2017-01-22
Thank you guys! I am not a beginner at all :) I just hadn't openssh-client installed on my second laptop and scp was not working.

---

