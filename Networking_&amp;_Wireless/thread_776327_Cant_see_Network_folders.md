---
title: "Cant see Network folders"
date: 2008-04-30
forum: Networking &amp; Wireless
---

### Post by columbo1977 on 2008-04-30
Hi Hope someone can help

My system can see all the shares on the machines on my network except the server?

running Linux Ubuntu 8.04 on this machine and Xp Pro on server(ZA firewall and ip addresses in trusted zone).

Samba usernames are the same. it sees all other machines just not the server? yet another laptop running ubuntu 7.10 can see the server???

must be a tweak or something to let it see the folders?

smb.conf is in /usr/share/samba/

Just thought I would add in case it helps someone identify the problem.

Turned off Firewall on server still would not see anything.

Other weird thing is when I click on a machine it pauses and the circle appears while it gets the shares. with the server there is no delay it just comes up with a empty screen as if it isnt even looking for anything?

Columbo1977

---

### Post by superprash2003 on 2008-04-30
are you able to ping the server from the hardy machine?

---

### Post by columbo1977 on 2008-05-01
yes they can both ping each other.

Vista is on the same machine dual booted and it can see all the folders.

---

### Post by superprash2003 on 2008-05-01
try smb://(ip address of server) in nautilus..

---

### Post by columbo1977 on 2008-05-01
I tried that several times last night and it would not come up with anything.

the machine is listed with the other computers in Network, but no folders? yet on the Ubuntu laptop it sees all?

---

### Post by elustran on 2008-05-03
Have either of you figured his out? I've been having a similar problem.  I upgraded my box from 7.10 to 8.04 recently and I can no longer access the shares I could in 7.10.  I'm getting a password prompt, but can't connect even when I put in the proper password (there actually is no password for the shares I'm trying to access).

---

### Post by elustran on 2008-05-03
Never mind! Got it working!

In Gutsy, I had my network files mounted into fstab like so, in case this helps someone else:

```
/network-directory 	/local-mount-point cifs userid="user",passwd="pass",rw 0 0
```

It's just that, for whatever reason, permissions to my mount point were set so my user couldn't even browse the directory...  I feel lame for not having caught that.

---

### Post by columbo1977 on 2008-05-21
I still havent firgured this out if anyone has any ideas?

---

### Post by columbo1977 on 2008-05-27
I am still having this problem and it seems to be a Hardy Heron problem.

Can anyone help?

Only thing I dont understand is I cant see the shares on only 1 computer, I can see all of the others on the network???

Columbo

---

### Post by columbo1977 on 2008-05-27
I have just used connect to server to connect to a share and it worked??

---

