---
title: "No Network Settings after upgrade"
date: 2008-11-12
forum: Networking &amp; Wireless
---

### Post by Liviu-Theodor on 2008-11-12
I upgraded ubuntu 8.04.1 to 8.10, but the settings where I can change the network behaviour just disappeared from the menu. The network still works just fine, but I want to change the domain/workgroup, to be similar to the rest of computers in the same network. The Network Setting where present prior to upgrade, so, what can I do?

---

### Post by randy78 on 2008-11-12
right-click on the taskbar>Add to panel>Network Monitor>Add

---

### Post by lindsaydmd on 2008-11-12
> **randy78 said:**
> right-click on the taskbar>Add to panel>Network Monitor>Add
Hi Randy78,

Thanks for the tip, however I still can't fix the problem I have - same as Theodore has:

I installed 8.04 a few weeks back to act as a server for my main shared drive and printer (and to learn more about Linux - fed up with MS!). I have Windows Vista PCs and another Ubuntu laptop all hanging off a wireless network. This works fine allowing each box to access the internet etc. However...

With 8.04 I could set the Windows domain name (e.g. WORKGROUP)using the System/Network GUI and access shares & printers on the Ubuntu box from the Vista clients. It was a little unreliable, though (dropped the domain name between restarts) so I decided to try Intrepid (8.10).

Here's the question: I can't find anywhere in 8.10 Network GUI apps(GNOME) to set the Windows domain name in the same way as 8.04. Or am  missing something obvious..?

Any help much appreciated!

Thanks

---

### Post by Liviu-Theodor on 2008-11-12
> **randy78 said:**
> right-click on the taskbar>Add to panel>Network Monitor>Add

Is already there, and it shows me internet traffic, but I can not change anything there. How can I change network name and domain in ubuntu 8.10?

---

### Post by randy78 on 2008-11-12
Check here: [http://ubuntuforums.org/archive/index.php/t-315294.html]("http://ubuntuforums.org/archive/index.php/t-315294.html")

---

### Post by Liviu-Theodor on 2008-11-13
> **randy78 said:**
> Check here: [http://ubuntuforums.org/archive/index.php/t-315294.html]("http://ubuntuforums.org/archive/index.php/t-315294.html")

I tried to modify the /etc/hostname and /etc/hosts files, and that resulted the system had no more workgroup, still connecting in network though. So, the only thing useful there was:
> For future reference ;), what you describe is more specifically known as the "workgroup name". This is specific to Windows machines (and Samba sharing setups), and has exactly *zero* bearing outside of Windows World™.
And I exactly for Samba Sharing I was thinking...

---

### Post by Liviu-Theodor on 2008-11-13
And I forgot something: also is missing  (at least to my eyes) any way to change the IP of the system (from static to dynamic, for example).

---

### Post by randy78 on 2008-11-13
You can change the ip from static to dynamic by right-clicking the network manager icon in the taskbar|Edit Connections|select your connection (eth0, ath0, etc.)|Edit|IPV4 Settings| Manual

---

### Post by Liviu-Theodor on 2008-11-14
No, I can not, as I don't have Edit Connections menu, in fact all I can choose is pretty much nothing there. Only shows the current connection. Weird is that in 8.04.1 it was possible to modify these settings.

---

### Post by Liviu-Theodor on 2008-11-17
Also I wish to change the name of some PCs in the network (for example from Station4 to Station2). It must be the same issue.

---

### Post by Liviu-Theodor on 2008-12-15
The post [http://ubuntuforums.org/showpost.php?p=6263366]("http://ubuntuforums.org/showpost.php?p=6263366") gave me the answer how to change the workgroup, but the other network issues are still unsolved.

---

