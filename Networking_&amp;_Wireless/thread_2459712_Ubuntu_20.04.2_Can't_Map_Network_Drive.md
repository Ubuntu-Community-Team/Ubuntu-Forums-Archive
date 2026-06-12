---
title: "Ubuntu 20.04.2 Can't Map Network Drive"
date: 2021-03-24
forum: Networking &amp; Wireless
---

### Post by sparks79 on 2021-03-24
I have been using Zorin and as far as mapping network drives it is as easy as pie.
I don't have to make any changes, just look for the network drive and Map it.
My situation is quite common, I have Cat 5 Cable Cable Connected to a Hub with 3 PC's on it and d-link NAS Box, Which can All be Mapped by Windows and Zorin without making any changes to Settings.
But here in Ubuntu it's almost Impossible and the only way to do it is by using heeps of commands and scripts, just to confusing for a novice.
There must be some Easy Way.
Any help would be appreciated

---

### Post by Morbius1 on 2021-03-24
You didn't provide enough information in your post so the following is just a flat out guess:

The latest version of Zorin uses version 4.7.6 of samba. Ubuntu 20.04 uses 4.11.6.

In order for Ubuntu 20 to act like Zorin you need to set SMB dialects back to the way they were in the 4.7.6 era. This involves editing /etc/samba/smb.conf and right under the **workgroup = WORKGROUP** line add these two:
```
client min protocol = NT1
server min protocol = NT1
```

Then reboot your Ubuntu box. A restart of smbd may not be enough so a reboot is your best bet.

If this represents something you don't want to do don't use Ubuntu - at least don't use the latest Ubuntu.

---

### Post by RobertoRecordo on 2021-08-24
This is a comment, I require no help.

I installed Xubuntu 21.04, and discovered I could not connect to SMB shares, and that the printer attached to the new 21.04 system was not available to other systems on the network.

I did edit /etc/samba/smb.conf
```
client min protocol = NT1
```

After rebooting I could see the NAS in the file manager. I could see folder names but not open them.
I have suspected that this was not consistent, even on earlier versions of Ubuntu, and it seemed that the on/off state of a windows computer on the network was involved.

An experiment proved that booting the windows machine before booting Ubuntu allowed the Ubuntu machine to access the NAS.


Having done that, I edited  /etc/samba/smb.conf
```
client min protocol = NT1 
server min protocol = NT1
```

Now when I boot Ubuntu with no other system running it immediately allows access to the NAS

I hope this helps someone!

And thanks to [**[COLOR=#000000]Morbius1[/COLOR]**]("https://ubuntuforums.org/member.php?u=982144")                                 who has answered this question countless times!

---

