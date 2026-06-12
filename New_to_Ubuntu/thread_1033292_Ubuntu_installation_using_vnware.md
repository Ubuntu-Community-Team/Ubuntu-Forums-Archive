---
title: "Ubuntu installation using vnware"
date: 2009-01-07
forum: New to Ubuntu
---

### Post by nshailesh on 2009-01-07
I want to install ubuntu on windows xp using vmware server.
I have created a separate 8 gb drive(partition) for this installation.
So what do I need to do in order to access the other drives on my computer(C,D,E etc) that 
belong to windows but not to the ubuntu i.e. the drives other than the ubuntu installation drive.Do I need to disable windows firewall?
Also what needs to be done so that ubuntu option appears on the boot screen so that I can choose windows or ubuntu when I start my PC.

---

### Post by mapes12 on 2009-01-07
Not sure if this is what you want but here's a HowTo using VirtualBox: [http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)

---

### Post by cwsnyder on 2009-01-07
I think you are confusing methods of installing Ubuntu.

WUBI installs Ubuntu under Windows, shares the Windows NTFS file partition, and has an entry in the Windows boot.ini to allow for booting under Windows or booting under Ubuntu.  The WUBI install allows you to remove Ubuntu using Windows Install/Remove programs methods.  WUBI will also crash when Windows crashes.  However, while WUBI is running, you are running full Ubuntu, not a virtual machine (like the Live CD version, only able to save your modifications), and you cannot switch back to Windows.  From WUBI, you can find your Windows drive C: information under /host folder.  Drive D:, E:, etc. have to be mounted, as you would under any Ubuntu.  Windows cannot normally access the Linux drive area, and the space set aside during installation is normally fixed in size.

Dual-boot Windows/Ubuntu, you have separate partitions of Windows and Ubuntu, selected while booting, usually from a GRUB menu.  The operating systems do not interact at all unless you either mount the Windows partition under Ubuntu, or install an EXT3 file driver under Windows.  Allocation of space on the drive depends on drive partitioning.

The Live CD version you have probably experimented with, where you boot from the CD, can mount and modify the Windows drive, but cannot normally save your Ubuntu configuration.  There is no space allocated on your drive for Linux.

Finally, VMWare Server/Workstation/etc. installs a virtual machine in a directory under Windows which is not normally accessible data-wise from Windows.  VMWare sets aside a fixed space for your Linux install, and your Linux can access your host operating system using the provided VMWare tools, only.

In all cases, the Ubuntu install communicates with the host as part of the system, not as an external computer.  In the case of the VMWare install, Windows does communicate with the Ubuntu virtual machine as if it was an external computer, however.

I hope this clears things up instead of making things more confusing.

---

