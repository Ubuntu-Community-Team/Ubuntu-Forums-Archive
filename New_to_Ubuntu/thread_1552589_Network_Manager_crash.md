---
title: "Network Manager crash?"
date: 2010-08-13
forum: New to Ubuntu
---

### Post by Sylchat on 2010-08-13
This is strange, [the same]("http://ubuntuforums.org/showthread.php?t=1481871") happened to me. And adding the 2 lines for eth0 in interfaces made the notification area on the gnome panel crash. After putting it back, I can't see the network icon anymore.

Why Network Manager wouldn't handle the interface file after adding the 2 lines ?

---

### Post by Sylchat on 2010-08-13
Found another thread: [http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8395858](http://ubuntu-virginia.ubuntuforums.org/showthread.php?p=8395858)

"Reading around it seems to be a longstanding issue with the e1000 and e1000e kernel drivers, or more accurately the Intel firmware within the networking device, since there have been reports of issues with Windows 7.
I have found that using static IP and editing my /etc/NetworkManager/nm-system-settings.conf to read helps."

But still wondering why my eth0 MAC address is in "no-auto-default", no info on this.

edit:
Can't make it to work, except by clicking on NetworkManager to disable then enable Networking after login, I can't get a connection... What's strange is that I didn't have the problem in the first place.
I guess that's the realtek 8112L chip that's giving also trouble under win7 (1MB/s on LAN transfers, and the network card gets disabled and have to reboot windows :P ).

My workaround will be to put a pci network card...

edit2: Damn I just realized I get 1MB/s tranfer from my SAN under Ubuntu as well...

---

### Post by Iowan on 2010-08-13
Started a new thread for you...

---

