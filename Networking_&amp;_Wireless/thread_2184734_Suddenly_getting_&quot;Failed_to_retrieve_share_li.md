---
title: "Suddenly getting &quot;Failed to retrieve share list from server&quot;"
date: 2013-10-30
forum: Networking &amp; Wireless
---

### Post by Rocket J Squirrel on 2013-10-30
Ubuntu 12.04 (running Lubuntu desktop)

Well this is a bit of a mystery. Up until this morning, everything was fine. I rebooted this computer for some reason, and now I cannot access the Windows network -- sort of. 

In PCManFM when I go to Go > Network Drives  then click on "Windows Network" I get "Failed to retrieve share list from server" followed by "The specified location is not mounted"

But I can get to shared folders on the network using "smb://hostname/shared folder name" in PCManFM's address bar. So I'm clearly connected to the network. 

In /etc/samba/smb.conf I have these two lines:
```
Workgroup = OurWorkgroupName
```
and
```
 name resolve order = lmhosts host wins bcast
```

I'm puzzled.

---

### Post by Rocket J Squirrel on 2013-10-30
Solved, my bad. I changed the hostname on another Linux machine on the network but used the wrong name. My local /etc/hosts had a different name, thus causing consternation and confusion all over the place. I guess.

---

