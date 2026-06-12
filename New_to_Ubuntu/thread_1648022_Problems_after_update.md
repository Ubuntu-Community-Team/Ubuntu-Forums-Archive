---
title: "Problems after update"
date: 2010-12-18
forum: New to Ubuntu
---

### Post by dawner on 2010-12-18
Hello everyone. 

I experienced some problems after last update(friday morning). Problem is that GNOME started to act weird, one of my partitions is not found and cannot access trash. First of all, everytime I want to start some apps from panels or menu Gnome refreshes itself(I do not know how to say it ). Second thing my data partition disappered. In fdisk it is mounted but I cannot access it. 
There is something I found out, I do not know if it has connection to my problems,but whenever I start any app from shell something like this is printed

(gedit:7391): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so) initialization check failed: GLib version too old (micro mismatch)

(gedit:7391): Gtk-WARNING **: Loading IM context type 'ibus' failed

(gedit:7391): Gtk-WARNING **: GModule (/usr/lib/gtk-2.0/2.10.0/immodules/im-ibus.so) initialization check failed: GLib version too old (micro mismatch)

(gedit:7391): Gtk-WARNING **: Loading IM context type 'ibus' failed


Any suggestions what could be wrong?

Michal

---

### Post by sanderd17 on 2010-12-18
Those GTK warnings have nothing to do with it.

I don't have an answer to your problems though.

---

### Post by carverj on 2010-12-18
So you think these issues are all related to update or have other changes taken place? 
 killall gnome-panel nautilus command allows you to reload gnome desktop.
 /var/log contains system logs that may be of use to troubleshoot.
And you say partition is not found? Where are you looking?
/dev gives a list of devices, such as /dev/sdb1 is ubuntu, /dev/sdb2 is swap
Gparted gives a graphical view of this.

---

### Post by dawner on 2010-12-18
So, when I execute this command killall gnome-panel nautilus  it looks very similar to my problem with UI. Basically whenever I want to perform any UI operation(open folder, any panel options) this will happen. 

And to partition:
I used fdisk -l to check if all are available

Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x2e723621

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1148     9216000   27  Unknown
/dev/sda2   *        1148       13440    98733056    7  HPFS/NTFS
/dev/sda3           13440       33750   163142789+   7  HPFS/NTFS
/dev/sda4           33751       38913    41471797+   5  Extended
/dev/sda5           33751       38696    39728713+  83  Linux
/dev/sda6           38697       38913     1743021   82  Linux swap / Solaris


I am running dual boot for 6 months now,so it should not be problem. sda3 is Data Partition which I cannot access

---

