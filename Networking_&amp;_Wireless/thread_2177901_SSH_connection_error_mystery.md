---
title: "SSH connection error mystery"
date: 2013-09-30
forum: Networking &amp; Wireless
---

### Post by sean-fitzpatrick on 2013-09-30
I've run into a problem with ssh that has me completely stumped (and our department IT guy as well): Up until a few days ago I had no problems accessing my files on our departmental server (university math department, running Scientific Linux) using SSH from my Ubuntu box at home, and I had no problems mounting my user directory at work as a network drive.

As of a couple of days ago, running ssh [email]user@hostname.tld[/email] returns

ssh_exchange_identification: Connection closed by remote host

Running ssh -v hostname.tld returns

OpenSSH_6.1p1 Debian-4, OpenSSL 1.0.1c 10 May 2012
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug1: Connecting to gorilla.math.uwo.ca [129.100.75.10] port 22.
debug1: Connection established.
debug1: identity file /home/sean/.ssh/id_rsa type -1
debug1: identity file /home/sean/.ssh/id_rsa-cert type -1
debug1: identity file /home/sean/.ssh/id_dsa type -1
debug1: identity file /home/sean/.ssh/id_dsa-cert type -1
debug1: identity file /home/sean/.ssh/id_ecdsa type -1
debug1: identity file /home/sean/.ssh/id_ecdsa-cert type -1
ssh_exchange_identification: Connection closed by remote host


and trying to mount the network folder gives 

Oops! Something went wrong. Unhandled error message: SSH program unexpectedly exited

My first thought was that either the server was down, or I had some sort of incorrect firewall setting (although I had not made any changes to the firewall or router). It's not a problem connecting via SSH through my router/firewall though, since I can connect to other servers via SSH (I still have access to my account on the server at my last department), and the server I want to connect to is still up, since I can connect as follows:
1. SSH into old server. 
2. From old server, SSH into new server.

However, I can't log into the new server directly. I'm completely stumped. Any ideas?

---

### Post by SeijiSensei on 2013-10-01
Are you sure the new server has your public key in the appropriate authorized_keys file?

---

### Post by sean-fitzpatrick on 2013-10-04
Well I previously had no problem connecting to this server. I sorted it out though: my ISP's DCHP server reassigned me to an IP address that was on the block list at work. (As far as I know there's no way to change your dynamic IP address without MAC address spoofing or something like that.)

---

