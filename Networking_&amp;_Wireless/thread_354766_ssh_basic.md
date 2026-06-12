---
title: "ssh basic"
date: 2007-02-06
forum: Networking &amp; Wireless
---

### Post by eldersoares on 2007-02-06
hello!
i'm trying to connect 2 linux machines thru ssh: 1 w/ ubuntu and the other w/ kurumin (knoppix based). i did, following  a tutorial:

ifconfig eth0 192.168.0.1 up

and in the other machine
ifconfig eth0 192.168.0.2 up

both as root. then, in ubuntu, i accessed places - connect w/ server. i put the data (ssh, ip of the other machine, user) and it worked. but just once! now, the ssh folder that appears doesnt open. testing w/ ping are successfully, sometimes. but w/ ssh user@ip the error message is: connection refused.

¿what is wrong?
thanks

---

### Post by spd106 on 2007-02-06
Hi, I think the problem is that when you boot kurumin it generates a new "usercode". Now when you attempt to contact the ssh server it sees this new code and checks it against the code it has stored for that ip addesss, as they don't match your connection is rejected.

I had this issue a while back when I tried to connect from multiple partitions on the same PC. I'm not sure what the best solution is. I think you can turn off this default behavior and just use the isername/password pair. Check out the man pages for the ssh.conf.

You could also try creating a public/private key pair (RSA) and use that for authentication. This enhances security and means that you don't need to enter a password every time. There's a [howto]("https://help.ubuntu.com/community/AdvancedOpenSSH") in the wiki

---

