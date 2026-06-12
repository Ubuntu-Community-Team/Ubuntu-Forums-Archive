---
title: "Remote desktop through internet"
date: 2007-04-18
forum: Networking &amp; Wireless
---

### Post by Chou on 2007-04-18
how do i set up the two routers? i know i have to port forward through port 23, but i cannot figure out how to do this. im using a matched pair of linksys routers.

---

### Post by dbott67 on 2007-04-18
Normally, you forward the external WAN port to the internal server IP address.  Then, when you want to connect remotely, you connect to the external IP of the router on the desired port.

You're probably not going to be using port 23 (telnet), perhaps 22 for SSH or maybe 5800 and 5900 for VNC/vino.  It depends on what type of access you want (remote desktop, shell, etc.).  What is it that you want to do?

If you want secure desktop access (GUI), then VNC/vino is what you want, but it is not very secure.  There are tutorials on how to setup [VNC over SSH]("http://linuxplanet.com/linuxplanet/tutorials/6155/1/"), but the performance can be poor.

A faster, secure way to access over SSH is [NX Machine.]("http://www.nomachine.com/")
Anyhow, if you can provide some details as to what you want to do, I can provide you with better advice.

-Dave

---

### Post by eponymous on 2007-04-19
just to piggyback on this for a second:
could this be accessed from a windows computer?

basically today when they released feisty i was thinking boy wouldn't it be great if i could start the download on my home PC from work via a remote session.

is that possible?

---

### Post by dbott67 on 2007-04-19
Absolutely.  From work I routinely SSH into my home computer to access files and what-not.

SSH is very secure and will give you command line access to use programs such as apt-get and aptitude (which you could use to install programs, etc.).  You would just need an SSH client on your Windows computer, such as [PuTTY]("http://www.chiark.greenend.org.uk/%7Esgtatham/putty/").  If you want to copy files back & forth, you can also download & install [WinSCP.]("http://winscp.net/eng/index.php")
.
NX Machine is a great solution for remote access, however, you cannot connect to the active desktop, so if you're trying to provide remote interactive troubleshooting, vino/VNC is a better option.  Having said that, if you are providing remote support & need to interact with the end-user, the Reverse VNC Howto in my signature works great for that type of application.

-Dave

---

