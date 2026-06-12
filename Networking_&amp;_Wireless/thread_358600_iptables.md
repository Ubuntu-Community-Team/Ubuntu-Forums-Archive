---
title: "iptables"
date: 2007-02-11
forum: Networking &amp; Wireless
---

### Post by DigitalXeron on 2007-02-11
Hello,

Is there a way in ubuntu like gentoo and fedora has where current iptables rules are saved on shutdown and restored on startup without having to edit both the rules AND the startup files? I know it is possible in other distros, All I see in this forum is how to use shell scripts with the rules in them that do [b[not[/b] automatically self-update.

The tutorial at [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall) doesn't provide an automatic update of the shell script files on shutdown. as well as it trashes any support for Webmin's editing of iptables in the process as it doesn't load appropreate rule sets.

The knetfilter program only allows for port-based filtering, it complains with an error that you must specify a port, i.e. you cannot set a rule to allow for accepting all ports on 127.0.0.1 and allow the packets if the connection is ESTABLISHED without specifying a port (as Webmin allows for)

Furthermore, it seems as if iptables is not started, is locked to all ports open, or is not properly installed by default under Ubuntu, is there a way to activate iptables without having to edit 2-3 files all the time? or is this support totally broken?

The version I'm using is Edgy

---

### Post by pxwpxw on 2007-02-11
I always settle for firestarter, which covers my security fairly well. Have you looked at that?

or iptables-save  and iptables-restore

---

