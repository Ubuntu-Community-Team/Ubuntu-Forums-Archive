---
title: "Setting up port fowarding in IPTABLES"
date: 2014-05-06
forum: Networking &amp; Wireless
---

### Post by david207 on 2014-05-06
Hi all, hoping someone could help me out with a problem i am having.  So here is the deal, i have usb broadband internet (eth3).   I have successfully set up masquerade so that all others on my internal network also have internet access.  (Using a wired adapter, eth1).  It has been working great, but yesterday i tried to set up a dynamic dns account so i could ssh into my machine externally. It is not working and i am wondering if i have to setup port forwarding since i am masquerading?  I am not extremely comfortable with iptables rules so if this is the case, any examples would be welcome..  Thanks in advance!

---

### Post by SeijiSensei on 2014-05-06
Are you trying to use SSH to connect to the machine doing the masquerading, or another one behind it? 

If you are trying to connect to gateway itself, and it is connected directly to the Internet, you shouldn't need to do anything but open port 22 and run openssh-server.  I'd make sure to use [keys]("https://help.ubuntu.com/14.04/serverguide/openssh-server.html#openssh-keys") rather than logins for security.

I can only guess about what firewall rules you already have.  But if you have an "ESTABLISHED,RELATED" rule, add this immediately afterward:
```
/sbin/iptables -A INPUT -p tcp -d public.ip.of.server --dport 22 -j ACCEPT
```

That only permits connections to the machine's public interface.  To permit SSH on all interfaces, remove the "-d public.ip.of.server" entry.

If this machine is itself behind a router, you'll need to set up port forwarding on that device.

---

### Post by david207 on 2014-05-06
THanks for the info, yes it is the machine doing the masquerading, not behind a router. Im unable to ssh or ping from outside my external network, firewall is off for testing, and still no luck.  Any ideas?

---

### Post by david207 on 2014-05-06
Looks like it is an issue with verizon LTE mobile broadband....

---

