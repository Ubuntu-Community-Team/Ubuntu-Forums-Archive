---
title: "How do I tell if I have a static ip address?"
date: 2009-10-09
forum: New to Ubuntu
---

### Post by japhyr on 2009-10-09
Hello,

I work in a mostly windows environment, with a mostly cooperative sysadmin.  I am trying to set up an ubuntu station for myself, and if I am successful others will want one as well.  The biggest hurdle is connecting to the windows network.  The sysadmin will tell me any settings I might need to know, but won't walk me through the process.

I am trying to follow the steps in [this guide]("http://ubuntuforums.org/showthread.php?t=202605"), and one of the prerequisites is "Your linux box should have a static ip-address".  Everything I can find talks about setting up a static ip address when using a computer as a server.  I only want to be a client on the windows network.  How can I find out if the ip address I see with "ifconfig | less" is a static one?

---

### Post by deconectat on 2009-10-09
On windows: start -> run -> cmd. Type *ipconfig /all* and you'll see if you have a static ip address (and what that ip is).

---

### Post by japhyr on 2009-10-09
I have a windows computer and an ubuntu computer set up side by side, both connected to the same network.  Both have similar ip addresses, but slightly different from each other.

Running "ipconfig /all" on the windows box lists "DHCP enabled...yes".  Does that mean I do not have a static ip address on either machine?

---

### Post by wojox on 2009-10-09
Follow this guide to set it in Ubuntu: [http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html](http://www.ubuntugeek.com/change-ubuntu-system-from-dhcp-to-a-static-ip-address.html)

---

### Post by deconectat on 2009-10-09
> **japhyr said:**
> 
Running "ipconfig /all" on the windows box lists "DHCP enabled...yes".  Does that mean I do not have a static ip address on either machine?

Exactly. It also means you should have network acces on the ubuntu computer without having to configure anything.

---

### Post by hal10000 on 2009-10-09
If your windows network is set up via dhcp then your ubuntu system will usually work with dhcp, unless your adminstrator has configurated the dhcp-server with some strange restrictions.
So you will get connected to the internet, but if you want access to your windows domain, file-servers. network-printers etc. you have to set up samba client in ubuntu (windows-passwords, domain-names etc.)
If you search in the ubuntu forums for samba you will get help.

---

