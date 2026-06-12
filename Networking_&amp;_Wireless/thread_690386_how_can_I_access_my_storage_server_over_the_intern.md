---
title: "how can I access my storage server over the internet?"
date: 2008-02-07
forum: Networking &amp; Wireless
---

### Post by grs on 2008-02-07
I have a small network at home of one storage server (Running FreeNAS) and three PC's all linked through a Linksys WRT45G Router. I want to set it up so that I can access the storage server over the internet when away from home, how can I set this up? Should I setup a PC to act as a "gateway"? I have no experience with Ubuntu as such, I just figured it would be a cheaper OS than Windows!
I already have an account with logmein.com I just want to hear of alternatives.

---

### Post by wiseguyxp on 2008-02-07
FTP would be a good option.  You could run an FTP server on a computer in the network with the root dir being the NAS share, then port forward 20-21 to the computer hosting the FTP server.

---

### Post by grs on 2008-02-08
Are there any guides to setting up FTP servers with Ubuntu?

---

### Post by ruy_lopez on 2008-02-08
SSH would work well. Just mount the network drive on one of your PCs, then make SSH available on the same PC.


To set up SSH:

```
sudo apt-get install ssh
```


Make sure your password is difficult, use numbers and letters and symbols.


Then you enable port forwarding on the router, for port 22, and point the address at the pc which is running SSH.

Once you have SSH setup properly you can use either SSH or SFTP, to access the files.

See this howto.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#SSH_Server]("http://ubuntuguide.org/wiki/Ubuntu_Edgy#SSH_Server")


I should add: you can setup a dynamic domain name at noip (google: noip) that will always point to your router. It's also a good idea to make the pc running SSH have a static IP, otherwise it might change from time to time and break the port forwarding.

---

