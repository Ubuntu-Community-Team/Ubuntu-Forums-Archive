---
title: "Host Monitoring"
date: 2006-08-07
forum: Networking &amp; Wireless
---

### Post by sesliu on 2006-08-07
Hi people,

Is there any program that do host monitoring? it like languard scanner for Windows!

thanks

---

### Post by sesliu on 2006-08-08
anybody?

---

### Post by Almighty on 2006-08-08
If you are referring to an intrusion detection systems then SNORT is what you are looking for, If you are looking for a security scanner then Nessus is the key. If you are looking for packet analyzers, there is a whole lot of them for you to choose from. 

Linux is the best networking OS in my opinion. Not as easy to use as windows, not as pretty as windows but you have many many many more powerful options in my opinion.

---

### Post by sesliu on 2006-08-08
> **Almighty said:**
> If you are referring to an intrusion detection systems then SNORT is what you are looking for, If you are looking for a security scanner then Nessus is the key. If you are looking for packet analyzers, there is a whole lot of them for you to choose from. 

Linux is the best networking OS in my opinion. Not as easy to use as windows, not as pretty as windows but you have many many many more powerful options in my opinion.

I know it, but I want a program that show me the machines in network like Operation system, CPU, memory and other informations. I need to make a network auditory and it's very easy if exist a software that help me this work.

---

### Post by halfvolle melk on 2006-08-08
Nmap is one of the many tools for network auditing.
> Nmap is a utility for network exploration or security auditing. It
 supports ping scanning (determine which hosts are up), many port
 scanning techniques, version detection (determine service protocols
 and application versions listening behind ports), and TCP/IP
 fingerprinting (remote host OS or device identification). Nmap also
 offers flexible target and port specification, decoy/stealth scanning,
 sunRPC scanning, and more. Most Unix and Windows platforms are
 supported in both GUI and commandline modes. Several popular handheld
 devices are also supported, including the Sharp Zaurus and the iPAQ.
Bugs: mailto:ubuntu-users@lists.ubuntu.com

---

### Post by sesliu on 2006-08-08
> **halfvolle melk said:**
> Nmap is one of the many tools for network auditing.

nice, but is there a program that show me memory information?

---

### Post by yeehawjared on 2006-08-08
what you're looking for is nagios
[http://www.nagios.org/](http://www.nagios.org/)
[http://www.nagios.org/about/screenshots.php](http://www.nagios.org/about/screenshots.php)

you can also monitor hosts with openNMS and BIXdata
[http://www.howtoforge.net/opennms_network_management](http://www.howtoforge.net/opennms_network_management)
[http://www.howtoforge.net/server_monitoring_bixdata](http://www.howtoforge.net/server_monitoring_bixdata)

does that help?

---

### Post by eoghan on 2006-08-08
[http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html](http://members.dslextreme.com/users/billw/gkrellm/gkrellm.html)

Gkrellm is another useful tool that I've found quite invaluable. Install a daemon on each server, then run a client instance to monitor it. Only downside is that a single client can't monitor multiple servers, you have to run it once for each one.

---

### Post by halfvolle melk on 2006-08-08
> **sesliu said:**
> nice, but is there a program that show me memory information?
Sorry, I must have missread your question. If you want to check out stuff on the computer you're working on, the terminal command "top" will do most of what you want. If you want it visual on your Desktop, please refer to the post above about Gkrellm.

---

