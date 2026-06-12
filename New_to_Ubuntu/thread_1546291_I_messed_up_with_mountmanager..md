---
title: "I messed up with mountmanager."
date: 2010-08-05
forum: New to Ubuntu
---

### Post by Rushyang on 2010-08-05
I installed mountmanager, so that I could auto mount my partitions on boot.

1) I've 5 partitions. When I first started mountmanager, I thought fsck was the priority to set which one first..
2) So I just set fsck=1 in one of my most important partition and fsck=2 in another one.
3) Now, when My system starts up, on the bootscreen, there're 2 errors comes up that unable to mount PC, press s to skip and when I do, there's another same error for another partition.
4) When I come into computer, and try to mount those partitions, the error is shown into attached screenshots.
5) I want to remove those errors, and make all like before. I restored the profile settings by choosing restoration points in mountmanager. But there's no restoration point before what I changed the settings for the first time.

error when I type mountmanager into terminal.. these are the messages...

> 2 records in /etc/fstab were detected.
[G] DBus interface was created
[G] All devices were recieved
[I] Storage device was detected: "/dev/sdb6"
[I] Storage device was detected: "/dev/sr0"
[I] Storage device was detected: "/dev/sdb3"
[I] Storage device was detected: "/dev/sdb5"
[I] Storage device was detected: "/dev/sdb2"
[I] Storage device was detected: "/dev/sdb1"
[I] Storage device was detected: "/dev/sdb"
[I] Storage device was detected: "/dev/sda3"
[I] Storage device was detected: "/dev/sda2"
[I] Storage device was detected: "/dev/sda1"
[I] Storage device was detected: "/dev/sdc1"
[I] Storage device was detected: "/dev/sda"
[I] Storage device was detected: "/dev/sdc"
QInotifyFileSystemWatcherEngine::addPaths: inotify_add_watch failed: No such file or directory
QFileSystemWatcher: failed to add paths: /home/rushyang/.config/ibus/bus
Bus::open: Can not get ibus-daemon's address.
IBusInputContext::createInputContext: no connection to ibus-daemon
[G] Parsing of  "/usr/share/mountmanager/options/common.xml"  was successful
[G] Parsing of  "/usr/share/mountmanager/options/vfat.xml"  was successful
[G] Parsing of  "/usr/share/mountmanager/options/ntfs-3g.xml"  was successful
[G] Parsing of  "/usr/share/mountmanager/options/iso9660.xml"  was successful
[G] Parsing of  "/usr/share/mountmanager/options/udf.xml"  was successful
Please help.. It's urgent. :(

---

