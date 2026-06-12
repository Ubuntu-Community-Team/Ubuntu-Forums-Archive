---
title: "[SOLVED] Mount Windows &quot;Drive Letter&quot; &quot;Shares&quot; via Samba"
date: 2007-09-10
forum: Networking &amp; Wireless
---

### Post by Jamie Jackson on 2007-09-10
I can mount explicit shares just fine, but I'm having trouble with the syntax for the implied "drive letter" shares (e.g., "C$", "D$", etc.).

It's easy in Nautilus:
smb://corpdom%3Buser12@icf6153/C%24

```

$ sudo mkdir -p /media/icf6153/c ; sudo smbmount //media/icf6153/C%24 /media/icf6153/c -o username=user12,workgroup=corpdom,rw,fmask=775,uid=jamlin

Password: 
20051: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
SMB connection failed

```

Either smbmount won't connect to those implied windows ("letter") shares, or I've got a simple syntax mistake.

How is it done?

Thanks,
Jamie

---

### Post by Zorael on 2007-09-10
Perhaps it wants the $ sign as a \123 code. This is assuming it wants it expressed in the same way fstab does. And I have no idea what $ translates to. Perhaps the output of smbtree would answer that.

For instance, I know spaces translate to \040, making it "/media/windows/Documents\040and\040Settings".

If you do manage to mount it in Nautilus (or something similar), you could cat /etc/mtab and see how it's listed there.

---

### Post by Jamie Jackson on 2007-09-10
Good idea, but mtab doesn't list the Nautilus-connected share, and smbtree shows the shares unescaped:
```

WORKGROUP
        \\PLUTO          
                \\PLUTO\J$              Default share
                \\PLUTO\J              
                \\PLUTO\C$              Default share
                \\PLUTO\bak            
                \\PLUTO\Y              
                \\PLUTO\Audio          

```

man smbmount mentions the space escape you wrote about, but it says nothing of other special characters. Any other ideas? I tried a double dollar sign, but that didn't work either.

---

### Post by Jamie Jackson on 2007-09-10
I'm no closer, but I found a nice command along the way. I couldn't effectively use the smbtree command at work, because there are thousands of machines on the network. I found a targeted way to do it:
```

$ smbclient -L pluto -U jamie
Domain=[PLUTO] OS=[Windows 5.0] Server=[Windows 2000 LAN Manager]

        Sharename       Type      Comment
        ---------       ----      -------
        EP1270          Printer   EPSON Stylus Photo 1270
        E$              Disk      Default share
        IPC$            IPC       Remote IPC
        D$              Disk      Default share
        Media           Disk      
        print$          Disk      Printer Drivers
        F$              Disk      Default share
        ADMIN$          Disk      Remote Admin
        Audio           Disk      
        Y               Disk      
        bak             Disk      
        C$              Disk      Default share

...etc.


```

---

### Post by Jamie Jackson on 2007-09-10
I thought I had tried this (and maybe I had but that particular server wasn't amenable?), but this works:

sudo mkdir -p /media/pluto/c; sudo smbmount //pluto/c\$ /media/pluto/c -o username=jamlin

...just a backslash for an escape.

---

### Post by Jamie Jackson on 2007-09-10
Eww, just found a funky bug with the forums software. It escapes html entities unnecessarily when a thread is marked "solved"

---

