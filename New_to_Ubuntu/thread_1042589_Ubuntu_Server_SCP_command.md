---
title: "Ubuntu Server SCP command"
date: 2009-01-17
forum: New to Ubuntu
---

### Post by honkthrast on 2009-01-17
I ran a search for 'scp timeout' and didn't come up with anything, I apologize if this is a repeat issue.

clientName is an ubuntu 8.10 box with ssh installed.
serverName is an ubuntu 8.10 server box with ssh installed.

Those aren't the actual names of the servers, obviously, but I figure this is enough information for you to help me solve the problem.

```
user@clientName:~/.ssh$ ssh xxx.xxx.xxx.xxx
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
8d:1c:71:ed:f3:ba:83:81:24:d3:37:58:da:c5:63:2e.
Please contact your system administrator.
Add correct host key in /home/user/.ssh/known_hosts to get rid of this message.
Offending key in /home/user/.ssh/known_hosts:3
RSA host key for 192.168.1.2 has changed and you have requested strict checking.
Host key verification failed.

user@clientName:~/.ssh$ scp ~/.ssh/id_dsa.pub user@serverName:.ssh/authorized_keys
ssh: connect to host serverName port 22: Connection timed out
lost connection
```

I know that there isn't a hacker listening, because I just finished reinstalling ubuntu server.  Unfortunately, I can't figure out how to send the corrected keys over to the server like this.

I'm sure it's just a simple step I'm missing, but I'm trying to teach myself through setting up servers so that it becomes as effortless as possible.

```

user@serverName:netstat -ant
Active Internet connections (servers and established)
Proto Recv-Q Send-Q Local Address      Foreign Address    State
tcp   0      0      127.0.0.1:3306     0.0.0.0:*          LISTEN
tcp   0      0      0.0.0.0:139        0.0.0.0:*          LISTEN
tcp   0      0      0.0.0.0:80         0.0.0.0:*          LISTEN
tcp   0      0      0.0.0.0:22         0.0.0.0:*          LISTEN
tcp   0      0      0.0.0.0:445        0.0.0.0:*          LISTEN
tcp   0      0      xxx.xxx.xxx.xxx:80 0.0.0.0:*          TIME_WAIT
tcp6  0      0      :::22              :::*               LISTEN

```
^ I typed that up, but that's what I got from the server when I ran netstat -ant.

Thank you all for your help,
Henry

---

### Post by ken22 on 2009-01-17
On the client side remove the entry for that server from .ssh/known_hosts
 by opening it in an editor.

Then run your scp command again.

---

### Post by honkthrast on 2009-01-17
Oh, and I get the same timeout if I try this:

```
user@serverName:$ ssh user@clientName
```

or

```
user@clientName:$ ssh user@serverName
```

If it matters, the user name is the same on both computers.

---

### Post by ken22 on 2009-01-17
Same issue, 

remove the entry for each machine from .ssh/known_hosts

---

### Post by honkthrast on 2009-01-17
Aha, I knew it was easy.  Thank you very much, ken22, for the help.

---

