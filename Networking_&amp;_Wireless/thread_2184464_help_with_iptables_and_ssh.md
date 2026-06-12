---
title: "help with iptables and ssh"
date: 2013-10-29
forum: Networking &amp; Wireless
---

### Post by ulao2 on 2013-10-29
I basically want to connect to ssh over 8022

iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 8022 -j REDIRECT --t o-port 22                                                                      
iptables  -A INPUT -i eth0 -p tcp -m tcp --dport 8022  -j ACCEPT  

If there is a reason it can not be 22 I guess plane telnet will work.

using what I have above never makes a connection.

---

### Post by ian-weisser on 2013-10-29
Another method, instead of using iptables to change the port to 22,
is to have the ssh server listen on 8022 instead of 22.

1) Edit /etc/ssh/sshd_config  (as sudo) 
2) Look for the line: port 22 .  Edit the line to the port desired. Save the changes.
3) Restart the ssh server:$ sudo service ssh restart

---

### Post by ulao2 on 2013-10-29
Any way to have it listen to both? use a comma?

---

### Post by Lars Noodén on 2013-10-29
> **ulao2 said:**
> iptables -t nat -A PREROUTING -i eth0 -p tcp -m tcp --dport 8022 -j REDIRECT --t o-port 22                                                                      
iptables  -A INPUT -i eth0 -p tcp -m tcp --dport 8022  -j ACCEPT  


That will work without UFW turned on.  Though you may have to change the -A to an -I in the second rule.

If you have UFW on, it will block port 22 by default and you will have to enable it explicitly so that it can receive the redirection. 

Or you can add one temporarily to the above.

```
 iptables -I INPUT -i eth0 -p tcp -m tcp --dport 22 -j ACCEPT 
```

 I'm not sure how you can get the PREROUTING rule to stick around between reboots, while adhering to UFW.

---

### Post by Lars Noodén on 2013-10-29
> **ulao2 said:**
> Any way to have it listen to both? use a comma?

You can have it listen to more than one port at a time by adding multiple [Port](http://manpages.ubuntu.com/manpages/raring/en/man5/sshd_config.5.html) options in /etc/ssh/sshd_config, one per line.  Be sure to read through the manual page for sshd_config and make a back up copy of the configuration file before editing. You can also use the [ListenAddress](http://manpages.ubuntu.com/manpages/raring/en/man5/sshd_config.5.html) option to listen to different ports on different ip addresses or host names.

---

### Post by ulao2 on 2013-10-29
this will do, thx.

---

