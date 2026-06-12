---
title: "iBook Internal Wireless"
date: 2006-08-20
forum: Networking &amp; Wireless
---

### Post by fix3r on 2006-08-20
I just installed ubuntu on my Mac iBook and I looked at the networks and all it said is there was modem and ethernet. I was looking for where my internal wireless would be but it didn't show up. What do I need to do to get my internal wireless connectivity up on the ubuntu? I am able to connect it through ethernet but I want to be able to work wirelesly throughout the house. ANy suggestions? THank you.

---

### Post by raysaunders on 2006-08-21
You might try this thread....


[http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm4311](http://ubuntuforums.org/showthread.php?t=185174&highlight=bcm4311)

---

### Post by insyzygy on 2006-08-21
Which model ibook is this. If its the ibook g3 then the wireless card is the airport (not extreme). In this case all you should have to do is.

```
sudo modprobe airport 
```
and 
```
iwconfig 
```
should report you now having an eth1, the wifi card.  

In fact today I just installed an airport card on this ibook g3 with ubuntu and am typing this over wifi. 

If its an ibook g4 then you have an airport extreme which uses a different chip and needs the broadcom bcm43xx driver. You will have to do the firmware extraction. The link above has some discussion of this as does 

[link]("https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Dapper")
You should probably search for airport extreme on the forums.

---

