---
title: "fstab without network"
date: 2008-08-08
forum: Networking &amp; Wireless
---

### Post by brononi on 2008-08-08
Hey,

Shortly i moved from windows towards Pardus 2008.
Everything is going great, except mapping of shared folders.  I've got a NAS with some shares.

I'm using a dekstop machine with wire, and with this, i'm having no problems. I've put the things into fstab, and every boot, the shared folders are properly mounted.

I've got also a portable, and when i'm using the cable, all goes well. 
If disconnect the cable, with the wireless connected, everything goes well. 
But when I boot with the cable disconnected, it goes wrong. The pardus hangs, and only thing (at least for me) to do is a reinstallation. A second boot stops also...

I think that problem is located in the fact that the wireless is started after the fstab?

It would be nice to have the shares mapped every time booted indoor. I'm a little afraid of this. What happens fe if the network is down? Will my fixed computer also fails to boot?

/etc/fstab
```

//192.168.111.5/Public /home/gebruikerX/Publiek cifs auto,credentials=/home/gebruikerX/.Smbcredentials,file_mode=0777,dir_mode=0777 0 0
//192.168.111.5/gebruikerX /home/gebruikerX/Prive cifs auto,credentials=/home/gebruikerX/.Smbcredentials,file_mode=0777,dir_mode=0777 0 0
```

/home/gebruikerX/.Smbcredentials
```
username=GebruikerX
password=WachtwoordY
```

---

### Post by ilrudie on 2008-08-08
I don't know about cifs but NFS has a soft mount option for this reason (to prevent boots from hanging when the network is messed up or the share not available).  Look at if CIFS has this.  Being a networked file system there is a chance it will.  This is also why best practice for managing *nix systems is to not mount networked file systems in fstab.

---

### Post by brononi on 2008-08-09
Apperantly there's also the option soft for the cifs.

xxxxx cifs soft,auto,creden xxxxxxxx


I can boot without any problems if the wireless is on now (so I just removed the networkcable). But once i disable the network completely (cable and wireless) on softwarelevel, he won't boot anymore. :(

When i retach my cable, it stays the same. 

Since i can't figure out how to start a kind of safe mode, only thing left to do is reinstalling the computer... :mad:

---

