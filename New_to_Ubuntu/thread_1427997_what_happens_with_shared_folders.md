---
title: "what happens with shared folders"
date: 2010-03-12
forum: New to Ubuntu
---

### Post by Steven_S on 2010-03-12
Hi everyone! A pre-install question...

I would like to switch to Ubuntu on a desktop machine. Right now, it is running XP. It has one OS disk (60GB) and 3 1TB disks (NTFS). I have recycled that computer specifically to hold shared files, but I also use it to burn cd's, do upload and download jobs, ... 

Internet comes through a Thomson router, which also manages the home network via DHCP. The router connects to a Philips Net TV, and to another (old) Linksys router in another room. 

On that second old Linksys router, the desktop is wired, as well as a NAS. The shared printer is connected to the desktop. 

I have chosen this setup to allow for only one cabe to run from one room to another. Our laptops connect using wireless (from the Thompson). Everything works automatically and fine, and I would like to keep it that way :-). 

The TB disks on the desktop are used to store and serve files and to make back-ups. Some folders are specific to users - e.g. my girlfriend can see her private folder, but not min (this simply to avoid messing up content accidentally). Typically, we put our pictures there (using synctoy), and I rip dvd's to the drives for the TV to play.

My question is: if I put Ubuntu on that desktop (in dual-boot), what will happen to the access to the folders that already exist? 

I understand the user permissions in Ubuntu, and in Windows, things are pretty much set up. What I don't understand very well is the interaction between the two. 

Say I create a folder on that disk from a Windows machine (laptop). Who will be able to see it while logged in to the desktop?

And the other way around: say I create a folder working from Ubuntu. Who will be able to see it from a Windows machine? 

Could anyone point me to how this stuff works? Many thanks!

I would like to install the normal Ubuntu distro and have it be a fully functional machine so that the kids can play around on it (of course with their own limited permissions). My next question will probably be about the netbook remix interface :-).

---

### Post by audiomick on 2010-03-12
Hi.
The mechanism you are interested in is Samb. Some info here
[https://help.ubuntu.com/community/SettingUpSamba](https://help.ubuntu.com/community/SettingUpSamba)

and there is a rather in depth trouble shooting thread here
[http://ubuntuforums.org/showthread.php?t=1169149](http://ubuntuforums.org/showthread.php?t=1169149)

Theoretically, you should just be able to right click on a folder an share it using the "share options" entry (or something similar to that. On mine it is called "Freigabeoptionen" ) in the drop down menu. The process is quite similar to that in windows.

---

### Post by Steven_S on 2010-03-12
Thanks! I'll read up and come back if I should encounter problems!

---

