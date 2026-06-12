---
title: "openvpn installation issue"
date: 2022-04-22
forum: Networking &amp; Wireless
---

### Post by johngab on 2022-04-22
Hi,
new to Ubuntu. Using Ubuntu 20.04.4 LTS.
 Trying to setup VPN for my work. I have been provided with the VPN keys and config files.

 I have copied the files provided by my company to etc/openvpn/ as per their instructions
 and then the instructions are to run:

sudo openvpn --config /etc/openvpn/config/filename.ovpn 

as root


 when I do that I have the following error: 

Error opening configuration file: /etc/openvpn/config/filename.ovpn

 The instructions from my company are  for Linux  though and I am installing on Ubuntu.


 Please help
Many thanks

---

### Post by TheFu on 2022-04-22
a) Ubuntu is linux.
b) what does **ls -al /etc/openvpn/config/filename.ovpn** show?

etc/openvpn/ 
is not the same as
[COLOR="#FF0000"]/[/COLOR]etc/openvpn/[COLOR="#FF0000"]config/[/COLOR]
Details matter.

BTW, don't use root on Ubuntu. Use sudo.

I assume you are trying to run as an openvpn client, not the server?  BTW, there is a GUI in the network controls for openvpn. I've never used it, but it can import a .ovpn file.

---

### Post by johngab on 2022-04-22
Hi, 
thanks so much for answering. I appreciate it. 

**ls -al /etc/openvpn/config/filename.ovpn** 

gives back:

ls: invalid option -- '/'

---

### Post by TheFu on 2022-04-22
You are doing something fundamentally wrong. I have no idea what it is.  Do you have at least 1 space between each of the 3 parts of the command?

---

