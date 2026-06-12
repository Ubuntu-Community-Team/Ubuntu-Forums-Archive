---
title: "How do I remove gvfs samba shares from the command line?"
date: 2014-06-12
forum: Networking &amp; Wireless
---

### Post by j.daniel on 2014-06-12
**Hi!,**

  ...small background; I'm helping out a friend with an Ubuntu machine (currently running 14.04). As this machine (and my friend) lives several hundred kilometers away, I pop in via ssh when there's trouble and do some command line magic.

  The current problem has to do with samba. My friend has added a few shares via nautilus and its not working well, so I thought I'd try the old-school / kernel-cifs way via [FONT=Courier New]smb.conf[/FONT] instead. My understanding of gvfs is superficial at best, but I have understood enough to realise that shares set up this way are stored in [FONT=Courier New]/var/lib/samba/usershares[/FONT] .

  My question is simply; will removing the files in [FONT=Courier New]/var/lib/samba/usershares[/FONT] remove the nautilus created shares in a clean way, or do I need to edit / remove some other files as well?

  Or perhaps; is there a [FONT=Courier New]gvfs-magicCommand[/FONT] that is even more appropriate?

Cheers!
/ Daniel

---

### Post by steeldriver on 2014-06-12
I don't know if it's necessary, but you possibly do

```

gvfs-mount --list

```

to identify the SAMBA-mounted shares and mountpoints, and then

 ```

gvfs-mount --unmount <mountpoint>

```

to unmount them gracefully - HOWEVER if you're doing that over SSH, you will probably need some quite strong DBUS-fu in order to attach to the running session - possibly something like

```

eval export $(grep -z "DBUS_SESSION_BUS_ADDRESS" /proc/$(pidof gvfsd)/environ)

```

first to grab and set the DBUS_SESSION_BUS_ADDRESS token.

---

### Post by bab1 on 2014-06-12
> **j.daniel said:**
> **Hi!,**

  ...small background; I'm helping out a friend with an Ubuntu machine (currently running 14.04). As this machine (and my friend) lives several hundred kilometers away, I pop in via ssh when there's trouble and do some command line magic.

  The current problem has to do with samba. My friend has added a few shares via nautilus and its not working well, so I thought I'd try the old-school / kernel-cifs way via [FONT=Courier New]smb.conf[/FONT] instead. My understanding of gvfs is superficial at best, but I have understood enough to realise that shares set up this way are stored in [FONT=Courier New]/var/lib/samba/usershares[/FONT] .

  My question is simply; will removing the files in [FONT=Courier New]/var/lib/samba/usershares[/FONT] remove the nautilus created shares in a clean way, or do I need to edit / remove some other files as well?

  Or perhaps; is there a [FONT=Courier New]gvfs-magicCommand[/FONT] that is even more appropriate?

Cheers!
/ Daniel

Just delete the the file in the */var/lib/samba/usershares* directory ( i.e. /var/lib/samba/usershares/<share> ).  It is the only file that defines the gvfs share.  The icon on the shared directory in Nautilus will go away in the next user session when Nautilus looks to see if that directory is shared or not.

---

### Post by bab1 on 2014-06-12
duplicate  :-(

---

### Post by j.daniel on 2014-06-13
> **steeldriver said:**
> I don't know if it's necessary, but you possibly do

```

gvfs-mount --list

```

to identify the SAMBA-mounted shares and mountpoints, and then

 ```

gvfs-mount --unmount <mountpoint>

```

to unmount them gracefully - HOWEVER if you're doing that over SSH, you will probably need some quite strong DBUS-fu in order to attach to the running session - possibly something like

```

eval export $(grep -z "DBUS_SESSION_BUS_ADDRESS" /proc/$(pidof gvfsd)/environ)

```

first to grab and set the DBUS_SESSION_BUS_ADDRESS token.

Thank you steeldriver, that expanded my knowledge of gvfs with at least 300% ;)
 

> **bab1 said:**
> Just delete the the file in the */var/lib/samba/usershares* directory ( i.e. /var/lib/samba/usershares/<share> ).  It is the only file that defines the gvfs share.  The icon on the shared directory in Nautilus will go away in the next user session when Nautilus looks to see if that directory is shared or not.

Great! I'll do that. Thank you!

Cheers
/ Daniel

---

