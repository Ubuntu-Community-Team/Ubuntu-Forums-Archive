---
title: "How do i actually run ssh"
date: 2007-10-01
forum: Networking &amp; Wireless
---

### Post by Cubedude04 on 2007-10-01
Hey. I installed ssh awhile ago and i believe i somehow turned it off 

I am trying to connect to it using putty on my windows computer but i keep getting a timed out error and i believe it's because it's not currently running on my ubuntu computer

So how would i check ssh is running


Thanks in advance

---

### Post by Hoff-Z on 2007-10-01
I think sshd (SSH daemon) must be running on your Ubuntu computer.

Try this in the terminal to see if it's running:
```
ps aux | grep sshd
```

A good way to debug an ssh connection attempt is to use the -v option. Use this syntax next time you try to log on:
```
ssh -vv username@host
```

---

### Post by hyper_ch on 2007-10-01
if you want to ssh into your box tehn you need the ssh server installed:

```

sudo apt-get install openssh-server

```

---

### Post by Cubedude04 on 2007-10-01
Okie thanks for that. It turns out that wasn't the problem but i think i know what it is now but can't work out how to fix it

I set up on my Router (DI-524UP) to give myself a static IP addess under DHCP which is as follows
	Prothex-Desktop	192.168.0.102

Under Virtual Server i have set 

prothexssh	192.168.0.102	TCP 22/22	Always

And under DDNS i have set

Enabled
prothex.dyndns.org
Cubedude04
**************

Under my account on dyndns.com i have set the following options

prothex.dyndns.org  	Host  	 121.209.72.41

Now when i try to connect with SSH i get this problem

james@Prothex-Desktop:~$ ssh -vv [email]james@prothex.dyndns.org[/email]
OpenSSH_4.3p2 Debian-8ubuntu1, OpenSSL 0.9.8c 05 Sep 2006
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting to prothex.dyndns.org [192.168.100.11] port 22.
debug1: connect to address 192.168.100.11 port 22: Connection timed out
ssh: connect to host prothex.dyndns.org port 22: Connection timed out
james@Prothex-Desktop:~$ 


As you can see it's trying to connect to 192.168.100.11

I have no idea where it is getting that IP address from and haven't set that as anything in my previous settings 

Does anyone have any idea what's happening

Thanks in advance







EDIT:

I found under 
DHCP Server
The DI-524UP can be setup as a DHCP Server to distribute IP addresses to the LAN network.
DHCP Server 	Enabled  Disabled
Starting IP Address 	192 .  168 .  0 . 100

I changed that to 192.168.0.102 and it works. Is that okay changing that or should i have left it alone

---

### Post by hyper_ch on 2007-10-01
if you are on the lan, you don't use the dyndns service... you just use the internal IP for connection.

---

### Post by Cubedude04 on 2007-10-01
I am testing it on a lan but trying to use the same method that would work on an outside connection

---

### Post by hyper_ch on 2007-10-01
you need to be outside the lan in order to use the dyn-ip service. otherwise it will only mix things up.

---

