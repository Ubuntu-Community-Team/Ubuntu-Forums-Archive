---
title: "using ssh"
date: 2008-12-11
forum: New to Ubuntu
---

### Post by pshootr on 2008-12-11
I want to use putty to connect to my server, but I am unsure how to do this. I read on a site that "echo server1.example.com > /etc/hostname
/etc/init.d/hostname.sh start" should start ssh on the server. But when I put in "echo server1.example.com > /etc/hostname" It tells me permission denied. I am logged in as root when I try this. Any ideahs?

---

### Post by bodhi.zazen on 2008-12-11
No, that is not how ssh works.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Make darned sure you secure the server:

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by handydan918 on 2008-12-11
> **pshootr said:**
> I want to use putty to connect to my server, but I am unsure how to do this. I read on a site that "echo server1.example.com > /etc/hostnameFirst, are you using windows? If not, you don't need puTTY. Second, the "echo" command you quoted contains "server1.example.com" which probably isn't exactly what you want to paste into a terminal, unless your server is really assigned the name of "hostname"...> 
/etc/init.d/hostname.sh start" should start ssh on the server.Not as far as I know...try ```
sudo /etc/init.d/ssh start
```>  But when I put in "echo server1.example.com > /etc/hostname" It tells me permission denied. I am logged in as root when I try this. Any ideahs?
Yeah, tell me what you mean by "I am logged in as root..."

---

### Post by pshootr on 2008-12-11
> **bodhi.zazen said:**
> No, that is not how ssh works.

[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)

Make darned sure you secure the server:

[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

Thank you for the links/heads up. All pc's on the network are behind a router. Is this secure enough?

---

### Post by bodhi.zazen on 2008-12-11
> **pshootr said:**
> Thank you for the links/heads up. All pc's on the network are behind a router. Is this secure enough?

Only if :

1. You trust the users on your LAN.

And

2. You do not forward port 22 (or other port if you changed the port) from your server to the internet.

---

### Post by pshootr on 2008-12-11
> **handydan918 said:**
> First, are you using windows? If not, you don't need puTTY. Second, the "echo" command you quoted contains "server1.example.com" which probably isn't exactly what you want to paste into a terminal, unless your server is really assigned the name of "hostname"...Not as far as I know...try ```
sudo /etc/init.d/ssh start
```
Yeah, tell me what you mean by "I am logged in as root..."

After I installed the server I set password for root. So when I log on I use root instead of micky. I assume this means I won't have to type su or sudo before each command?

---

### Post by albinootje on 2008-12-11
As long as your users refrain from using simple passwords, and you do some work by reading how to secure your ssh-connections, and if you're router is not suffering from some well-known security-bug in its firmware, then you're in pretty good shape.
Of course you should also check your security-updates in Ubuntu from time to time.

---

### Post by pshootr on 2008-12-11
> **bodhi.zazen said:**
> Only if :

1. You trust the users on your LAN.

And

2. You do not forward port 22 (or other port if you changed the port) from your server to the internet.

Ok good thanks. Yeah this is a home network.

---

### Post by pshootr on 2008-12-11
> **handydan918 said:**
> First, are you using windows? If not, you don't need puTTY. Second, the "echo" command you quoted contains "server1.example.com" which probably isn't exactly what you want to paste into a terminal, unless your server is really assigned the name of "hostname"...Not as far as I know...try ```
sudo /etc/init.d/ssh start
```
Yeah, tell me what you mean by "I am logged in as root..."

I want to use windows to connect to my ubuntu server using ssh. 

I assighned a hostname during the install of the server, and used it in the command.

when I try ```
sudo /etc/init.d/ssh start
``` I get "no such directory. Though I chose to install ssh during server install. I don't get it.

---

### Post by albinootje on 2008-12-11
sudo apt-get install ssh
will install the openssh-server package

---

### Post by pshootr on 2008-12-11
> **albinootje said:**
> sudo apt-get install ssh
will install the openssh-server package

Seems that ssh did not intall for some reason even though I chose to install it during the server install. May be  the files are not on the disk and NEED to be downloaded. Anyway, thanks for the tip. I have another problem though, I can not access the net from the server yet. I have configured my network and can ping the router from the server, but no internet. I assume it is a dns issue. I am a little confused here. I added "nameserver 72.43.76.132" which is the dns server other pc's use to access the net. still no go.

---

### Post by albinootje on 2008-12-11
If you think it's a DNS-issue, then what gives pinging a public ip-address (which normally answer ping-requests) ?

---

