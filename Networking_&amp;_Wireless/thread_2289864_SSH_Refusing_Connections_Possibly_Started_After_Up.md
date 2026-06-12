---
title: "SSH Refusing Connections Possibly Started After Upgrade to Vivid"
date: 2015-08-07
forum: Networking &amp; Wireless
---

### Post by douglas-marsh1 on 2015-08-07
I have had ssh & sftp working in the past, but now all connections are refused. It may have started after the upgrade to 15.04, but I'm not sure of that, Here's the output of ssh -vvvv user@255.255.255.255:
OpenSSH_6.7p1 Ubuntu-5ubuntu1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to 10.255.6.100 [10.255.6.100] port 22.
debug1: Connection established.
debug1: key_load_public: No such file or directory
debug1: identity file /home/dada/.ssh/id_rsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/dada/.ssh/id_rsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/dada/.ssh/id_dsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/dada/.ssh/id_dsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/dada/.ssh/id_ecdsa type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/dada/.ssh/id_ecdsa-cert type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/dada/.ssh/id_ed25519 type -1
debug1: key_load_public: No such file or directory
debug1: identity file /home/dada/.ssh/id_ed25519-cert type -1
debug1: Enabling compatibility mode for protocol 2.0
debug1: Local version string SSH-2.0-OpenSSH_6.7p1 Ubuntu-5ubuntu1
debug1: Remote protocol version 2.0, remote software version OpenSSH_6.7p1 Ubuntu-5ubuntu1
debug1: match: OpenSSH_6.7p1 Ubuntu-5ubuntu1 pat OpenSSH* compat 0x04000000
debug2: fd 3 setting O_NONBLOCK
debug1: SSH2_MSG_KEXINIT sent
Connection closed by 10.255.6.100
--------------------------------------------------------------------------------------------------------------------------------------------------------
Thanks for your help. Normally I could probably figure it out, but I had surgery recently and I'm really wiped out.

Doug

---

### Post by douglas-marsh1 on 2015-08-07
The problem was bad permission on a *_key file in /etc/ssh

---

### Post by ajgreeny on 2015-08-07
Please mark this as "Solved" from the Thread Tools menu at the top.

Don't worry; I have done this for you.

---

