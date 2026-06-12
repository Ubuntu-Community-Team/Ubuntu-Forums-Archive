---
title: "Dumbo ssh Client/Server Question"
date: 2020-11-16
forum: Networking &amp; Wireless
---

### Post by Quarkrad on 2020-11-16
I have successfully setup a remote ssh connection between my host pc and a virtual kvm on the same machine. Initially I had openssh-client and openssh-server installed on both machines.  Then, I thought perhaps I only need the client on my host machine and the server on the remote/kvm machine as this is the way it will always work.  I have set the server sshd_config file to listen on a non standard port but when connecting my host machine will not connect because the outgoing connection is defaulted to port 22.   I went to change ssh_config on the host machine but there is no ssh_config file in /etc/ssh.   Reading around some suggest I create a ssh_config file.  At this stage I'm not sure if I should have the client and server installed on both machines, create a ssh_config file on my openssh-client only host, or do something else on my host to divert port 22.  Is it the cast that if one is only ever going to connect to remotes (and not the other way round) you only need the openssh-client installed (and the openssh-server at the other end)?

---

### Post by The Cog on 2020-11-16
For the client on the host, you could create either /etc/ssh/ssh_config (affects all users), or you could create /home/$USER/.ssh/config (only affects that one user). If both exist, the global one is applied first, then the personal one (possibly overriding parts of the global one).
For the server on the guest, /etc/ssh/sshd_config is where you would change the listening port (and restart the service afterwards).
> Is it the cast that if one is only ever going to connect to remotes (and not the other way round) you only need the openssh-client installed (and the openssh-server at the other end)?Yes, that is the case.

---

### Post by Quarkrad on 2020-11-16
Thank you very much

---

