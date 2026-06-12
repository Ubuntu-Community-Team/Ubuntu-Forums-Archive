---
title: "How to set up ssh on guest machine (Linux 64b, on VirtualBox)"
date: 2016-04-23
forum: Networking &amp; Wireless
---

### Post by minh10 on 2016-04-23
I've created a guest OS on virtualbox. I would like to ssh into it from Putty (running on my host machine, Windows 10). I read that I should use port forwarding to establish connection. 

**VirtualBox is configured such: **
1. Attached to "NAT"
2. Port forwarding (Name/Protocol/Host IP/Host Port/Guest IP/Guest Port) : ssh/TCP//2500//22
[B]
On the guest OS: [/B]
I've sudo-installed "openssh-client" and "openssh-server" 

**On Putty: **
Host name: 127.0.0.1 
Port: 2500

I'm prompted "login name" -> I enter my user name, and password -> I enter the password that I use to log in. I get "access denied" message. 
Checking /var/log/auth.log for the corresponding log-in attempt, I see the following: 

pam_unix(sshd:auth): authentication failure; logname= uid=0 euid=0 tty=ssh ruser= rhost=10.0.2.2
Failed password for invalid user <my username> from 10.0.2.2 port 49241 ssh2

I'm not sure why I get "access denied"

---

### Post by SeijiSensei on 2016-04-23
You'll find it much easier if you use "bridged" networking rather than "NAT".  If you bridge the adapter, your virtual machine will get an IP address on the same network as the host computer.  All your other networked machines will be able to see it without having to forward ports through the host.  Right-click on the machine in VirtualBox manager and choose Settings > Network.  Change "NAT" to "Bridged Adapter".  Now boot the VM.  You should be able to ping its IP address from other machines on the network and connect to it with SSH.

---

### Post by minh10 on 2016-04-23
While using the "Bridged Adapter" option, I still get the same error in my log while trying to log in. 

Could it be my username? When prompted "login as:", I enter the account name which I usually log in. Password -> password for that account.

---

### Post by minh10 on 2016-04-23
Solved the problem by using my computer's name instead of the name that I saw in the log-in screen... strange.

---

