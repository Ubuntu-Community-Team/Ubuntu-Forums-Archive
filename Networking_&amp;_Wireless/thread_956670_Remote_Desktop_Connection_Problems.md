---
title: "Remote Desktop Connection Problems"
date: 2008-10-23
forum: Networking &amp; Wireless
---

### Post by Zelandeth on 2008-10-23
I'm thinking this is a configuration problem with the host machine - as it was working flawlessly beforehand - despite a somewhat irritiating tendency for this (the client) machine to hang up when viewing the remote desktop, requiring a hard reset to restore any sort of functionality whatsoever.  This only happens once in a blue moon though, so I'm really not worried about it.

I run a small scale web server here, which is an old Duron 1200 box which hides behind the sofa in the living room, connected by the wired network into the BT Homehub.  For a good six months, this was using an 11 year old 4.3Gb 2.5" harddrive I scavenged from some long dead laptop about 6 years ago - eventually I got around to upgrading this.

Got a package list from dpkg, and used dselect to reinstall all the packages on the new harddrive, then copied over /etc, /home and /var.  Eventually deciding this was the easy approch after spending many hours trying to work out how to get Grub to co-operate when cloning the drive - without success.

However since the reinstall, the one and only thing I've not been able to get working is the remote desktop access.

Prior to this, it was a simple matter of typing the internal IP address into the remote desktop client (having enabled it prior to disconnecting the monitor from the server when I was setting it up - and on the second attempt remembering to uncheck the "ask me for confirmation box!

However now, it just reports to me that the connection was closed whenever I try to connect.  Using TightVNC (under Wine) shows it initialising the connection - then reporting that it can't connect to the host.  Addresses and ports definitely match up.

I can still get into the system via XDCMP, but that's nowhere near as convenient.  

Admittedly, about the only time I actually need to log in is when adding a new user account or installing updates.  Still would be nice to have it actually working properly.

Anyone got any pointers?

Both machines are running 8.04 Desktop edition.  This one's 64-bit, server's 32-bit.  Yes I know I should probably be using server edition on the server...I may look into that in the future, it's behaved flawlessly for the last six months though...so I'm happy for now.

---

### Post by cariboo on 2008-10-23
I don't know if wine is the problem, but I would eliminate it just in case. There is a native version of tightvnc in the repositories, the less complications the better.

Jim

---

### Post by Zelandeth on 2008-10-24
Thanks for the pointer.  The only reason that the TightVNC client got installed was because someone asked me how to use it - and that seemed the quickest way to answer the question - it does definitely work though.

Using the native remote desktop viewer I simply get an error saying that the connection was closed as soon as I hit connect though.

---

