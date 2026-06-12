---
title: "ssh reseting"
date: 2007-04-01
forum: Networking &amp; Wireless
---

### Post by mwagz on 2007-04-01
My ssh connection keeps resting.....

Read from remote host host_name: Connection reset by peer
Connection to host_name closed.


ssh user@host_name

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
b2:11:94:bf:7d:c5:58:59:54:f4:e9:e8:c7:c7:0e:63.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:3
RSA host key for ppgp2 has changed and you have requested strict checking.
Host key verification failed.

---

### Post by jakev383 on 2007-04-01
> **mwagz said:**
> My ssh connection keeps resting.....

Read from remote host host_name: Connection reset by peer
Connection to host_name closed.


ssh user@host_name

@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
@    WARNING: REMOTE HOST IDENTIFICATION HAS CHANGED!     @
@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@
IT IS POSSIBLE THAT SOMEONE IS DOING SOMETHING NASTY!
Someone could be eavesdropping on you right now (man-in-the-middle attack)!
It is also possible that the RSA host key has just been changed.
The fingerprint for the RSA key sent by the remote host is
b2:11:94:bf:7d:c5:58:59:54:f4:e9:e8:c7:c7:0e:63.
Please contact your system administrator.
Add correct host key in /root/.ssh/known_hosts to get rid of this message.
Offending key in /root/.ssh/known_hosts:3
RSA host key for ppgp2 has changed and you have requested strict checking.
Host key verification failed.

It's trying to tell you that the fingerprint of the machine has changed, which means that someone may be impersonating the machine you're actually trying to talk to. 
Did you reinstall the machine you're trying to log into recently?  If so you'll need to delete the fingerprint entry for it in your ~/.ssh/known_hosts file.

---

### Post by mwagz on 2007-04-01
When I deleted the entries in /root/.ssh/known_hosts,i connected but it reset all the time.
How can I stop this reseting?

---

### Post by jakev383 on 2007-04-01
> **mwagz said:**
> When I deleted the entries in /root/.ssh/known_hosts,i connected but it reset all the time.
How can I stop this reseting?
It's the server that is resetting it's fingerprint. Do you have any control over that?

---

### Post by mwagz on 2007-04-02
I can connect to my machine from the server. i dont get disconnected.
But I do get disconnected when I log in from my machine.

---

### Post by jakev383 on 2007-04-02
> **mwagz said:**
> I can connect to my machine from the server. i dont get disconnected.
But I do get disconnected when I log in from my machine.
Right. When your machine logs into the server it sees that the fingerprint has changed (you'll want to see why it does this).
You can be a little more lenient on security and change the line in your /etc/ssh/ssh_config that has to do with this, and make it look like this:
   StrictHostKeyChecking ask

---

