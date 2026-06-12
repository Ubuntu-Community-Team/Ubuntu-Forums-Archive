---
title: "Vista and Ubuntu file sharing"
date: 2007-09-02
forum: Networking &amp; Wireless
---

### Post by danbrownlow on 2007-09-02
Hey all, I need some help trying to get Vista to Network with Ubuntu 6.06. I've installed Samba, configured the file and tried mapping to the host which is the Ubuntu Desktop but I can't seem to get anything to work, does anyone know a how to to get it to work? Or is there just no way that Vista will network with Ubuntu.
Any help would be appreciated.
Dan

---

### Post by Zorael on 2007-09-02
Does connecting directly to the IP work? Meaning, instead of \\CHARLES, do \\192.168.0.15.

Further, is your Ubuntu box bridging networks? I experienced some samba anomalies when I tried to set up a bridge to make my Windows installation in VirtualBox get its own IP. I guess it could be manually configured with the interface setting in smb.conf.

Lastly, does typing smbtree in a terminal output anything?



Including this just in case it helps anything:

> **Zorael]Edit /etc/samba/smb.conf.

```
   workgroup = XXXXXXXXXX
```
Find and modify this line to match the workgroup of your Vista machine(s).

```
   server string = %h blah blah whee
```
You can also change this line to add a description to your machine, now that you're at it. %h translates to the name of your Ubuntu box - in lowercase, I think.

Now, at the very bottom you'll want to define your shares. Unless you have a modified smb.conf, with its commented lines deleted, there's a short documentation as to how you can configure them. NOTE that this is the least secure version said:**
> 
path = /media/main/video
writable = no
read only = yes
guest ok = yes
browseable = yes

[audio]
path = /media/main/audio
writable = no
read only = yes
guest ok = yes
browseable = yes

[share]
path = /media/main/share
writable = yes
guest ok = yes
browseable = yes
```

---

### Post by danbrownlow on 2007-09-03
I tried using typing in the IP instead, but this hailed no results :(  What I tried with the shares was setting the whole home folder. Then I mapped the drive, but to make sure, I use \\hostname\sharename, how do I find out the hostname =[ I checked under admin
Dan

---

