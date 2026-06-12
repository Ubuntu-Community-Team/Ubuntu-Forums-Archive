---
title: "Installed firewall but unsure if it's running properly"
date: 2018-04-09
forum: Networking &amp; Wireless
---

### Post by accounts0 on 2018-04-09
I installed arno-iptables-firewall & answered the questions during setup, but its status says it's dead. Is there more I need to do?

```
[FONT=monospace][COLOR=#000000]$ sudo service arno-iptables-firewall status[/COLOR]
&#9679; arno-iptables-firewall.service - Arno's Iptables Firewall                                                                                            
   Loaded: loaded (/lib/systemd/system/arno-iptables-firewall.service; disabled; vendor preset: enabled)                                               
   Active: inactive (dead)
[/FONT]
```

---

### Post by TheFu on 2018-04-09
In Linux, the firewall is part of the kernel.  Any extra tools you install to interface with it are just that, interface tools.

I have never heard of the package you mentioned. 
There is a README here: [https://github.com/arno-iptables-firewall/aif](https://github.com/arno-iptables-firewall/aif) which explains how to get help. Seems to be a firewall script created for fairly advanced users.

Normally, people on ubuntu use ufw, gufw on desktops and iptables on servers to manage the built-in firewall. I've seen mention of firewalld from time to time, but have only seen that on CentOS/RHEL systems. It might be available on newer Ubuntu releases than I run. 16.04 is my newest release.

---

### Post by accounts0 on 2018-04-25
> **TheFu said:**
> Normally, people on ubuntu use ufw, gufw on desktops and iptables on servers to manage the built-in firewall.

Switched to gufw, much better- thanks.

---

