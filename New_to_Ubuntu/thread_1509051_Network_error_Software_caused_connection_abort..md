---
title: "Network error: Software caused connection abort."
date: 2010-06-13
forum: New to Ubuntu
---

### Post by unix_user on 2010-06-13
Please excuse me for posting a question that's been repeatedly asked on ssh
timeouts. [I have searched prior posts and tried solutions suggested by other members
and still unable to have an uninterrupted ssh connection to my ubuntu server.]

I have Ubuntu 10.04 and connect to server from my Windows 7 laptop. I use
putty and experience random disconnects (sometimes stays alive for 2 minutes, sometimes stays alive for 30 mins) to my Unix session.

Does anyone have ideas how to address this issue. I use dyndns with ddclient that
updates IP address dynamically. 

I have also tried putty-login to Unix terminal and invoke screen (with timestamp at bottom)- still timeouts.

Putty on Windows 7:
Connection:
    Seconds between keepalives  5
    [x] enable TCP keepalives

Ubuntu 10.04
       /etc/sshd_config:     
             TCPKeepAlive yes
             ClientAliveInterval    300
             ClientAliveCountMax    0
       /etc/ssh_config 
             ServerAliveInterval    5
 I do restart ssh after changes, I have this problem even when on Ubuntu 9.x
I get this message on windows putty when it disconnects: Network error: Software caused connection abort.

---

### Post by dearingj on 2010-06-13
Perhaps you should try turning off keepalives. According to [this page]("http://tartarus.org/~simon/putty-snapshots/htmldoc/Chapter10.html#errors-connaborted"), "It can also occur if you are using keepalives in your connection. Other people have reported that keepalives fix this error for them. See section [4.13.1]("http://tartarus.org/~simon/putty-snapshots/htmldoc/Chapter4.html#config-keepalive") for a discussion of the pros and cons of keepalives."

---

