---
title: "Why can't I ssh into my Ubuntu server's external ip address?"
date: 2021-01-01
forum: Networking &amp; Wireless
---

### Post by chunkydrew2 on 2021-01-01
When I'm on my home network, I frequently SSH into my server, using *** ssh chunkydrew@192.168.0.150***; I am then prompted for my password on the server, supply it, and am granted access. No problem there. 

My issue is, I want to access the server (Ubuntu 20.04) from outside the network. I have found my external IP address. When I type in PowerShell ssh [email]chunkydrew@xx.xxx.xx.xxx[/email], I get the error message:
[INDENT]
**ssh_dispatch_run_fatal: Connection to xx.xxx.xx.xxx port 22: Invalid key length**[/INDENT]

Why won't it use the same ssh keys used inside the network? When I try to use putty instead, it asks for my password, then returns **Access Denied**. What am I doing wrong, or missing? Any assistance would be greatly appreciated!
[INDENT=2][/INDENT]

---

### Post by TheFu on 2021-01-01
[https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections](https://blog.jdpfu.com/2015/08/17/troubleshooting-ssh-connections) has some ideas and steps to take.

---

