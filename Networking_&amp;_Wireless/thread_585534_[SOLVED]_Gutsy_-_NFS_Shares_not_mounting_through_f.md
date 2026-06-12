---
title: "[SOLVED] Gutsy - NFS Shares not mounting through fstab?"
date: 2007-10-21
forum: Networking &amp; Wireless
---

### Post by Jose Catre-Vandis on 2007-10-21
I've been on Edgy for about a year, NFS as client from my server works fine.

Created a new installation of Gutsy and copied over my fstab settings, installed portmap and nfs-common for nfs client use and set up the directories for the mounts. I am using the same fixed IP as with Edgy

Nothing happens on boot, no nfs shares are mounted. if I ```
sudo mount -a
``` they all come up as expected and work as expected.

here is a typical mount line:
```
10.10.10.70:/media/share1 /media/share1 nfs rsize=8192,wsize=8192,timeo=14,intr,bg
```

Again, this works fine if I boot back into Edgy.

Is something different happening in Gutsy to stop fstab being read and actioned upon?

---

### Post by Jose Catre-Vandis on 2007-10-22
Found the reason why! This was due to my /etc/network/interfaces settings, which were set up, as in my Edgy install to create a network bridge and tap interfaces for virtualbox. This is a shame as it worked brilliantly in Edgy.

I'll have to do some scripting to get the tap interfaces up and running after boot has finished. It's a workaround rather than a solution, but here is the resultant script, slows down the boot process after login a bit but gets the job done.
```
#! /bin/bash
#network interfaces conversion script
#changes interfaces file after boot, restarts networking then resets interfaces file

#copies the bridge and tap interfaces file to interfaces
cp /etc/network/interfaces.tap /etc/network/interfaces
#restarts networking to enable bridge and taps
/etc/init.d/networking restart
#reinstates original interfaces file
cp /etc/network/interfaces.static /etc/network/interfaces

exit
```

Some explanation, I placed a reference to the script in /etc/rc.local, so that it ran after everything else booted up and loaded. I created two additional files in /etc/network - interface.static (simple static IP setup) and interface.tap (complex bridging and tap interface creation). The script copies over the tap interfaces file, restarts the network and then reinstates the simple interfaces file (ready for the next reboot). Not pretty, but it works. Advice on a better solution is always welcome. Had a look at creating dynamic tap interfaces, but this required a bridge to be in place, so would probably have to do what I have done anyway.

---

### Post by AndyC_772 on 2007-12-08
I have exactly the same problem, now I've upgraded from Edgy to Gutsy I have to 'sudo mount -a' to get my NFS shares to mount, rather than them being mounted automatically at start-up.

My mount lines look like this:
```
192.168.1.201:/media /mnt/media nfs rsize=4096,wsize=8192,timeo=60,intr
```

I'm using a wireless network, managed using Wicd, which was the only way I could find to connect to a WPA protected network with a hidden SSID and a static IP address. It works fine. My /etc/network/interfaces, therefore, contains no reference to the wireless LAN.

Oddly, the first time I booted my PC this morning, some (but not all) of the shares DID mount OK - but on subsequent reboots none of them are connected.

Ideas please?

---

