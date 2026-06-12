---
title: "Samba name resolution problem"
date: 2007-06-24
forum: Networking &amp; Wireless
---

### Post by complexgeek on 2007-06-24
Hi.
I'm having a very strange problem with samba networking on Kubuntu 7.04. The computer seems to be having an identity crisis.
This is what is supposed to be output from smbtree (run on an OS X system):
```

SUNNYDALE
        \\WILLOW                        willow server (Samba, Ubuntu)
                \\WILLOW\IPC$                   IPC Service (willow server (Samba, Ubuntu))
                \\WILLOW\media
                \\WILLOW\music
                \\WILLOW\data
                \\WILLOW\cdrom                  Samba server's CD-ROM
                \\WILLOW\print$                 Printer Drivers

        \\BUFFY                         Buffy server
                \\BUFFY\ADMIN$      IPC Service (Buffy server)
                \\BUFFY\IPC$            IPC Service (Buffy server)
                \\BUFFY\downloads
                \\BUFFY\www
                \\BUFFY\data
                \\BUFFY\print$          Printer Drivers

```
Willow is the workstation I'm having issues with, Buffy is a fileserver. When smbtree is run on Willow the output is
```

SUNNYDALE
        \\WILLOW                        willow server (Samba, Ubuntu)
                \\WILLOW\IPC$                   IPC Service (willow server (Samba, Ubuntu))
                \\WILLOW\media
                \\WILLOW\music
                \\WILLOW\data
                \\WILLOW\cdrom                  Samba server's CD-ROM
                \\WILLOW\print$                 Printer Drivers

        \\BUFFY                         Buffy server
                \\BUFFY\IPC$            IPC Service (willow server (Samba, Ubuntu))
                \\BUFFY\media
                \\BUFFY\music
                \\BUFFY\data
                \\BUFFY\cdrom           Samba server's CD-ROM
                \\BUFFY\print$          Printer Drivers


```
Buffy's resources are those on Willow, and accessing them simply accesses the resource on Willow.
Obviously Samba is obtaining the list of hosts correctly as Buffy is showing the correct description, but when it lists the resources, it is listing its own. Obviously there's an issue with name resolution where resolving Buffy ends up pointing to Willow. but I can't figure out where. It's not in smb.conf as far as I can see. Any suggestions?

---

