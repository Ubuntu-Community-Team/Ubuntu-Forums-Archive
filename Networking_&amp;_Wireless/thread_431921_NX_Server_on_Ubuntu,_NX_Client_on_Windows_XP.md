---
title: "NX Server on Ubuntu, NX Client on Windows XP"
date: 2007-05-03
forum: Networking &amp; Wireless
---

### Post by jackmorelli on 2007-05-03
I'm pretty new to this whole linux thing, and i tried posting something on this yesterday in the beginner forum, but no one knows how to help yet.  so:

i installed nx server on my feisty computer according to the instructions at helpdot ubuntudot com slash community slash FreeNX.

i then installed the old nxclient on my windows machine.

```
when i try to connect, i get the following error on my client:
NX> 203 NXSSH running with pid: 3560
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: xxx.xx.xxx.xxx on port: 8888
Connection closed by Peer
```

sometimes this is replaced with:
Connection closed by xxx.xx.xxx.xxx 

can anyone offer any help?  

much thanks in advance, you rock,
jack

---

### Post by dannyboy79 on 2007-05-04
> **jackmorelli said:**
> I'm pretty new to this whole linux thing, and i tried posting something on this yesterday in the beginner forum, but no one knows how to help yet.  so:

i installed nx server on my feisty computer according to the instructions at helpdot ubuntudot com slash community slash FreeNX.

i then installed the old nxclient on my windows machine.

```
when i try to connect, i get the following error on my client:
NX> 203 NXSSH running with pid: 3560
NX> 285 Enabling check on switch command
NX> 285 Enabling skip of SSH config files
NX> 285 Setting the preferred NX options
NX> 200 Connected to address: xxx.xx.xxx.xxx on port: 8888
Connection closed by Peer
```

sometimes this is replaced with:
Connection closed by xxx.xx.xxx.xxx 

can anyone offer any help?  

much thanks in advance, you rock,
jack
can you successfully ssh into the box? when you're on the server, what does this return?

sudo nxserver -status

also, i tried to find the guide you used but when I go to help.ubuntu.com/community/FreeNX I get nothing! I wouldn't use the FreeNX, I would use the nxserver, nxnode, and the nxclient. I don't know what you mean about the "old" client either? have you tried this guide: [http://ubuntuforums.org/showthread.php?t=204976](http://ubuntuforums.org/showthread.php?t=204976)

starting at thread #2.

---

### Post by nero2150 on 2007-05-04
Make sure you forward the port 8888 in your router or firewall.
 
Also I m not sure but I think port 8888 might be used for something else or use port 22 its the default one.
In my case I cannot use any other port than 22 if there is anyone who could help to change the port no. I did try editing  /etc/ssh/sshd_config and restart ssh but without luck 

sudo /usr/NX/bin/nxserver --status 
gives 

NX> 900 ssh: connect to host 127.0.0.1 port 22: Connection refused
NX> 110 NX Server is stopped.
NX> 999 Bye.
:confused:

nevermind I ve found out 

[http://ubuntuforums.org/showthread.php?t=204976&page=3](http://ubuntuforums.org/showthread.php?t=204976&page=3)

---

### Post by jackmorelli on 2007-05-04
thank you both for your help, much appreciated it.

i imagine it had to do with port forwarding, when i switched it back to the default port 22, it worked well.

and by the "old" client, i just meant the 1.5.0.114 nxclient instead of the newest 2.0.x.x nxclient software versions.  

thanks again!!  problem solved!!
jack

---

