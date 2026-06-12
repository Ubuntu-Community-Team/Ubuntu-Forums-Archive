---
title: "Unable to ssh into my laptop"
date: 2014-06-24
forum: Networking &amp; Wireless
---

### Post by Patransky on 2014-06-24
Hi folks, 

I've Ubuntu 12.04 on my laptop and I need to connect remotely to it from another computer. 
However, whenever I try to connect with "**ssh myuser@myip" **nothing happens. 

I can ssh from those computers on my other machines here and there, but not on my laptop. 
I've tried this from several different computers on different networks. Same result everywhere. 

I think this has to do with the ssh configuration in Ubuntu on my laptop. I've ssh installed there (and I can 
ssh to any location from my laptop). I've tried [B]sudo lsof -i | grep ssh

[/B]This is the output: 
*sshd        703       root    3u  IPv6   9525      0t0  TCP *:ssh (LISTEN)*
[I]sshd        703       root    4u  IPv4   9527      0t0  TCP *:ssh (LISTEN)
[/I]
Any syuggestion about what I might be doing wrong?
Thanks!

---

### Post by Lars Noodén on 2014-06-24
Going from your laptop is different then going to your laptop.  The former involves a client and the latter the server.  Your output from lsof shows that you do have the server listening on the port for ssh.  Maybe the next thing to check would be the obvious, make sure the firewall is letting incoming connections for SSH.

```

ufw allow ssh

```

---

### Post by Patransky on 2014-06-24
Hi Lars, 

thanks for your reply. I just tried your suggestion but the result is unchanged: when I try to connect to my laptop nothing happens...any other suggestion?

---

### Post by steeldriver on 2014-06-24
[LIST]
[*]where are you trying to connect from? a computer on the same LAN, or some other network? 
[*]what exactly does "nothing happens" mean? does the terminal hang, or do you immediately get a new prompt? 
[*]have you tried invoking ssh with verbose reporting e.g. 
[/LIST]

```

ssh **-vv** myuser@myip

```

[LIST]
[*]you can also try connecting **to **the laptop **from **the laptop with 
[/LIST]
```

ssh myuser@localhost

```

just to verify that the basic configuration and default port are correct

---

### Post by Patransky on 2014-06-24
Ok. When I try (on my laptop)** ssh my-user@localhost **I can connect without problems.

When I go to my desktop computer (on a different network) and I do [B]ssh -vv myuser@myip
[/B]this is what I get: 
```
OpenSSH_6.6.1, OpenSSL 1.0.1f 6 Jan 2014
debug1: Reading configuration data /etc/ssh/ssh_config
debug1: /etc/ssh/ssh_config line 19: Applying options for *
debug2: ssh_connect: needpriv 0
debug1: Connecting my-ip-is-here [my-ip-is-here] port 22.

```

and everything stays like this as if waiting for an answer. I've left this ongoing for few minutes and then I get

```

debug1: connect to address *my-ip-is-here* port 22: Connection timed out
ssh: connect to host *my-ip-is-here* port 22: Connection timed out

```


To be sure that the problem is not with my desktop machine I've tried from a third different computer on a different network and I get the exact same result. So I think it's my laptop not answering the call...but I've no idea what I'm doing wrong.

---

### Post by steeldriver on 2014-06-24
Does your laptop have a **public **IP? have you set up **port forwarding** on your LAN router?

---

### Post by Lars Noodén on 2014-06-24
You mention a third machine on a different network.  Is the second machine on the same network / LAN ?  Can you ping the laptop from that second machine?

```

ping -c 5 -w 1 myip

```

How are you getting the ip that you are trying to use for connecting to  your laptop?

---

### Post by CTate on 2014-06-24
Is the ssh daemon running on the laptop? Try "ps-ax | grep -sshd"

If it's not running try starting it: /usr/sbin/sshd or prob sudo /usr/sbin/sshd

---

