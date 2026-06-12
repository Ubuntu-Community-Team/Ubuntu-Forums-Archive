---
title: "problems with ssh in xubuntu"
date: 2008-08-26
forum: Networking &amp; Wireless
---

### Post by pauts on 2008-08-26
i have edited /etc/ssh/sshd_config file and changed Port and AllowUsers.

I can open a ssh session locally, but when i try it from another computer in the lan, it says "Connection refused".


i think it's something with the ports, do i need to open it or something? and if is that, how can i do it?

thanks

---

### Post by jigsaws on 2008-08-26
Check in your config file:
Port
ListenAddress

Did you restarted sshd daemon after editing config?

Maybe firewall?

---

### Post by pauts on 2008-08-26
i have restarted the daemon, and even the computer.

the config file seems to be right. i've made the same changes with ubuntu and it works fine, but just don't work with xubuntu.

what's the diference?

---

### Post by jigsaws on 2008-08-26
Ok, give me output from:

netstat -nlt
iptables -L -v

---

