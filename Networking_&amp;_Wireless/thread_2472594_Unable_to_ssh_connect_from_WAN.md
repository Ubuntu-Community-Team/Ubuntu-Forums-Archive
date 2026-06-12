---
title: "Unable to ssh connect from WAN"
date: 2022-03-05
forum: Networking &amp; Wireless
---

### Post by catav on 2022-03-05
Hi,
I've a physical home server runs on Ubuntu 20.04.4 LTS. Everything works as expected till I change my ISP. After that I can't connect to my server from WAN. In LAN there is no problem.
```

ps -A | grep sshd
1804803 ?        00:00:00 sshd

sudo ss -lnp | grep sshd
tcp            LISTEN            0            128
0.0.0.0:22        0.0.0.0:*        users:(("sshd",pid=1790621,fd=3))                                              
tcp            LISTEN            0            128
[::]:22        [::]:*                 users:(("sshd",pid=1790621,fd=4))
```

On modem/router port 22 forwarded to the server

On LAN and WAN same client machine used

----------------------On Server---------------------
```
ssh user@localhost
Last login: Fri Mar  4 17:42:10 2022 from 192.168.1.33
Welcome to fish, the friendly interactive shell
Type `help` for instructions on how to use fish
user@server ~>
---
ssh user@127.0.0.1
Last login: Fri Mar  4 19:49:19 2022 from 127.0.0.1
Welcome to fish, the friendly interactive shell
Type `help` for instructions on how to use fish
user@server ~>
---
ssh user@192.168.1.25 #(server LAN IP)
Last login: Fri Mar  4 19:50:18 2022 from 127.0.0.1
Welcome to fish, the friendly interactive shell
Type `help` for instructions on how to use fish
user@server ~>
---
ssh user@domain.ltd #(sever domain name)
Last login: Fri Mar  4 19:50:51 2022 from 192.168.1.25
Welcome to fish, the friendly interactive shell
Type `help` for instructions on how to use fish
user@server ~>
```

---------------------On LAN Client-------------------
```
ssh user@192.168.1.25
Last login: Fri Mar  4 19:51:16 2022 from 192.168.1.25
Welcome to fish, the friendly interactive shell
Type `help` for instructions on how to use fish
user@client_on_LAN ~>
---
ssh user@domain.ltd
Last login: Fri Mar  4 19:59:53 2022 from 192.168.1.33
Welcome to fish, the friendly interactive shell
Type `help` for instructions on how to use fish
user@client_on_LAN ~>
```

---------------------On WAN Client-------------------
```
ssh user@domain.ltd
ssh: connect to host domain.ltd port 22: Connection timed out
user@client_on_WAN ~ [255]>
---
ssh user@domain.ltd -vvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvvv
OpenSSH_8.2p1 Ubuntu-4ubuntu0.4, OpenSSL 1.1.1f  31 Mar 2020
debug1: Reading configuration data /home/user/.ssh/config
debug1: /home/user/.ssh/config line 2: Applying options for *
debug3: kex names ok: [curve25519-sha256,curve25519-sha256@libssh.org,diffie-hellman-group16-sha512,diffie-hellman-group18-sha512,diffie-hellman-group-exchange-sha256]
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: include /etc/ssh/ssh_config.d/*.conf matched no files
debug1: /etc/ssh/ssh_config line 21: Applying options for *
debug2: resolving "domain.ltd" port 22
debug2: ssh_connect_direct
debug1: Connecting to domain.ltd [xxx.xxx.xxx.xxx] port 22.
debug1: connect to address xxx.xxx.xxx.xxx port 22: Connection timed out
ssh: connect to host domain.ltd port 22: Connection timed out
user@client_on_WAN ~ [255]>

```

-----------------------------------------------------------------------------


What is my problem? How can I solve this weird problem?
Thanks in advance.

---

### Post by The Cog on 2022-03-05
Possible causes that I can think of:

1: You are calling your WAN address when the client is at home on the server LAN: This type of hairpin connection often doesn't work, depending on the type of router you use.
Try calling from an outside location.

2: Server firewall blocking incoming connections from your WAN client address.
Try temporarily disabling the firewall rule

You really need to eliminate each of these possibilities one by one.
You can use tcpdump on the server to verify whether any incoming connect request arrives. In fact, all you need to do is run
```
sudo tcpdump -nnl -i eth0 tcp port 22
```
and wait for a few minutes and you should see packets being printed as people try to hack your server. You may not even need to go elsewhere to make a call yourself. If the ISP is blocking SSH then you won't see any incoming packets on port 22 except from your own LAN whatever you do.

---

### Post by catav on 2022-03-05
> **The Cog said:**
> Possible causes that I can think of:

1: You are calling your WAN address when the client is at home on the server LAN: This type of hairpin connection often doesn't work, depending on the type of router you use.
Try calling from an outside location.

No, I'm trying it over my phone LTE - as hotspot connection -

> **The Cog said:**
> 2: Server firewall blocking incoming connections from your WAN client address.
Try temporarily disabling the firewall rule

You really need to eliminate each of these possibilities one by one.
You can use tcpdump on the server to verify whether any incoming connect request arrives. In fact, all you need to do is run
```
sudo tcpdump -nnl -i eth0 tcp port 22
```
and wait for a few minutes and you should see packets being printed as people try to hack your server. You may not even need to go elsewhere to make a call yourself. If the ISP is blocking SSH then you won't see any incoming packets on port 22 except from your own LAN whatever you do.

Firewall allows to OpenSSH with limit but it doesn't matter if it is disabled.

```
sudo tcpdump -nnl -i eth0 tcp port 22
```
tcpdump: listening on enp0s25, link-type EN10MB (Ethernet), capture size 262144 bytes
..........waiting........

During the last ten minutes there was no activity, even if I was try to connect.

If I try to connect from LAN a lot of activities occur.

I think my ISP blocks all my SSH traffic.

---

### Post by CharlesA on 2022-03-05
> **catav said:**
> 
I think my ISP blocks all my SSH traffic.

That could be possible. You can use a site like this one to scan your external IP and see if that port is open.

[https://www.grc.com/shieldsup](https://www.grc.com/shieldsup)

You could try changing the port at the router so you leave internal connections alone, and see if that resolves the issue or not.

---

### Post by catav on 2022-03-05
> **CharlesA said:**
> That could be possible. You can use a site like this one to scan your external IP and see if that port is open.

[https://www.grc.com/shieldsup](https://www.grc.com/shieldsup)

You could try changing the port at the router so you leave internal connections alone, and see if that resolves the issue or not.

grc.com says only port 80, 443 and 1024 (I think this is related to my IPTV stream) are open. 22 and all other common ports are stealth.

---

### Post by CharlesA on 2022-03-05
In that case, you can try changing the port the router listens for to forward to port 22 on the LAN side and see if it shows as open or not.

---

### Post by catav on 2022-03-06
> **CharlesA said:**
> In that case, you can try changing the port the router listens for to forward to port 22 on the LAN side and see if it shows as open or not.

Hi,
This is the solution. Thanks for your attention and help.
Now I'm able to use ssh connection over an alternate port.

---

