---
title: "share external hard drive over network"
date: 2007-04-02
forum: Networking &amp; Wireless
---

### Post by Ryan8720 on 2007-04-02
I have an external USB hard drive that is formatted to FAT32.  I had it connected to my Windows laptop and had is shared over the network.  My Ubuntu desktop could access it.  Now I want to connect it to the desktop and share it over the network.

The hard drive mounts fine and I can access it, but I don't know how to share it over the network.  Any help is appreciated. Thanks.

---

### Post by chadlewis on 2007-08-09
Sorry to hijack your thread, but I'm actually having a very similar issue, though I think I've gotten a bit further than you. 

I can see the share in Places -> Network -> [Machine Name], however when I try to enter the directory I get an error dialog: 

> 
The folder contents could not be displayed.
Sorry, couldn't display all the contents of "FILES".

My smb.conf contains the following:

[PHP]   netbios name = MACHINENAME
   workgroup = WINDOWSWORKGROUP[/PHP]

and then later:

[PHP]
[FILES]
path = /media/FILES
available = yes
browsable = yes
public = yes
writable = yes
guest ok = yes[/PHP]

Adding the following line to my fstab results in a weird sort of dual mounting, where I can actually view the contents of the mounted directory, but it's not the *correct* directory, so it's empty, so I've taken it out for the time being and I'm just letting it auto-mount at boot.

[PHP]
#/dev/disk/by-id/usb-WDC_WD-ANDSOMEHEXSTUFFYOUDONTNEEDTOKNOW:0-part1 /media/FILES vfat user,noauto,umask=077 0 0[/PHP]

FYI, I've done the chmod 777 thing about a bazillion times, but I'm not sure if that sticks after a reboot. I've gotten conflicting information on that. 

Probably the strangest part about all of this is that every machine reacts differently to the situation. The one Windows machine on my network can view, read and write to the share. Through the "Network" view the host machine can see it's own **directory**, but trying to enter it gets me that error message above (though I have no problems accessing the directory through any other means on that machine). The other Ubuntu machine can see the **server**, but trying to enter it gets me that message above.

I've been fighting with this for a week, and I'm stumped.

---

### Post by chadlewis on 2007-08-10
Anyone?

---

### Post by chadlewis on 2007-08-10
Bueller? :-|

---

### Post by chadlewis on 2007-08-10
And one last time before I give up and switch back to a Windows-based server...

---

### Post by Crimble on 2007-08-11
"I have an external USB hard drive that is formatted to FAT32. I had it connected to my Windows laptop and had is shared over the network. My Ubuntu desktop could access it. Now I want to connect it to the desktop and share it over the network.

The hard drive mounts fine and I can access it, but I don't know how to share it over the network. Any help is appreciated. Thanks."


Places > Computer > File System > Media > ~~~ here you will see the folder that is associated with the drive you want to share, share this and your drive will be public.  :guitar:

---

### Post by prince_niceguy on 2007-08-11
install samba and share the same. You can find the guide here.

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server](http://ubuntuguide.org/wiki/Ubuntu:Feisty#Samba_Server)

hope that helps.

---

