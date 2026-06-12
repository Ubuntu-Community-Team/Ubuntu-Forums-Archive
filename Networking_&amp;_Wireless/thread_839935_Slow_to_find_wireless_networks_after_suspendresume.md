---
title: "Slow to find wireless networks after suspend/resume"
date: 2008-06-24
forum: Networking &amp; Wireless
---

### Post by EricDB on 2008-06-24
After my laptop resumes from sleep, it seems like it takes much longer now under Hardy than it used to with Gutsy to find and connect to a wireless network.

After I restore, I can keep running "iwlist scanning" to see which networks come up.  Initially none do, then one or two, then maybe none again, then a different one or two, and so forth.  The names will accumulate in the NetworkManager list as they're (slowly!) found.  

Finally, when my network appears in the scan, NetworkManager will connect.  Sometimes it takes nearly a minute after restore to find and connect.  This behavior is identical on my home and campus wireless networks.

Why can it only find a few networks at a time?  Is it a channel hopping thing?  Can I tell it to look on a certain channel first?

---

### Post by mikeytag on 2008-08-05
Not sure if it helps at all, but I experience the exact same slowness. However, I am incredibly happy that suspend/hibernate work at all and I can even get a wireless connection back. In the past, I would have to reboot or many times suspend would just plain not work. I will try to investigate the issue on my machine and if I find anything out I will post it here.

FWIW, I am running an HP Pavilion 9233cl (Intel Duo Core/Intel Wireless)

---

### Post by ezzieyguywuf on 2008-11-30
I am experiencing similar issues as the OP. I notice especially when I'm moving from my home network to my campus network, with the computer suspended, it has issues finding any network. If i click on the wireless icon in my tray, sometimes no networks appear. Then, if I right-click to disable then re-enable the wireless card, a few more will appear. If I do it again a few different ones might appear. Sometimes the network I'm looking for never appears.

I've noticed recently that if I select "Connect to Hidden Wireless Network" theres an option to choose my home network and that usually seems to work, but why would it be hidden? 

Also, my main concern (as with the OP) is the slowness of this whole process. Can we speed it up at all?

---

### Post by rhcm123 on 2008-11-30
This is a problem with the system restarting the dameon processes. I have seen this problem multiple times before this thread, but it really is the system bringing everything up after a suspend (which is not an easy thing for the computer to do). I had a friend who had to wait 10 minutes for the system to get his wifi after a hibernate.

---

### Post by onlythetim on 2008-12-05
> **rhcm123 said:**
> This is a problem with the system restarting the dameon processes. I have seen this problem multiple times before this thread, but it really is the system bringing everything up after a suspend (which is not an easy thing for the computer to do). I had a friend who had to wait 10 minutes for the system to get his wifi after a hibernate.

Is it possible to raise the the priority of the wifi daemon, or somehow get it earlier in the queue of tasks after a suspend?  Often, I turn on my computer just to check something on the internet, so for me connecting quickly would have a very high priority.

---

### Post by nelliott71 on 2008-12-27
*BUMP*  :)

I have the same complaint.  HP DV9207us laptop with intel 3945ABG wireless.

It takes around 60-90 seconds to get wifi connected again after suspend.  I would *LOVE* to see this fixed.  I have poked around in the /etc/acpi directory and /etc/defaults/acpi-support, and tried to make some sense out of the stuff in dmesg, but so far this seems to be above my pay grade. LOL

Merry Christmas!!

---

