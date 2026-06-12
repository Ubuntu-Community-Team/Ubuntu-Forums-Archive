---
title: "Cannot connect to windows network"
date: 2009-03-27
forum: New to Ubuntu
---

### Post by jrandolph on 2009-03-27
I have 2 other boxes running Microshit Windows on my network 
For some reason since I upgraded to 8.10 I cannot connect to those machines over the network, I have done it in the past and it worked fine.

I do have samba installed - when I go to Places>Network - The Windows Network is shown and when I click it it shows MSHOME which is the network I want but when I click that to connect it tell me "Unable to mount location" "Failed to recieve share list from server"

Can anyone tell me what has happened since I upgraded?

---

### Post by LowSky on 2009-03-27
did you go from Fiesty to Intrepid?

---

### Post by jrandolph on 2009-03-27
No I went from Hardy 8.04 to Intrepid 8.10

Sorry I never edited my Ubuntu version

---

### Post by LowSky on 2009-03-27
Then change your user details it still says Fiesty.

Anyway you might have to reset up your SAMBA settings. 
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

Personally WIndows networking has been hit or miss for quite some time now (since Hardy things havent really worked well). I cant even get my spare Ubuntu machine to see my normal desktop machine over Samba. I completely gave up on it.

Heck my PS3 has an easier time seeing the windows network then my Ubuntu machine... anyone else think that is wrong?

---

### Post by jrandolph on 2009-03-27
Tried uninstalling and reinstalling samba to no avail

so i guess i will just waste disks burning the files and walking the 20 feet to my ubuntu box and gettin them that way

---

### Post by mlentink on 2009-03-27
Might want to try this:
Open terminal and type 
```
smbtree
```Do you now see those windows boxes?

You can also try and connect to them through their ip-address, like 
smb://192.168.1.1/path/to/share

You might also want to read: [http://ubuntuforums.org/showthread.php?t=1028651&highlight=nautilus+bug+windows+shares](http://ubuntuforums.org/showthread.php?t=1028651&highlight=nautilus+bug+windows+shares)

---

### Post by jrandolph on 2009-03-27
Actually yes the output of that shows the one windows box that I am trying to connect to
but then came back with something else for the other box but that one makes no difference to me - i dont need anything from that computer

---

