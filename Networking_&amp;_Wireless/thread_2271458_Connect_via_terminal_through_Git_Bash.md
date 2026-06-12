---
title: "Connect via terminal through Git Bash"
date: 2015-03-30
forum: Networking &amp; Wireless
---

### Post by soprano2 on 2015-03-30
hello,


I have the pc with Lubuntu 14.04 and I want acess them via git bash through windows 7 (another pc). How a connect the another pc with my Lubuntu 14.04 via terminal in git bash?
I need configure some program or parameters in Lubuntu?


thanks,
soprano

---

### Post by TheFu on 2015-03-30
git uses ssh, so just use any ssh client - on Windows Putty is popular. Of course, the remote system will need to have openssh-server installed and it would be smart to install fail2ban and only allow ssh-keys - never passwords - for authentication.

---

