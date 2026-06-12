---
title: "Ssh problems"
date: 2009-05-10
forum: New to Ubuntu
---

### Post by milandobrota on 2009-05-10
After I run ssh username@address I get no feedback... It just hangs..
I didn't change the configuration file.
Anyone knows what the problem might be?

---

### Post by spiderbatdad on 2009-05-10
Is the firewall on the sshserver blocking the port? Does the user account exist on the server? On a LAN or WAN?
Lots of documentation on Ubuntu wiki:
[https://help.ubuntu.com/community/SSHHowto](https://help.ubuntu.com/community/SSHHowto)
[https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html](https://help.ubuntu.com/8.04/serverguide/C/openssh-server.html)
[https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)

---

### Post by milandobrota on 2009-05-10
It is not LAN, I'm trying to connect to webhosting server. Isn't it supposed to give me some sort of a feedback if the user credentials are wrong? And do I have to do any router configuration? I just wanna make sure everything is OK on my side before I contact the hosting crew.

---

### Post by bodhi.zazen on 2009-05-10
To debug ssh use

ssh -vv user@server

That is - v v (two v's) and not a -w

---

