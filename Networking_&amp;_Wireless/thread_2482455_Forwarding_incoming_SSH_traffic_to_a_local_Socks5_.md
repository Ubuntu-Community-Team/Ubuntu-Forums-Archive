---
title: "Forwarding incoming SSH traffic to a local Socks5 server (or other services)"
date: 2022-12-31
forum: Networking &amp; Wireless
---

### Post by sam1999 on 2022-12-31
[LEFT][COLOR=#232629][FONT=-apple-system][URL="https://askubuntu.com/questions/1448154/forwarding-incoming-ssh-traffic-to-a-local-socks5-server-or-other-services"]Question link on AskAubuntu
[/URL]
The scenario is That a cloud Ubuntu server is running a Socks5 proxy server on a specified port; on this cloud server :
[/FONT][/COLOR][/LEFT]
[LIST]
[*]Socks5 server serving on port 1515 (only local connections accepted)
[*]SSH is accepting connections from ports 22,33 and 44
[/LIST]
[LEFT][COLOR=#232629][FONT=-apple-system]What we want is to let any client use "Dynamic port forwarding" ability of SSH to connect to the Socks5 server running on the cloud server to be specific Client is going to use this command :[/FONT][/COLOR][/LEFT]ssh -D 1080 -N -f [email]user@cloudserver.host[/email] 
[LEFT][COLOR=#232629][FONT=-apple-system]So any application that uses Port 1080 on the client will have it's traffic routed through the SSH connection and then That remote Socks5 server, so the traffic path will be like :[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]**App running on client machine>Client Socks server on port 1080>SSH Tunnel>Socks5 server accepting local connections**[/FONT][/COLOR][COLOR=#232629][FONT=-apple-system]I hope I have explained clearly, Thnaks
[/FONT][/COLOR][/LEFT]

---

### Post by TheFu on 2023-01-02
Any user with ssh access to a remote system can use that ssh connection as a SOCKS5 server for their browser.  

Let me search for the script I've posted in these forums a few times .... 
Took a bit ... [https://ubuntuforums.org/showthread.php?t=2452922&p=13996823#post13996823](https://ubuntuforums.org/showthread.php?t=2452922&p=13996823#post13996823)

Anyway, hope that helps someone.

---

