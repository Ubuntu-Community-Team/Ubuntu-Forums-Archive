---
title: "Configure and Use OpenSSH"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by EliYui on 2009-05-10
I just recently installed Ubuntu 8.10 onto a computer I own.  I am trying to use OpenSSH as a server on the computer so that I can access it from work to work on it throughout the day.

The computer I have is a Optiplex GX260.  It is connected to the internet through two Linksys routers.  The router between the computer and the router that is connected to the modem, has been configured with a local IP address as to not conflict with the first router and DHCP disabled.  It is being used as a switch.

The router connected to the modem is a Linksys -WRT54G2- wireless router.
The router that is being used as a switch is a Linksys -BEFSR81v3- ethernet router with 8-port switch.
I used the following command to install OpenSSH: "sudo apt-get install openssh-client openssh-server".

What I am having difficultly with is configuring the daemon.  
When I type in: "$ sshd -f /home/eliyui/Desktop/sshd_config2" in a terminal session, 
I receive the following error in : "sshd re-exec requires execution with an absolute path".

Also when I go in to /etc/ssh/ to change the default config file using gedit I am told that I do not have permission.  sshd_config2 is the config file I copied from /etc/ssh to my desktop so that I could make changes to it.  The only change I made was to make the port number 1863.

I want to be able to change the port because my work has security policies that inculdes port blocking and I need to be able to change the port to one that isn't blocked.

If you have any suggestions on how to configure the SSH-server, how to configure port-forwarding on the gateway router, and what SSH-client I should use to access the server on a Windows machine, please post them.

---

### Post by wizard10000 on 2009-05-10
Can't help you much on the ssh thing (well, I could but choose not to - maybe someone else will) but do have one other thing to say.

If your work firewall is blocking ports it's probably a terrible idea to just try and ssh on another port because even if it is successful (which it may not be - if it is successful your firewall admin needs to be fired) the office information assurance guys *will* see the traffic on port 1863, trace it back to your work PC and most likely get you reprimanded if not unemployed.

I almost became unemployed once for tunneling into my home server from the office - there's no such thing as anonymity on a network, especially not on a network you don't manage.

Don't try to breach your employer's network security - if the company has hired decent people you'll be the one paying the price.

---

### Post by Bölvaður on 2009-05-10
check out the first few lines in /etc/ssh/sshd_config

---

### Post by EliYui on 2009-05-10
The first 10 lines are as follows:

# Package generated configuration file
# See the sshd(8) manpage for details

# What ports, IPs and protocols we listen for
Port 22
# Use these options to restrict which interfaces/protocols sshd will bind to
#ListenAddress ::
#ListenAddress 0.0.0.0
Protocol 2
# HostKeys for protocol version 2

This is from the sshd_config file which I can't make any changes to.

---

### Post by Bölvaður on 2009-05-10
open the terminal or alt+f2 and type

```
gksu gedit /etc/ssh/sshd_config
```

change port 22 to something fun like 31337 and save :)

---

### Post by EliYui on 2009-05-10
Great, that allowed me to make changes to sshd_config.

---

### Post by alphacrucis2 on 2009-05-10
> **EliYui said:**
> Great, that allowed me to make changes to sshd_config.

That's because you have to have administrative rights to modify that file. Use gksu to run a gnome program with admin rights. For command line use sudo.

---

### Post by EliYui on 2009-05-10
How do I set my computer to use a static IP address while no one is logged into it, so all I have to do is start the computer up?

Currently I have to change from "Auto eth0" to my own connection entry after I log into an user account otherwise the computer uses a DHCP address that is given to it by the gateway router.  I would rather not use MAC address filtering to set the computers IP address.

---

