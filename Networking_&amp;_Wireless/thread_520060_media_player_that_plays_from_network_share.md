---
title: "media player that plays from network share?"
date: 2007-08-07
forum: Networking &amp; Wireless
---

### Post by Moezzie on 2007-08-07
I am going completly insane here. For the past week ive tried to get my ubuntu boxes to play videos that are stored on my media server. It just wont work.
Well sort of...

The only player that could actually play the files was totem, but the performace isnt really the greates. Big laggs and bad sync.

All the popular players refuse to play the files.(VLC, MPlayer, SMPlayer,Xine).
Most of the players wont even give me an error, Xine however tells me that there is no input plugin.
Is there any way to make for example VLC play the files stored on my server? I can play my movies from both my Mac and Windows machines no problem but ubuntu just wont.

Please help!(a "it doesnt work would do it to")

---

### Post by Moezzie on 2007-08-07
im sorry, i just realized i posted this in the totally wrong forum i think.
If someone would be so kind and put it the media section?

---

### Post by nodows on 2007-08-07
It would be helpful to know exactly what your media server is.

Is it windows based?  Linux? Ubuntu? 
If the latter is it just a samba share or nfs etc?

---

### Post by olejorgen on 2007-08-07
If you are trying to play over samba:// or ssh:// via nautilus, only programs that rely on gnome-vfs will work. I'ts better to use **smbfs** and **sshfs**. This way every program can use the files.

I'm not sure, but I think vlc can be set up as a standalone streaming server

---

### Post by Moezzie on 2007-08-07
My server is an runs Fiesty and shares files over samba and smbfs.
I access it though "connect to server".

Never tried ssh, didt even know you could stream media through that. What would the difference to samba be?

---

### Post by olejorgen on 2007-08-08
Well, the data are transferred with ssh, so I guess it might be a little safter. (Not that you're streaming that suspicious videos, I hope :P)

Connect to server uses gnome-vfs, so this is not the best solution.

Install **smbfs** and do a **man smbfs**. I don't remember the exact syntax. Then access the media through the mounted folder.

---

### Post by liquid circuit on 2007-08-09
I think this requires smbfs to be installed...

I just setup a share on my girlfriends Powerbook G4 (OS X), enabled Windows File Sharing  on her laptop (Samba), and I am able to connect to the share with the following command:

```
sudo smbmount //192.168.0.102/HostShare /media/LocalMount -o username=hostuser,password=hostpassword,uid=1000,mask=000
```

When I run that, I get the following error:
> timeout connecting to 192.168.0.102:445
...however, the share has been mounted correctly and works.  The first thing I did to test the share was play some videos back from the share by browsing with Nautilus to /media/LocalMount, locating the video, and opening it with VLC.

Her computer is connected to the router through WiFi, and I'm wired to the router.

To avoid frequent hiccups, I had to increase the following setting (5000+): **VLC -> Settings -> Preferences -> Input/Codecs -> Access modules -> File -> Caching value in ms**... to see this setting the "Advanced Options" checkbox must be checked.

For me, it works... but there may be a better way to do this.  If I ever put together a dedicated media server, I hope setting up my Amarok music library this way is just as easy.  I would imagine you should be able to get this working, but you'll probably want to set it up to automount on boot; I haven't tried this yet since I'm only connecting to a laptop for the rare need to transfer files back and forth.

[For more help, see here.]("https://help.ubuntu.com/community/SettingUpSamba")

---

