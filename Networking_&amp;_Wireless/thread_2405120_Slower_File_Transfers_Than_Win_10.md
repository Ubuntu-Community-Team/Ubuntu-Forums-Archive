---
title: "Slower File Transfers Than Win 10?"
date: 2018-11-01
forum: Networking &amp; Wireless
---

### Post by michael. on 2018-11-01
I ran across a youtube video where the person was complaining that windows was able to transfer large files over a LAN faster than Linux and since he works on multimedia for a living he was moving off Linux for his production environment.

I decided to do some testing myself because I have always had the impression that linux networking was much better than windows.

For my test environment I am using a NAS (FreeNAS) connected to a gigabit wired network. I have both SMB and NFS shared configured on the NAS. My workstation is fairly current, I7 8700K processor, 32GB RAM and I am using all SSD's on the system, the NIC is an onboard Realtek connecting at gigabit. These are all bare metal installs on the same hardware. For networking it is wired to the same switch that the NAS is on. For my test file I am using a 5GB file, an ISO image. Here are the results I came up with:

Ubuntu 18.10 (Gnome DE)

NFS:      60MB/s
SMB:      85MB/s

Windows 10

SMB:     115MB/s

I thought their must be something buggy in this new release so I installed Fedora instead. Fedora gave me exactly the same download speed, I also tried using the KDE DE instead of Gnome with the same result. The idea came to me that perhaps it was a slower SSD issue so I installed Ubuntu on an SSD that Windows could download at the higher speed on, no difference. Next I thought perhaps the speed windows was giving me was off so I logged into my NAS and verified the network bandwidth out of the NAS was greater under windows.

Unlike the guy on youtube I do not do huge downloads and I am not insterested in using a windows install as my daily driver. Has anyone else noticed this speed difference and if so come up with any solutions?

Mike

---

### Post by michael. on 2018-11-01
As an update I discovered something interesting. When I opened a terminal session, mounted the SMB share, and copied the file from the command line using scp I got the same speeds as windows. It seems like copying files using a GUI (KDE or Gnome) is slower then at the terminal. Also this happens with Xorg or Weyland.

Mike

---

### Post by Holger_Gehrke on 2018-11-01
It's a known problem. There are abstraction layers that make it possible to treat all file systems (and a lot of things that are not really file systems, like a MTP-connection to a smart phone, ssh connections etc) the same. These are used when mounting through the GUI. That high level of abstraction comes at a severe performance cost, so if you know what you are using and use it often (or often enough) you use traditional mounting (through the command line or /etc/fstab) and get better performance. To see for yourself that it's not the GUI itself but the way it mounts things at fault, try the following experiment: mount the share through the GUI. You'll find it's accessible from the command line as a subdirectory of /run/user/ID/gvfs/ (replace ID with your numeric user id as printed by the id command; that's the directory used on Ubuntu 18.04, 18.10 should be using the same - if it isn't, look in /proc/mounts for the mount point of gvfsd-fuse). Time some copying operations with 'cp' to and from the share. They should be slow, on the same level as copying through a graphical file manager.

Holger

---

