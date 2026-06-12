---
title: "Samsung cellphone not mounting in mass file transfer mode"
date: 2009-03-25
forum: New to Ubuntu
---

### Post by humphreybc on 2009-03-25
Hi there so my Samsung cellphone used to mount fine with Ubuntu by connecting it to the computer and then going to Tools > User Memory > Connect PC and it would show up as a USB drive, and pop up in Nautilus.

Now for some reason it is still showing up but giving me this error:

> 
Unable to mount location

Can't mount file


Any ideas?

---

### Post by CRCarl on 2009-03-25
Can you disconnect the phone then run
```
lsusb
```

Then open up another terminal window and run 
```
tail -f -n 0 /var/log/messages
```

Then plug the phone back in and run ```
lsusb
``` again.

Post the output from both lsusb commands and the messages file here.

---

### Post by humphreybc on 2009-03-25
lsusb - phone disconnected:

```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

lsusb - phone connected
```

Bus 007 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 006 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 005 Device 004: ID 04e8:663b Samsung Electronics Co., Ltd 
Bus 005 Device 003: ID 0458:003a KYE Systems Corp. (Mouse Systems) 
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 002: ID 0483:2016 SGS Thomson Microelectronics Fingerprint Reader
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 04f2:b008 Chicony Electronics Co., Ltd 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```



messages file is attached as it is too long for the post. (Note I just cut out the relevant part of the whole logfile, starting at Mar 25 22:42:15.

Thanks

---

### Post by CRCarl on 2009-03-25
It looks like there is a bug filed on this one - [https://bugs.launchpad.net/ubuntu/+bug/151094]("https://bugs.launchpad.net/ubuntu/+bug/151094"). The bug has been closed, but it looks like what you have. 

Here is an idea from the intertubes - 
Open ```
/etc/udev/rules.d/65-persistent-storage.rules
``` as sudo and comment out the line ```
IMPORT{program}="vol_id --export $tempnode"
```
Plug the phone back in, see if you still get the 
> Mar 25 22:43:00 benjamin-laptop kernel: [17438.326716] sd 7:0:0:0: [sdc] Device not ready: Sense Key : Not Ready [current] 
Mar 25 22:43:00 benjamin-laptop kernel: [17438.326728] sd 7:0:0:0: [sdc] Device not ready: Add. Sense: Medium not present

errors. 
If you do, reboot then continue, otherwise try and mount the device manually - 
```
sudo mkdir /media/samsung
sudo mount -t vfat /dev/sdc1 /media/samsung
sudo chown -R <username>:<username> /media/samsung
ls /media/samsung
touch /media/samsung/test
```

Let us know if that helps.

---

### Post by mikwig on 2009-04-14
thankyou - this worked for me.

---

### Post by mathewd on 2010-02-27
> **CRCarl said:**
> It looks like there is a bug filed on this one - [https://bugs.launchpad.net/ubuntu/+bug/151094](https://bugs.launchpad.net/ubuntu/+bug/151094). The bug has been closed, but it looks like what you have. 

Here is an idea from the intertubes - 
Open ```
/etc/udev/rules.d/65-persistent-storage.rules
``` as sudo and comment out the line ```
IMPORT{program}="vol_id --export $tempnode"
```Plug the phone back in, see if you still get the 

errors. 
If you do, reboot then continue, otherwise try and mount the device manually - 
```
sudo mkdir /media/samsung
sudo mount -t vfat /dev/sdc1 /media/samsung
sudo chown -R <username>:<username> /media/samsung
ls /media/samsung
touch /media/samsung/test
```Let us know if that helps.

I think I have the same issue with my Samsung phone, but within "/etc/udev/rules.d/" I see only "/etc/udev/rules.d/70-persistent-net.rules" and "/etc/udev/rules.d/70-persistent-cd.rules"

Am I meant to edit one of these, or just create the file? Sorry for the newbie question ^_^ btw I'm using Ubuntu 9.10

---

### Post by audiomick on 2010-03-02
@ mathewd
Hi.
I had an issue in this direction with syncing my Nokia E51. The sync is now not working for other reasons, but as far as the rules go, you have to add one to the file
/etc/udev/rules.d```

```look at
```
man udev
```
for information.
Basically, your new rule has to have a higher number at the start than any of the existing ones.

---

