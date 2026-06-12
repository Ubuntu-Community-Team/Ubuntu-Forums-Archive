---
title: "Wrestling with SSH"
date: 2008-08-24
forum: Networking &amp; Wireless
---

### Post by jeenuv on 2008-08-24
Hi,

My ultimate goal is to setup an SSH server running on my Ubuntu laptop, so that I can ssh from my work PC (Windows XP) and manage some downloads. This is my current setup:

I followed this thread: [http://ubuntuforums.org/showthread.php?t=256102](http://ubuntuforums.org/showthread.php?t=256102), where it explains how to start your SSH serever first of all. It does start listening to 22, but I can't make it listen to any other port (say 4000), after editing the /etc/ssh/ssh_config file (Port directive). I verified this by doing:

ssh localhost -p 4000

and it says "ssh: connect to host localhost port 4000: Connection refused"

What am I doing wrong?

PS: After successfully running the SSH server on a custom port and later enabling port forwarding on my router (which has a static IP), I assume ssh on the router will be directed on to my PC

Thanks
Jeenu

---

### Post by squaregoldfish on 2008-08-24
Try setting the port in sshd_config instead of ssh_config - that should do the trick.

Your assumption about the port forwarding is correct - that's exactly how my system is set up. Of course, I assume your router is configured to always assign the same IP address to the laptop...

Hope this helps,
Steve.

---

### Post by pauts on 2008-08-25
i have the same problem in xubuntu 8.04 (32 bits).

i set the Port and the AllowUsers in /etc/ssh/sshd_config, but i have the connection refused error. if i do the ssh local, from the same computer running ssh server, it's ok, but when i try to connect from other machines the ports seems to be closed ¿? 

i haven't set any firewall, does xubuntu close port by default?

any help?

---

