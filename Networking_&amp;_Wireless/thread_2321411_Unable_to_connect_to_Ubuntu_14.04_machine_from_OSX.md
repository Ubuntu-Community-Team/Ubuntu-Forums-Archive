---
title: "Unable to connect to Ubuntu 14.04 machine from OSX 10.11.2"
date: 2016-04-22
forum: Networking &amp; Wireless
---

### Post by snap-hiss on 2016-04-22
I have had no problems connecting to my Ubuntu machine from an OSX machine to transfer files until very recently. Now I am getting connection failed and "check the server name or IP address" errors. Any suggestions?

---

### Post by snap-hiss on 2016-04-22
The file that I am sharing on the Ubuntu machine now has a tiny padlock icon on it, and I'm not sure what I did. I assume this is probably the source of the issue.  UPDATE: I got rid of the lock but I am still unable to connect from my mac.

---

### Post by Morbius1 on 2016-04-22
2 questions:

*** Is your Ubuntu machine up to date? If it is you installed a very buggy samba update. Run this to verify:
```
samba -V
```
If it comes back with this it's messed up:
> Version 4.3.8-Ubuntu

*** If the answer to the first question is "yes" are you trying to access the ubuntu server from OSX as "guest"?

If you are that will no longer work. You will get that exact error message. You need to specify a real user on the ubuntu machine and pass a samba password for that user.

You can just add yourself to the samba password database and use that one if your want:
```
 sudo smbpasswd -a whatever-your-user-name-is
```

---

### Post by snap-hiss on 2016-04-22
> **Morbius1 said:**
> 2 questions:  *** Is your Ubuntu machine up to date? If it is you installed a very buggy samba update. Run this to verify: ```
samba -V
``` If it comes back with this it's messed up:   *** If the answer to the first question is "yes" are you trying to access the ubuntu server from OSX as "guest"?  If you are that will no longer work. You will get that exact error message. You need to specify a real user on the ubuntu machine and pass a samba password for that user.  You can just add yourself to the samba password database and use that one if your want: ```
 sudo smbpasswd -a whatever-your-user-name-is
```  Ok, yes, it appears that is exactly the problem. That worked perfectly. Thanks so much.  You mentioned the newest update is buggy... I have noticed now that the transfers are working again it seems slow and erratic... is there anything that can be done to fix this?

---

### Post by Morbius1 on 2016-04-23
Based on the flood of bug reports submitted to not only individual Linux support systems but to Samba itself I think they are aware of the problem so all we can do is wait for the next release. 

*Samba really needs to handed over to something like the Apache Software Foundation or Red Hat or IBM or somebody that has the adult supervision and resources available to do testing. That is obviously my own opinion of course.*

---

