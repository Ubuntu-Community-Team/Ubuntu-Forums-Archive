---
title: "unable to mount iPod Touch for gtkpod use!! Please help!!"
date: 2010-03-09
forum: New to Ubuntu
---

### Post by surajpkn on 2010-03-09
Hello,

I am an absolute beginner and I am having issues with mounting my ipod touch with my ubuntu 9.10 for GTKPOD use. Here are the details

1. When I plug in my ipod touch, I get a message saying that ubuntu has found a device with digital photos and asks if i want to open it with "f-spot".  ( I usually choose to do nothing)

2. I can see my ipod's icon on the desktop with an icon of that of a "digital camera".

3. I don't know where this ipod is now mounted. when i right click the desktop icon and go to properties, I am not able to find anything that says where my device is mounted.

The question is: How do i mount this ipod to /media/ipod so that my gtkpod can access it?

Please note: 
1. I dont know where this ipod is mounted.
2. I installed gtkpod by following the instructions from here
      [http://ubuntuforums.org/showthread.php?t=36632](http://ubuntuforums.org/showthread.php?t=36632)
3. Everytime i try "mount /dev/sdc2 /media/ipod" i get error saying there is nothing like /dev/sdc2. This is the same error i got for sdb2 also. (I dont even know how this sda,sdb and sdc works)
4. This is the output of my dmesg | tail command
[   18.884387] tg3: eth0: Link is up at 100 Mbps, full duplex.
[   18.884389] tg3: eth0: Flow control is on for TX and on for RX.
[   18.884550] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   20.890915] hda-intel: IRQ timing workaround is activated for card #1. Suggest a bigger bdl_pos_adj.
[   28.639906] Bluetooth: HIDP (Human Interface Emulation) ver 1.2
[   29.061010] eth0: no IPv6 routers present
[   29.197490] input: Dell BT Travel Mouse as /devices/pci0000:00/0000:00:1a.0/usb3/3-1/3-1.3/3-1.3:1.0/bluetooth/hci0/hci0:11/input16
[   29.197574] generic-bluetooth 0005:046D:B006.0003: input,hidraw1: BLUETOOTH HID v1.24 Mouse [Dell BT Travel Mouse] on 00:24:2C:B6:59:BB
[   35.027352] process `skype' is using obsolete setsockopt SO_BSDCOMPAT
[   54.325065] CE: hpet increasing min_delta_ns to 15000 nsec

5. This is the output of my mount command
/dev/sda1 on / type ext4 (rw,errors=remount-ro)
proc on /proc type proc (rw)
none on /sys type sysfs (rw,noexec,nosuid,nodev)
none on /sys/fs/fuse/connections type fusectl (rw)
none on /sys/kernel/debug type debugfs (rw)
none on /sys/kernel/security type securityfs (rw)
udev on /dev type tmpfs (rw,mode=0755)
none on /dev/pts type devpts (rw,noexec,nosuid,gid=5,mode=0620)
none on /dev/shm type tmpfs (rw,nosuid,nodev)
none on /var/run type tmpfs (rw,nosuid,mode=0755)
none on /var/lock type tmpfs (rw,noexec,nosuid,nodev)
none on /lib/init/rw type tmpfs (rw,nosuid,mode=0755)
/dev/sda6 on /home type ext4 (rw)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw,noexec,nosuid,nodev)
gvfs-fuse-daemon on /home/suraj/.gvfs type fuse.gvfs-fuse-daemon (rw,nosuid,nodev,user=suraj)

Please tell me what I am missing here and what I should do.
Thanks
Suraj

---

### Post by surajpkn on 2010-03-09
Also another point
I have tried searching almost every thread in this forum and other forums to find similar problems and solutions or finding out approaches on how to use gtkpod etc etc. 
I have achieved nothing with the so many hundreds of threads and links that i saw.
So I don't know how helpful it would be to ask me to view another thread and see if I find a solution there. I have tried a lot of them. Nothing is specific to my case.
!!

---

### Post by Paul Lynch on 2010-03-18
Hi,
I had a similar problem. After looking through these threads for a solution I eventually solved my problem quit simply by resetting my IPOD (hold down the center and play buttons for 8 seconds, google your ipod for specific info). With the ipod reset everything worked 100% in GTKPOD. The ipod automatticaly mounts and gtkpod works fine.
Hope this helps....

---

### Post by franzejr on 2010-12-23
I have the same problem.

Someone can help us ?

Thanks

---

### Post by Chronon on 2010-12-24
The iPod Touch does not have an MSC mode, so you can't mount it as a UMS device.  I think you can view the phone's file system using ifuse.  For more info see the community help page:
[https://help.ubuntu.com/community/PortableDevices/iPhone](https://help.ubuntu.com/community/PortableDevices/iPhone)

---

### Post by z987k on 2010-12-25
I have the same problem as well.  Just shows up as a camera and gtkpod nor rythmbox can see it or transfer anything.

Firmware 4.2 on the touch.

---

### Post by pmooney78 on 2012-10-22
I know that this is an old thread, but if anyone's still looking for this information, I've recently noticed that recent versions of Ubuntu create a "real" mount somewhere under ~/.gvfs -- so, for me, I can find the "real" mount at "~/.gvfs/Patrick's iPod." 

I stumbled across this when trying to figure out how to scrobble my iPod Touch with the last.fm client software.

---

### Post by wildmanne39 on 2012-10-22
Thanks for sharing and please do not post in threads that have not had activity for a year or longer, since this is an old thread it has been closed.

---

