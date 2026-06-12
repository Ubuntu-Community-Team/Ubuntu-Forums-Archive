---
title: "[SOLVED] How to automount NAS at startup with wireless connection?"
date: 2008-11-19
forum: Networking &amp; Wireless
---

### Post by stormtrooprdave on 2008-11-19
I have a network drive with all my media on and need help to have it automount on startup.

Firstly can somebody tell me if the line I have added to fstab is correct?

//192.168.1.64/openshare/ mnt/networkspace cifs 0 0

The address is fixed, I have created the folder in mnt, there is no password or username on the NAS.

If I mount the drive by going to place>network>networkspace it appears on the desktop, which is where i want it to be, and the file path in nautilus is smb://networkspace/  

If I mount through terminal using sudo mount.smbfs //192.168.1.64/openshare/ mnt/networkspace cifs 0 0 then it mounts at mnt/networkspace but does not appear on the desktop. In fstab should I be using the address 192.168.1.64 or the name networkspace?

Please can somebody tell me exactly what to type in fstab?  Secondly, how do I get it to automount AFTER I've connected wirelessly?

---

### Post by stormtrooprdave on 2008-11-20
Solved this myself so for anyone else with similar problems here it is:

The problem was many of the threads here say to make the mount point in mnt/ when it needed to be in media/

My original fstab and mount point was //192.168.1.64/openshare/ mnt/networkspace cifs 0 0 but all I needed to do was change it to //192.168.1.64/openshare/ media/networkspace cifs 0 0 (creating the appropriate folder of course) and it mounted automatically after the wireless was connected.

---

