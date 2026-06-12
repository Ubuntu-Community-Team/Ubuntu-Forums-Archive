---
title: "&quot;Simple&quot; file sharing..."
date: 2007-05-05
forum: Networking &amp; Wireless
---

### Post by tpg on 2007-05-05
I have two computers, one running Kubuntu Feisty, the other openSuSE 10.2, and I want to back up data from one (the Feisty machine) to the other. Not wanting to waste CDs, I would like to connect the computers together with an ethernet crossover cable, and then transfer files. I am having two problems:

1) The machine running Feisty doesn't seem to like the ethernet connection. KNetworkManager does not seem to notice it. ifconfig reports that eth0:avah has been given an IP address, but not eth0 itself. (N.B. - SuSE machine reports that it can connect to the wired network)

2) I am not sure what the best method of transferring files is. I've heard that NFS is supposed to be good (although I know nothing about it). I've also tried Samba, which worked for a few minutes, but now when I try to access the share I set up from either computer it gives me a "Timeout on server" error message.

Anyone have any ideas? Thanks in advance.

---

### Post by tpg on 2007-05-05
Well, I seem to have got it to work, although I don't know how! :) 

Rebooting my Feisty machine seemed to fix the problem about Samba "server time out". It also seems that even though eth0 doesn't have an IP address, I can use the one assigned to eth0:avah, and that seems to work.

I'd still welcome comments about how to share files over LAN a bit more reliably (i.e. not have to spend about 10 minutes rebooting both machines / reconfiguring etc.each time I want to use the share)

---

### Post by TheWizzard on 2007-05-05
you should be able to make samba reliable. mine is working perfectly.

---

