---
title: "port forwarding with ssh"
date: 2019-05-27
forum: Networking &amp; Wireless
---

### Post by marchello_lippi2 on 2019-05-27
Hi all, 
I use this command for socks proxy using ssh: 
```
[FONT=monospace][COLOR=#FF5454]**ssh**[/COLOR][COLOR=#000000] user@ip -D9522 -C[/COLOR][/FONT]
```
After it was executed, I can open browser with socks proxy settings 127.0.0.1: 9522 and use internet as I'm on remote ip. This part works fine. I can open any site like "what is my ip" and it will show that I'm on remote ip address. 

The ip address used in command above is my virtual private server where I can run my own services.

Now what does not work anymore. I have transmission running there and I could access it in browser before like 127.0.0.1:9091, but I can't access it anymore. I have also syncthing running there and I could access it in browser before like 127.0.0.1:8384. 

It does not work for me now. What's wrong? I am able to see syncthing running and also I can see that files are synced. But I can't access it in browser. 

Is port forwarding broken in ssh? Please advise.

---

### Post by TheFu on 2019-05-27
You are asking for the wrong host.

127.0.0.1 is the client you are sitting on, not the remote computer.

You need to use the local hostname of the other box, preferably the non-routable LAN IP.  Just add that to your local client /etc/hosts file.

Or you can setup another ssh port forward from the client to the exact port on the remote system, perhaps.  I've never done that with an active SOCKS proxy.  I always just use the LAN IPs / LAN-hostnames.

---

