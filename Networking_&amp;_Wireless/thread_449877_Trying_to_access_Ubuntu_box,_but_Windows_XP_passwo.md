---
title: "Trying to access Ubuntu box, but Windows XP password prompt not working"
date: 2007-05-20
forum: Networking &amp; Wireless
---

### Post by kexodusc on 2007-05-20
I followed a few of the Samba guides and have made some good progress towards getting my laptop with Windows XP (wireless) and my Ubuntu machine up and running on my network.

The Ubuntu box can see the XP box on the network, access the shared files, etc.
The XP box can see the Ubuntu machine, but when I try and access the shared files, I get a prompt for the user name and password.   Yes, I added a Samba user name and password, but when I enter those I don't get access to the Ubuntu shared files.
Anyone got any ideas where I'm going wrong?

---

### Post by ym4546 on 2007-05-20
I'm having a similar problem. I think this is a result of the recent samba update (that I got on May 16). Here's my post about it:

[http://ubuntuforums.org/showthread.php?t=449991](http://ubuntuforums.org/showthread.php?t=449991)

kexodusc: what version of samba do you have?

---

### Post by kexodusc on 2007-05-20
> **ym4546 said:**
> I'm having a similar problem. I think this is a result of the recent samba update (that I got on May 16). Here's my post about it:

[http://ubuntuforums.org/showthread.php?t=449991](http://ubuntuforums.org/showthread.php?t=449991)

kexodusc: what version of samba do you have?

Hmm, not sure what version, I just did a 
```
sudo apt-get install samba smbfs
```
today...whatever version that pulls from the repos I guess...how would I check?

---

### Post by kexodusc on 2007-05-21
> **kexodusc said:**
> Hmm, not sure what version, I just did a 
```
sudo apt-get install samba smbfs
```
today...whatever version that pulls from the repos I guess...how would I check?

Okay, I have Version 3.0.24-2ubuntu1.1

Maybe you're on to something???

---

### Post by bobmac on 2007-09-04
Folks,

It seems that I've got the same problem. Has anyone found out how to fix it yet?

regards,

Bob

---

