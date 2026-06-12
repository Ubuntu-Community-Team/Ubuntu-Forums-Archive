---
title: "Not able to configure Internet"
date: 2008-08-30
forum: Networking &amp; Wireless
---

### Post by juzar on 2008-08-30
Hi guys,
I have recently installed Hardy Heron on my machine and I'm trying to configure the net. I have put in all the settings right in the network settings and also have set the network proxy correctly. Since I'm working on LAN out here and I'm able to ssh into other computers but from other computers I'm not able to ssh into my Hardy Heron. Tried everything but can't figure out the problem.
Any suggestions would be of great help. Thanks in advance.

---

### Post by RequinB4 on 2008-08-30
More information helps: Is the problem that you can't connect to the internet, or you can't setup a ssh network server?

Hold on, you're able to ssh into other computers but other computers can't ssh into yours?  By default, hardy has no open ports, so you have to setup a ssh server in order for your computer to accept the connection (otherwise its a security vurnurability).  

Can you connect to the internet via normal browsing (it seems you can because other computers seem to recognize yours, so the whole thing doesn't look like a connection problem at all)?

---

### Post by juzar on 2008-08-30
Hey Thanks but I'm still a bit confused how do I set up a ssh server? I'm new to Hardy Heron so an explicit list of steps would be helpful. Thanks.

---

### Post by DemonBob on 2008-08-30
sudo apt-get install ssh

---

### Post by juzar on 2008-08-30
It says ssh package not available. By the way I have installed from the UBUNTU 8.04 live cd which is a Desktop version. Do I have to install the server version for the ssh server to be installed and also for the internet to work correctly?

---

### Post by juzar on 2008-08-30
Hey sorry guys had typed in the wrong Gateway, now I'm able to connect to the internet via Hardy Heron, but still the problem regarding ssh persists. Still cant ssh from other machines into Hardy Heron any suggestions?

---

### Post by RequinB4 on 2008-08-30
[https://wiki.ubuntu.com/SSHHowto](https://wiki.ubuntu.com/SSHHowto)
Have fun:popcorn:

---

