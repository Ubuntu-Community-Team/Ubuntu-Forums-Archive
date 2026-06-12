---
title: "SSH from Ubuntu (7.04, ix86) to Debian (4.0, Sparc) - Connection Closed"
date: 2007-08-02
forum: Networking &amp; Wireless
---

### Post by Kalman on 2007-08-02
Good evening,

I am trying to establish an SSH connection from an Ubuntu 7.04 (ix86) system to a Debian 4.0 (Sparc) system on a LAN.

The first attempt resulted in the following message,

[COLOR="Blue"]The authenticity of host '10.0.0.7 (10.0.0.7)' can't be established.
RSA key fingerprint is 44:da:4b:d7:43:de:ed:73:4b:3a:cc:52:69:25:6f:11.
Are you sure you want to continue connecting (yes/no)? yes
Warning: Permanently added '10.0.0.7' (RSA) to the list of known hosts.
Connection closed by 10.0.0.7[/COLOR]

The second attempt (with the '~/.ssh/known_hosts' file now in place) results in the message,

[COLOR="Blue"]Connection closed by 10.0.0.7[/COLOR]

The SSHD daemon is active on the Debian system using the default port of 22.  Both systems have default LiveCD installations with the required SSH(D) packages installed.  Both systems use static IP address.  No modifications to the SSH(D) configuration files have been made.

I can establish SSH sessions from a default install of openSUSE 10.1 and using default Putty settings from Windows to the Debian system.  Only from Ubuntu I can not create an SSH connection.

Any insights or suggestions are greatly appreciated.


Kalman.

---

