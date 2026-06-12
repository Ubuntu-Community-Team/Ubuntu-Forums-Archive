---
title: "Local network down after update - Internet up. Suggestions?"
date: 2008-03-13
forum: Networking &amp; Wireless
---

### Post by smoore98 on 2008-03-13
I am running 7.10 64-bit server version with Gnome 2.20 on an AMD64 machine. I have a built-in NIC card and two additional NIC cards that I installed after purchase. I have no wireless connection, only hardwired 100/1000GB cards. All are using static IP addresses. I use this as a vmware server. 

Everything has been working great until 03/09, when I decided to use update manager to check and install any of the latest updates. I have not done this in about 2 months (could be longer). I noticed after upgrading and rebooting that I could no longer SSH into the machine remotely. I found all ports from the local subnet not responding. However, on UBUNTU I can still get to the Internet, and connect to other machines as long I connect through the internet. Wireshark shows no packets hitting or leaving any NIC when I am trying to reach  another machine on the local network. The only thing that changed was the updates.

I viewed the update log for 03/09 and noticed a new network manager version was one of the updates. While I am not positive, I think this is the source of the trouble. My log shows:

2008-03-09 18:28:29 status installed network-manager 0.6.5-0ubuntu16.7.10.0

There are other possibilities. It installed samba-common 3.0.26a-1ubuntu2.3, smbfs 3.0.26a-1ubuntu2.3, libsmbclient 3.0.26a-1ubuntu2.3, ssh 1:4.6p1-5ubuntu0.1 and a couple of related ones, but if SSH were the problem I would think that only port 22 would be the problem, and it is all ports. Same with Samba. BUT - I am not an UBUNTU expert, and know just enough to keep things up and running (most of the time - until now). 

I checked all the IP addresses and network configuration of each NIC and everything looks exactly the same as before the update. Can anyone tell me if I am on the right track or if there is something I else I need to look at? It must be something simple because the Internet connection works great. 

If the new network manager package is the issue, what is the easiest way to back out of this specific package? I have never had to back out of an update.

Thanks in advance!

Scott

---

### Post by handydan918 on 2008-03-13
How are your firewall settings?

---

### Post by smoore98 on 2008-03-13
all ports are open.

---

### Post by handydan918 on 2008-03-13
Do all your boxen show smbd and sshd installed (and running)?

---

### Post by smoore98 on 2008-03-13
They show installed in package manager, SSH shows running in the Services Settings and ps - ef shows ssh-agent and smbd processes running. Again, nothing shows to have changed, just the updates have been applied. I am using Gnome and on the graphical "Network Tools" application I can connect/ping/tracert between the individual NICs, like from ip 110 to 101 or 102 (just showing the last octet in the subnet there).  A port scan on 110 shows all the ports open. Subnet masks look fine.

Any other ideas?

S

---

### Post by smoore98 on 2008-03-14
Hmm... well, I may not be able to solve my issue here. perhaps I have not provided enough information? 

Can anyone point me to a place that shows how to back out of a specific package to the previous version?

Thanks,
Scott

---

### Post by handydan918 on 2008-03-15
> **smoore98 said:**
> They show installed in package manager, SSH shows running in the Services Settings and ps - ef shows ssh-agent and smbd processes running. Again, nothing shows to have changed, just the updates have been applied. I am using Gnome and on the graphical "Network Tools" application I can connect/ping/tracert between the individual NICs, like from ip 110 to 101 or 102 (just showing the last octet in the subnet there).  A port scan on 110 shows all the ports open. Subnet masks look fine.

Any other ideas?

S

Just one: IIRC, sshd MUST be running in order to ssh in. Just do ```
sudo apt-get install openssh-server
```
and let's see what happens...

---

### Post by smoore98 on 2008-03-15
It says it is alreasdy the newest version, set to manual insalled. 
S

---

### Post by smoore98 on 2008-03-15
is there any way to simply back out of a package?
S

---

### Post by handydan918 on 2008-03-15
Sure, just search installed packages in synaptic, and uninstall it. If you do top or ps -aux , do you see sshd running?

---

### Post by smoore98 on 2008-03-15
That is not what I asked. If I uninstall the package then does it revert back to the previous version? Or do I have to install the older version manually after this?

This is NOT an SSH issue. I have at least three other ways that I used to connect to this machine. FTP, Vmware console, web, webmin on a different port, etc. None of it works. No ping, no tracert, nothing in, nothing out. It is as if the network cable has been unplugged. No packets on the sniffer trace. This is all on the LOCAL SUBNET only. I can open a browser and surf the web.

All the ports are open. There is no firewalll. VM's are running and everything is still set to just before the update. I was hoping that instead of trying to troubleshoot specific ports like SSH, someone had more information about the latest NETWORK MANAGER package and if there are known problems with it hosing up the local network connections, and if so, the easiest way to back out of it. I am especially concerned that possibly the package updater may have installed the wrong version of the network manager package. I am on a 64-bit version of the 7.10 server and perhaps it installed the wrong version for that. It's just a guess.

Again - nothing else has changed. I have not modified any configuration files, the process table has all the stuff running, it just won't connect, ping, etc the local subnet.

S

---

