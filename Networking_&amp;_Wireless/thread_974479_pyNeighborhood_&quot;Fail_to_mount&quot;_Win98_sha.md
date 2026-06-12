---
title: "pyNeighborhood &quot;Fail to mount&quot; Win98 shares"
date: 2008-11-07
forum: Networking &amp; Wireless
---

### Post by JKyleOKC on 2008-11-07
I'm in the process of installing a new Xubuntu box which will eventually replace my remaining two Win98 boxes on my home-office LAN. The LAN uses Samba to interconnect the Win boxes and the four (now five) Linux systems, and (until I installed 8.04.1 LTS) was working exactly as expected. That is, full r-w sharing of all drives on all systems, from any of the six, thus allowing me to maintain any of them from any of the others. Security is not a problem here since I have an extremely tight single-point WAN interface that blocks intrusion attempts at the periphery.

However, when I upgraded one of the older Linux boxes from 7.04 through 7.10 to 8.04.1 using on-line upgrades, LinNeighborhood quit working and I had to install pyNeighborhood in its place. Suddenly the Win98SE boxes failed to mount, although the "scan" operation shows their shares properly. The other Linux boxes, though, continued to be accessible as before.

I thought something might have been glitched in the upgrade, but the new box is a clean install from the 8.04.1 alternate disk, and shows the same problem. What's even more puzzling is that after I installed three VMs on it, to run Win98SE, Win2K, and WinXP (all needed to support my customers), the Windows VMs are able to access the two Win98SE boxes just as before!

The new system is a Pentium 4, 2 GB of RAM, some 500 GB of disk spread across three drives. Mobo is Abit E85 and the NIC is on the mobo. The VMs all run bridged networking, each with its own IP accress and each set up for file sharing with full r-w access.

This certainly looks like a bug somewhere in the 8.04.1 package, most likely in the samba service, but it could also be a problem in samba.conf since I'm currently just using its default. Has anybody else run into a problem like this, or have any suggestions?

---

### Post by spikeb on 2008-11-27
Same issue (errors mounting shares with it) on 8.10 here

---

### Post by JKyleOKC on 2009-01-19
Sorry to be so long in replying; I broke my left leg not long after doing the original post and spent several weeks in hospital and rehab!

I've discovered the cause, I think, and it appears that we're well and truly hosed by the updates to Samba. The old "smbmount" and "smbfs" components have been eliminated, and those words are now simply links to the cifs equivalents -- which for a number of reasons are not capable of recognizing older Windows or OS/2 systems! Running pyNeighborhood in debug mode from the terminal clearly illustrates the reason for failure to mount: the program is unable to locate the specified host, despite having scanned it moments before via smbclient. A Google search for "error 112" which is reported in the debug output brings up several threads about this problem in the mount.cifs and cifs components, which require recompiling the kernel to resolve.

However, all is not lost. While doing the searches I came across another SMB browsing program, called xsmbrowser, that's in the repositories -- and when it's installed, all of my Win98 machines became accessible again. I still cannot mount them, but xsmbrowser allows me to access any specific file, open it with my desired local program, or transfer it to the local machine for additional work -- and these capabilities suffice to meet my needs.

---

