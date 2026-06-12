---
title: "Can't Mount Sd card"
date: 2008-12-13
forum: New to Ubuntu
---

### Post by Ericthegreat on 2008-12-13
It was mounting as read only and im sure the switch is ok so i checked around a bit and it seemed to be a bug and you needed to mount with -o rw but im really stupid and i put that in the mount options so now it says Cannot Mount: Invalid Mount options >.< so what should i do tyvm in advance (and if you could try and tell me how to bypass the read only bug thing)

---

### Post by cdtech on 2008-12-13
SD cards are auto mounted as media devices using the "Hardware abstraction layer" (hal). If the device is not auto mounted when pluged in then you may have other issues. With the card pluged in, what do you get on a command line using:
```
df -h | grep mmc
```

---

### Post by Ericthegreat on 2008-12-13
Nothing:  

eric@Chad:~$ df -h | grep mmc
eric@Chad:~$ df -h | grep mmc
eric@Chad:~$ sudo df -h | grep mmc
[sudo] password for eric: 
eric@Chad

The card works fine in everything but Ubuntu.

---

### Post by Ericthegreat on 2008-12-13
Using Storage Device Manager i got it to mount but still has the read only error

---

### Post by cdtech on 2008-12-13
What do you get when you type:
```
sudo /etc/init.d/hal restart
```

---

### Post by Ericthegreat on 2008-12-13
eric@Chad:~$ sudo /etc/init.d/hal restart
 * Restarting Hardware abstraction layer hald                            [ OK ] 
eric@Chad:~$

---

### Post by cdtech on 2008-12-13
> **Ericthegreat said:**
> Using Storage Device Manager i got it to mount but still has the read only error

I would umount the device from the way you have it mounted and start by simply pluging it in then check the device by using the command above and try to reset the hald. Do you have any other SD media devices? Do you have any other issues with pluging other devices in?

---

### Post by Ericthegreat on 2008-12-13
USB storage works fine seems just SD cards have the issue

---

### Post by Ericthegreat on 2008-12-13
Seems it is sdb1 so is there a command to force write?

---

### Post by Ericthegreat on 2008-12-13
Ah if anyone can understand this please Do:

eric@Chad:~$ tail -f /var/log/syslog
Dec 13 16:01:05 Chad kernel: [ 1635.187631]  sdb: sdb1
Dec 13 16:01:05 Chad hald: mounted /dev/sdb1 on behalf of uid 1000
Dec 13 16:02:11 Chad hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 1000
Dec 13 16:02:19 Chad hald: mounted /dev/sdb1 on behalf of uid 1000
Dec 13 16:04:09 Chad kernel: [ 1686.986873] ioctl32(gnome-terminal:6588): Unknown cmd fd(26) cmd(0000530b){t:'S';sz:0} arg(0fce0588) on /dev/pts/0
Dec 13 16:04:09 Chad kernel: [ 1686.986903] ioctl32(gnome-terminal:6588): Unknown cmd fd(26) cmd(0000530b){t:'S';sz:0} arg(0fce0590) on /dev/pts/0
Dec 13 16:04:09 Chad kernel: [ 1686.986923] ioctl32(gnome-terminal:6588): Unknown cmd fd(26) cmd(0000530b){t:'S';sz:0} arg(0fce0598) on /dev/pts/0
Dec 13 16:04:40 Chad NetworkManager: <info>  HAL disappeared 
Dec 13 16:04:43 Chad NetworkManager: <info>  HAL re-appeared 
Dec 13 16:08:48 Chad hald: unmounted /dev/sdb1 from '/media/disk' on behalf of uid 1000
Dec 13 16:09:20 Chad kernel: [ 1769.485824] sd 1:0:0:1: [sdb] 1984000 512-byte hardware sectors (1016 MB)
Dec 13 16:09:20 Chad kernel: [ 1769.487971] sd 1:0:0:1: [sdb] Write Protect is on
Dec 13 16:09:20 Chad kernel: [ 1769.487986] sd 1:0:0:1: [sdb] Mode Sense: 00 06 00 80
Dec 13 16:09:20 Chad kernel: [ 1769.487994] sd 1:0:0:1: [sdb] Assuming drive cache: write through
Dec 13 16:09:20 Chad kernel: [ 1769.490326] sd 1:0:0:1: [sdb] 1984000 512-byte hardware sectors (1016 MB)
Dec 13 16:09:20 Chad kernel: [ 1769.492080] sd 1:0:0:1: [sdb] Write Protect is on
Dec 13 16:09:20 Chad kernel: [ 1769.492093] sd 1:0:0:1: [sdb] Mode Sense: 00 06 00 80
Dec 13 16:09:20 Chad kernel: [ 1769.492101] sd 1:0:0:1: [sdb] Assuming drive cache: write through
Dec 13 16:09:20 Chad kernel: [ 1769.492120]  sdb: sdb1
Dec 13 16:09:20 Chad hald: mounted /dev/sdb1 on behalf of uid 1000

---

### Post by cdtech on 2008-12-13
Check your "dmesg" once you plug the device in and see if it recognizes it and see if you have the module installed for the SD reader.
```
lsmod | grep sd
```

---

### Post by cdtech on 2008-12-13
Be sure you don't have the write protect tab pushed in the wrong direction on the SD card.....

---

### Post by Ericthegreat on 2008-12-13
eric@Chad:~$ lsmod | grep sd
sd_mod                 44344  2 
scsi_mod              241688  5 sd_mod,usb_storage,sg,sr_mod,ps3rom
eric@Chad:~$ 

And ive checked the tab

---

### Post by Ericthegreat on 2008-12-16
Btw this was solved i put tape on the tab now it works >.<, Seems that when i was putting it in the card reader would push the tab down then when i would take it out it would pull it back up,  H ow i figured this out was when i put it in with read only it would still come out Read/Write. Sorry to waste everyones time :(

---

### Post by doobiest on 2008-12-16
Ya what are the odds that the physical lock on the side of the sd card is on.  I have one sd card that has a loose lock and always goes write protect by accident.

I'd be wondering 3 things:

1) Check the physical lock (I believe this is what ericthegreat is getting at as his example has write protect enabled)
2) Check permissions.  An easy way to do this is to browse to the sd card in a terminal (cd /media/disk or whatever)  then do a 'sudo touch test' and see if a file named test get's written to the card.
3) Very unlikely but when an SD card has seen better days and reached it's end of life you will no longer be able to write to some if not all sectors/cells on the card, that's just they way she goes, they do have a limited write capacity

---

### Post by doobiest on 2008-12-16
> **Ericthegreat said:**
> Btw this was solved i put tape on the tab now it works >.<, Seems that when i was putting it in the card reader would push the tab down then when i would take it out it would pull it back up,  H ow i figured this out was when i put it in with read only it would still come out Read/Write. Sorry to waste everyones time :(

HAHAHA of course you write that in the middle of me replying.  Glad it worked.

---

