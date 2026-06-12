---
title: "Public IP Account Credentials Error"
date: 2019-10-12
forum: Networking &amp; Wireless
---

### Post by andrewak2 on 2019-10-12
Hi, I am using Ubuntu version 18.04 LTS, and i have been suffering confirming issues through the internet. I have enabled ssh, and if I attempt a login using my private IP address, it works. However, if I use my public IP address, even if i enter the correct username and password, it says the my password is incorrect. Can someone help me?

---

### Post by The Cog on 2019-10-12
Some more details might help. 
1: Is Ubuntu the server (as opposed to the client)?
2: Using your private / public address: Is this changing the address you are connecting to (as opposed to the address you are calling from)?
3: Assuming my guesses above are correct, are you still on the private network when you try to connect to the public address?

It may be worth checking the server configuration (usually /etc/ssh/sshd_config) to see if there are any restrictions on where users can log in from, e.g. only allowing logins from the local network, e.g. username@192.168.0.0/24

---

### Post by TheFu on 2019-10-12
Many home routers prevent connections to their public IP from inside the LAN they manage. It is a security thing.  Might be possible to disable this setting, but IDK.

Can you telnet to the ssh port and see the ssh header?
```
$ telnet algo333 50020
Trying 50.33.33.333...
Connected to algo333.
Escape character is '^]'.
SSH-2.0-OpenSSH_7.2p2 Ubuntu-4ubuntu2.8
^C
Connection closed by foreign host.
```
IPs and hostnames changed to protect the guilty. ;)

You can also use **ssh -vvvv** to get more details about the connection attempt.

---

