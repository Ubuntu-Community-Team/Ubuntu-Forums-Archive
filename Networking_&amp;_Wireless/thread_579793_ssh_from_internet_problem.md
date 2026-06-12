---
title: "ssh from internet problem"
date: 2007-10-18
forum: Networking &amp; Wireless
---

### Post by benma on 2007-10-18
i have ssh installed on one of my network PCs. i can ssh to it from within the network, but when i ssh through my internet IP i don't seem to be able to connect. My DSL router has firewall but i forwarded port 22. when i scan ports from online site it says 22 is open. please help!

ssh -v      returns:

OpenSSH_4.6p1 Debian-5build1, OpenSSL 0.9.8e 23 Feb 2007
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug1: Connecting to 212.150.114.161 [212.150.114.161] port 22.
debug1: Connection established.
debug1: identity file /home/benny/.ssh/identity type -1
debug1: identity file /home/benny/.ssh/id_rsa type -1
debug1: identity file /home/benny/.ssh/id_dsa type -1
ssh_exchange_identification: Connection closed by remote host

---

### Post by scrooge_74 on 2007-10-18
Could it be you have the ssh server config to only allow connections from inside the LAN?

If the router is forwarding port 22 correctly you shold not have that kind of problems.

---

### Post by Whiffle on 2007-10-18
Which IP is it forwarding to and which IP is the computer?

---

### Post by benma on 2007-10-18
it forwards from internet IP to local IP.
The forward seems to be ok.
how is ssh blocking outside network connections? how do i allow it to accept outside connections?

---

### Post by tkharris on 2007-10-18
Check the /etc/hosts.deny and /etc/hosts.allow files.

---

### Post by benma on 2007-10-18
Both files are commented entirelly.

---

