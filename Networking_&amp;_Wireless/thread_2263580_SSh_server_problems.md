---
title: "SSh server problems"
date: 2015-02-01
forum: Networking &amp; Wireless
---

### Post by linuxn00b1 on 2015-02-01
I'm trying to connect 2 xubuntu 14.04 machines. laptop (client) is an old install with previous ssh sessions on a rasp pi and this computer with ubuntu 12.04. The Desktop has a fresh xubuntu install and fresh ssh server install. After the install the First time I installed SSh server on the desktop (server) I could log in using local host with password and port 22 was open. I tried to log in from the laptop and got an error message about a possible man in the middle attack.

 Please contact your system administrator.
Add correct host key in /home/me/.ssh/known_hosts to get rid of this message.
Offending ECDSA key in /home/me/.ssh/known_hosts:6
  remove with: ssh-keygen -f "/home/me/.ssh/known_hosts" -R 1xx.xxx.xxx
ECDSA host key for xxx.xxx.xxx has changed and you have requested strict checking.
Host key verification failed.
me@Sate:~$ ssh-keygen -f "home/me/.ssh/known_hosts" -R 1xx.xx.x.xx
ssh-keygen: home/mike/.ssh/known_hosts: No such file or directory
me@Sate:~$ ssh-keygen -f home/me/.ssh/known_hosts -R 1xx.xxx.xxx
ssh-keygen: home/me/.ssh/known_hosts: No such file or directory

I also tried 

ed -i '6' ~/.ssh/known_hosts (read multiple threads, this didn't work)

I then uninstalled ssh server from the desktop and reinstalled, now using localhost login on the desktop won't work and gives the same message. 

I understand (kind of) the private and public keys but I NEVER had to set that up before. I usually go to the terminal and type ssh [email]user@ip.addres[/email]s with user name and password.

please advise where to go from here. 

thanks

---

### Post by SeijiSensei on 2015-02-02
You're missing the initial "/" in /home/me/.ssh/known_hosts.  Notice the subtle difference between what you entered and what the SSH client told you to type.

```

remove with: ssh-keygen -f "/home/me/.ssh/known_hosts" -R 1xx.xxx.xxx
ECDSA host key for xxx.xxx.xxx has changed and you have requested strict checking.
Host key verification failed.
me@Sate:~$ ssh-keygen -f "home/me/.ssh/known_hosts" -R 1xx.xx.x.xx
ssh-keygen: home/mike/.ssh/known_hosts: No such file or directory

```

---

### Post by linuxn00b1 on 2015-02-02
proper command didn't work.
I did a fresh xubuntu install on laptop (had some other startup system error for a while)  now I am able to ssh into desktop. thanks for the help

---

