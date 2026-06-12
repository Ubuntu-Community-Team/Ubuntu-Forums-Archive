---
title: "How do I telnet (or ssh) to my Ubuntu desktop?"
date: 2006-10-16
forum: Networking &amp; Wireless
---

### Post by xp_newbie on 2006-10-16
I installed Ubuntu 6.0.6 desktop and it works great (I am writing this message via this Ubuntu installation).

I can even ping it from other machines on my LAN, but... I cannot telnet or ssh to it. :( 

To the best of my knowledge, no firewall is running on this Ubuntu installation.

What do I need to do to telnet or ssh to my Ubuntu desktop?

Thanks!
Alex

---

### Post by feathers on 2006-10-16
I think it is not installed by default. sudo apt-get install ssh and you can start connecting.

---

### Post by girishv on 2006-10-16
Hi,

ping just tells whether the machine is alive or not. To connect to it through telnet/ssh, corresponding servers should be running. Check whether the servers are installed and running
dpkg -l | grep ssh
should give some thing like  openssh-server, or else install open-ssh with
sudo apt-get install openssh-server

Girish

---

### Post by xp_newbie on 2006-10-16
Thank you all who responded. I just installed openssh-server using Synaptic and it works out-of-the-box (i.e. not only it downloaded and copied the files the appropriate directories, it also configured it as a service and started running it without any need to reboot).

---

