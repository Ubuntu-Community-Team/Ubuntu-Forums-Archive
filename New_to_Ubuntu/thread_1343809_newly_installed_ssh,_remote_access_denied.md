---
title: "newly installed ssh, remote access denied"
date: 2009-12-02
forum: New to Ubuntu
---

### Post by ernieball on 2009-12-02
Hi.

I just installed ssh to connect remotely with putty, but I always get an access denied by putty, even though Im sure Im typing the right password.

Do I have to add ssh-users or something?

What am I missing?

Thanks for any help...

---

### Post by yeats on 2009-12-02
On the computer you're trying to connect to, you have to have the openssh-server package installed... Have you installed that?

---

### Post by ernieball on 2009-12-02
Yes, I ran apt-get install ssh before.

Now I get:

benkvi@ubu:~$ sudo apt-get install openssh-server
[sudo] password for benkvi: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
openssh-server is already the newest version.
openssh-server set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 139 not upgraded.

so i guess so :)

---

### Post by slakkie on 2009-12-02
Have a look in your logs, and paste them here if needed. Without our telepathic powers we cannot say anything useful.

---

### Post by ukripper on 2009-12-02
More info needed - Are you trying to connect from Local network or from external?

---

### Post by ernieball on 2009-12-02
Ok, I got it. A little embarassing though, as I only had my username wrong... checking the logs. What a great idea :)

thx for the support :P

---

