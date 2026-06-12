---
title: "Connection refused SSH and FTP"
date: 2015-05-29
forum: Networking &amp; Wireless
---

### Post by MrDaves on 2015-05-29
Good morning,

After some research on Google, I didn't find any solution for my problem :(
I recently installed nginx for my web server but suddenly, impossible to connect it trough SSH ! Putty from windows 7 says : Network error: Connection refused !
And localy, when I do "ssh localhost" :
ssh: connect to host localhost port 22: Connection refused
And my FTP server also block any connexion :(
But the nginx I installed and configured work and I can browse my website from anywhere !

Any idea ?
Thank you,
MrDaves

Tech specs :
Hardware :
It is a ODROID c1 with eMMC 8gb + external HDD

[COLOR=#333333][FONT=monospace]lsb_release -a :
[/FONT][/COLOR]No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 14.04.2 LTS
Release 14.04
Codename: trusty

ifconfig :
eth0      Link encap:Ethernet  HWaddr 00:1e:06:c3:95:c2  
          inet addr:192.168.0.13  Bcast:192.168.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:6ff:fec3:95c2/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:27518 errors:0 dropped:0 overruns:0 frame:0
          TX packets:5037 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:5367401 (5.3 MB)  TX bytes:1925073 (1.9 MB)
          Interrupt:40

---

### Post by Lars Noodén on 2015-05-29
What is the packet filter doing?

```

sudo ufw status verbose

```

It should show that port 22 for SSH and ports 80 and 443 for HTTP and HTTPS are open.  If not they need to be opened.

```

sudo ufw allow in ssh

```

---

### Post by MrDaves on 2015-06-15
I didn't install any firewall as I am behind a rooter that filter.
I cleared the problem by reinstalling OPENssh but my FTP still doesn't work... I tried to reinstall it but apparently, I don't have any ftp packet installed...

---

### Post by Lars Noodén on 2015-06-15
If you have SSH working then [you probably don't need FTP](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) because OpenSSH-server has SFTP built in.  If you use SFTP, you will have a secure connection, unlike what you get with FTP.  You can use SFTP with FileZilla or even [Nautilus](https://www.youtube.com/watch?v=9S4DV1PluzA) and the other file managers.  If SFTP works for you, then it's a good idea to remove FTP.

---

