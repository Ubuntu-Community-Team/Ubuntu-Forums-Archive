---
title: "Networking Problems"
date: 2009-04-03
forum: New to Ubuntu
---

### Post by Taoh15 on 2009-04-03
Hi

I have a Netgear router acting as a DHCP server, an XP machine and an old machine interpid ibix desktop which I installed a couple of weeks ago. 
The Ubuntu machine is used to download files at night. I then transfer them to my XP machine in the morning. 
However I can't ping either way by name although I can by IP Address.

I also mis-named the Ubuntu machine and need to change it's name.

Everything pointed to using the network-admin tool, however here's the problem.
I tried using 

terminal with 
scottn@ubuntu:~$ gksudo network-admin 
I was asked for my password then it returned to the prompt and nothing else

terminal with
scottn@ubuntu:~$ sudo network-admin
[sudo] password for scottn:
sudo: network-admin : command not found

 
GUI
System|Preferences|Network Configuration
But I get the following tabs
Wired Wireless Mobile Broadband VPN DSL 
With eth0 in wired
Instead of the expected Connections General DNS Hosts


I managed to resolve the original problem by hand crafting /etc/network/interfaces and rebooting but I have now lost eth0 in Wired.

Any idea what's wrong.

Taoh

---

### Post by steeleyuk on 2009-04-03
The network-admin tool is deprecated in favour of using the network-manager configuration.

To change your hostname you'll need to edit the file /etc/hostname.

As to pinging by hostname, I think you'll need to edit your hosts file (/etc/hosts) to reflect the names of the machines on the network - I could be wrong about this one, will have to check.

Edit: just read that you might [need to do this]("http://forums.devshed.com/showpost.php?p=2052462&postcount=5").

---

### Post by The Cog on 2009-04-03
If you change the host name in /etc/hostname, you should also edit /etc/hosts and change the name to match in there.

While you're at it, you can add the address and name of the windows machine to /etc/hosts. Then edit \windows\system32\drivers\etc\hosts and add the address/name of the Ubuntu system there.

---

