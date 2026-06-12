---
title: "Possible bug with SSHFS + AMD64?"
date: 2007-08-06
forum: Networking &amp; Wireless
---

### Post by dfreer on 2007-08-06
Hi all,

   After installing compiz fusion, I rebooted. I went to mount my remote SSH filesystem, as I normally do, and the entire system started to chug until I had to hard reboot. I went into gnome-system-monitor, and then launched my command, as shown:
```
sshfs 10.1.10.102:/ /media/sshfs/
```
No output came to the terminal, but I immediately saw my memory usage go WAY up. Plus, a huge number of processes labelled "sshfs" started showing up in the process list. After rebooting again, I tried:
```
sudo apt-get --purge remove sshfs
sudo apt-get clean
sudo apt-get install sshfs
```
And then tried just launching sshfs like so:
```
sshfs -v
```
The same thing happens. Can anyone else duplicate this behaviour, it seems whenever sshfs is launched this happens. Can't figure out why it is doing so, I haven't seen any updates/upgrades for sshfs.

Basically, normal memory usage as reported by system monitor is about 250 MBs of RAM (out of a 1 GB total), and 0 bytes of about 1.4 GB's of swap. When sshfs is run, it starts launching it's processes, and RAM gets so full it starts overfilling to swap, and then once swap gets close to full I get full system lockup. If I can kill the process beforehand, everything goes back to normal. Otherwise even restarting the X server doesn't help.

Any ideas?

---

