---
title: "Remote Desktop Works - now how about SSH?"
date: 2007-03-16
forum: Networking &amp; Wireless
---

### Post by Brian Boyko on 2007-03-16
My remote desktop works, so I think I've got this "port forwarding thing" down, but I can't seem to connect to Telnet, SSH, or FTP on my Ubuntu system.  Is there a daemon I need to activate or some service to turn on?

---

### Post by bernied on 2007-03-16
For ssh you need a server - openssh is the usual. It runs the sshd daemon which listens on port 22. It is a very good idea to familiarise yourself with the config file /etc/ssh/sshd_config and if you're opening yourself up to the big wide world then make sure you know how your security works.

Telnet and FTP are both considered a poor altenative to ssh, AFAIK.

---

### Post by dbott67 on 2007-03-17
As bernied states, openssh is what you need for access (telnet, ftp & others are quite insecure).  After installation, you would just use the command:
```
ssh user@ip.address.of.ubuntu
```If you're trying to access remotely, then you may need to forward port 22 on your router to the internal address of your Ubuntu computer.  Then, you would connect to your computer using this command:
```
ssh user@external.ip.of.router
```If you want remote desktop capabilities, you can try remote desktop, or VNC (insecure), VNC over SSH (secure but sluggish) or FreeNX (secure, fast and a beautiful thing!).

The nice thing about NX is that it just runs over port 22, so no issues with port-forwarding if you get ssh working correctly.

These are the steps that I performed in setting up NX and SSH:

For SSH:

1. Installed openssh server via Synaptic.
2. Configured and running on port 22
3. No other modifications

SSH can be used as a conduit to copy files between host & remote.  You would just need to install the appropriate packages depending on whether the remote is Windows or Linux, etc.  On my work computer (Windows XP) I installed the following software to access my home computer:

- PuTTY (ssh client for Windows)
- WinSCP3 (for remote GUI-based copying)
- NoMachine client

For NX:

1. Dowloaded the .DEB versions of NXserver, NX Client and NX Node from [www.nomachine.com]("http://www.nomachine.com/").
2. Installed the .DEBs in this order:
    - NX Node
    - NX Client
    - NX Server
3. Installed the NX Server following these instructions:
    - [http://www.nomachine.com/documents/server/install.html](http://www.nomachine.com/documents/server/install.html)
4. Configured the Nodes & added users following this document:
    - [http://www.nomachine.com/documentation/admin-guide.php](http://www.nomachine.com/documentation/admin-guide.php)

The one thing that I noticed is that it is better to create a new user account for NX rather than using my regular account.

Below are some screenshots of NX from Windows & Ubuntu, as well as my work computer running NX, SSH and SCP to my home computer.

-Dave

---

### Post by timcredible on 2007-03-17
to get telnet to work, you have to install telnetd and (i forget the specific dependency, there's some package that synaptic doesn't install by default, do a search to find it).  for ftp, install ftpd.

---

