---
title: "Enable SSH"
date: 2009-04-18
forum: New to Ubuntu
---

### Post by Dai Bando on 2009-04-18
How do you enable SSH so that my son in Holland can connect to my computer?:D

---

### Post by Bachstelze on 2009-04-18
The OpenSSH server is not installed by default in Ubuntu. To install it, install the package [font="monospace"]openssh-server[/font].

---

### Post by iponeverything on 2009-04-18
Go to:

System -> Administration -> Synaptic Package Manager

openssh-server

---

### Post by nandemonai on 2009-04-18
If you are behind a NAT router you will need to forward a port (default ssh port 22) to your machine.

---

### Post by Carl Hamlin on 2009-04-18
> **iponeverything said:**
> Go to:

System -> Administration -> Synaptic Package Manager

openssh-server

And then prepare to have your logs *filled to the brim* with reports of folks pounding your system with common ssh exploits unless you change the port sshd listens on to something higher up.

To keep this from happening, open a terminal and follow along:

you@yourcomputer~$: cd /etc/ssh
you@yourcomputer/etc/ssh$: sudo nano sshd_config
[sudo] password for you: yourpassword

When you're looking at sshd_config, change the 'Port' value to something in the high range, and hit <Ctrl> + X to write the changes, then reboot.

When your son connects, he'll have to enter the port number - ssh will try the default port by default, surprisingly enough. If he's connecting through nautilus, then there's a dialog which will ask for it, but if he's connecting through a terminal, the command goes like this:

yourson@yourson'scomputer~$: ssh your.computer.whatever -p portnumber

SSH is a fantastic tool, and I think it's really neat. So do a lot of other folks, though, so you gotta be careful with it in order to keep your computer from getting *pounded* with ssh exploits. Good luck!

---

### Post by Carl Hamlin on 2009-04-18
> **nandemonai said:**
> If you are behind a NAT router you will need to forward a port (default ssh port 22) to your machine.

Indeed. The process for doing so will vary within a scope depending on the router, but is usually pretty intuitive, and should be presented in the router manual if you can't figure it out by sight. If you change the listener port, you'll want to make sure the router is forwarding the port you chose, rather than the default.

---

### Post by nandemonai on 2009-04-18
> **Carl Hamlin said:**
> And then prepare to have your logs *filled to the brim* with reports of folks pounding your system with common ssh exploits unless you change the port sshd listens on to something higher up.

To keep this from happening, open a terminal and follow along:

you@yourcomputer~$: cd /etc/ssh
you@yourcomputer/etc/ssh$: sudo nano sshd_config
[sudo] password for you: yourpassword

When you're looking at sshd_config, change the 'Port' value to something in the high range, and hit <Ctrl> + X to write the changes, then reboot.

When your son connects, he'll have to enter the port number - ssh will try the default port by default, surprisingly enough. If he's connecting through nautilus, then there's a dialog which will ask for it, but if he's connecting through a terminal, the command goes like this:

yourson@yourson'scomputer~$: ssh your.computer.whatever -p portnumber

SSH is a fantastic tool, and I think it's really neat. So do a lot of other folks, though, so you gotta be careful with it in order to keep your computer from getting *pounded* with ssh exploits. Good luck!

[Deny Hosts]("http://denyhosts.sourceforge.net/") is another option, especially since the script kiddies are starting to port scan as well now I've noticed. ;)

Though a good firewall will prevent that anyway.

To the OP, I'd suggest reading up a little on SSH, firewalls and port forwarding if not for piece of mind.

---

### Post by Dai Bando on 2009-04-18
Thank you all gentlemen. I will give it a go.:D

---

### Post by SpinningAround on 2009-04-18
side question

Can you edit /etc/hosts.deny and /etc/hosts.allow so only Dai Bando son is allowed to connect?

---

### Post by MrWES on 2009-04-18
> **nandemonai said:**
> [Deny Hosts]("http://denyhosts.sourceforge.net/") is another option, especially since the script kiddies are starting to port scan as well now I've noticed. ;)

Though a good firewall will prevent that anyway.

To the OP, I'd suggest reading up a little on SSH, firewalls and port forwarding if not for piece of mind.

+1 for DenyHosts:

[http://ubuntuforums.org/showthread.php?t=450853]("http://ubuntuforums.org/showthread.php?t=450853")

I would also set /etc/ssh/sshd_config to read

```
PermitRootLogin no

```

And go with key only logins:

[https://help.ubuntu.com/community/AdvancedOpenSSH]("https://help.ubuntu.com/community/AdvancedOpenSSH")

Wouldn't hurt to throw in a rate limit on your firewall iptables to prevent brute force attacks:
[http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/]("http://kevin.vanzonneveld.net/techblog/article/block_brute_force_attacks_with_iptables/")

Bill

---

