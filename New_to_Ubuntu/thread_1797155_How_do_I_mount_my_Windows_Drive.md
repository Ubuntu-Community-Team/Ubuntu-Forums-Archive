---
title: "How do I mount my Windows Drive?"
date: 2011-07-04
forum: New to Ubuntu
---

### Post by greenelf on 2011-07-04
How do I mount my Windows Drive? I've already googled the problem, and nothing seems to work. Please help me!

---

### Post by rosencrantz on 2011-07-04
I take it you want to mount a windows NTFS drive on the same computer?
It should show up in Nautilus->Places and be mountable by clicking on it.
If not, open a terminal and try 
sudo mkdir /media/windrive
sudo mount -t ntfs /dev/sda1 /media/windrive
This assumes Windows is on the first partition of your first hard drive. If not, check the output of ls -l /dev/disk/by-id.
If you want to include the partition permanently into your setup, you can either install and run ntfs-config or edit your fstab file:
sudo gedit /etc/fstab
Create a mount folder like /media/windrive if you haven't already and do sudo gedit /etc/fstab in a terminal. Put in a line like

/dev/sda1  /media/windrive      ntfs    defaults     0       0

---

### Post by wildmanne39 on 2011-07-05
Hi, if you do not see it in your file manager on the left side of the window,then you can open disk utility and see if it is there if it is then mount it. Here is a link for mounting window drives. 
[http://ubuntuforums.org/showthread.php?t=1604251](http://ubuntuforums.org/showthread.php?t=1604251)
[http://www.psychocats.net/ubuntu/mountwindowsfstab](http://www.psychocats.net/ubuntu/mountwindowsfstab)

---

### Post by RoyLongbottom on 2011-07-05
See LAN Benchmarks in:
 
[http://www.roylongbottom.org.uk/linux_disk_usb_lan_benchmarks.htm#anchor2](http://www.roylongbottom.org.uk/linux_disk_usb_lan_benchmarks.htm#anchor2)
 
 
Roy

---

### Post by Mark Phelps on 2011-07-05
Be careful in doing this.  If the Windows version is Win7, you mount the OS partition read-write, and you WRITE to it -- you run the risk of corrupting the filesystem and rendering Win7 unbootable.

So, if your PC has an optical drive, BEFORE you do this mount, use the Backup feature in Win7 to create and burn a Win7 Repair CD.  At least this way, if it DOES get corrupted, you can boot from this CD and repair it.

---

