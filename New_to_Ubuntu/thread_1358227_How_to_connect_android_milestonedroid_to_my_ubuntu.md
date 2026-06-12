---
title: "How to connect android milestone/droid to my ubuntu 8.04 pc?"
date: 2009-12-18
forum: New to Ubuntu
---

### Post by kramer65 on 2009-12-18
Hello,

I just got my new motorola milestone (called droid for people from the US) and I wanted to put some music on it. When I connect it to my pc however, I don't get anything. Ubuntu doesn't show any sign of recognition, and my phone also doens't show any sign that it is connected to anything.

Does anybody have any tip?

---

### Post by treesurf on 2009-12-18
I don't have a Droid, but my HTC Hero also runs Android.  With my phone I have to put it into USB mode so that the PC can mount it as a drive.  On the Hero a little icon pops up in the notification area asking if I want to do this whenever I plug it into a USB port.  

Check the manual of your Droid.  I'm sure it's a similar process.  As far as I know, any mobile device running Android should be able to mount as a generic mass USB storage device.  You could also just try looking through the settings menus on your phone.  There should be something there about USB management.

---

### Post by kramer65 on 2009-12-18
:confused: I just tried again, and now it worked.. strrrange. Thanks a lot anyway..

One more question. I just want to put music in the music player. I see that the datacard in it now contains all sorts of things; backup, data, dcim, LOST.DIR, Motonav, an two files named device.nng and tfc.pn.

Can I simply add a folder named "music" and put music in it?

---

### Post by kimberlite on 2009-12-18
Not the proper way, but could work:

put out the microSD card and insert it to your cardreader/notebook...

---

### Post by gregh on 2009-12-20
I have just got my milestone and also have this issue. When tailing the /var/log/messages it appears to try to connect as a mass storage device, but fails with the message:
Dec 21 07:23:35 jscgxh kernel: [ 1059.674498] scsi 7:0:0:0: Direct-Access     Motorola A853             0001 PQ: 0 ANSI: 2
Dec 21 07:23:35 jscgxh kernel: [ 1059.674965] sd 7:0:0:0: Attached scsi generic sg2 type 0
Dec 21 07:23:35 jscgxh kernel: [ 1059.688998] sd 7:0:0:0: [sdb] 15523840 512-byte logical blocks: (7.94 GB/7.40 GiB)
Dec 21 07:23:35 jscgxh kernel: [ 1059.689858] sd 7:0:0:0: [sdb] Write Protect is off
Dec 21 07:23:46 jscgxh kernel: [ 1070.088024] usb 1-4: reset high speed USB device using ehci_hcd and address 9
Dec 21 07:23:46 jscgxh kernel: [ 1070.656018] usb 1-4: reset high speed USB device using ehci_hcd and address 9
Dec 21 07:23:50 jscgxh kernel: [ 1074.160291]  sdb:
Dec 21 07:23:50 jscgxh kernel: [ 1074.160403] Dev sdb: unable to read RDB block 0
Dec 21 07:23:50 jscgxh kernel: [ 1074.160458]  unable to read partition table
Dec 21 07:24:01 jscgxh kernel: [ 1085.038680] usb 1-4: USB disconnect, address 9
Dec 21 07:24:01 jscgxh kernel: [ 1085.038910] sd 7:0:0:0: [sdb] Write Protect is on
Dec 21 07:24:01 jscgxh kernel: [ 1085.038926] sd 7:0:0:0: [sdb] Attached SCSI removable disk
Dec 21 07:24:01 jscgxh kernel: [ 1085.038948] sd 7:0:0:0: [sdb] READ CAPACITY failed
Dec 21 07:24:01 jscgxh kernel: [ 1085.038953] sd 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Dec 21 07:24:01 jscgxh kernel: [ 1085.038957] sd 7:0:0:0: [sdb] Sense not available.
Dec 21 07:24:01 jscgxh kernel: [ 1085.039063] sd 7:0:0:0: [sdb] READ CAPACITY failed
Dec 21 07:24:01 jscgxh kernel: [ 1085.039065] sd 7:0:0:0: [sdb] Result: hostbyte=DID_NO_CONNECT driverbyte=DRIVER_OK
Dec 21 07:24:01 jscgxh kernel: [ 1085.039068] sd 7:0:0:0: [sdb] Sense not available.


seems to be an issue with the way the microSD is formatted ?
I will post any other findings here.

-G

---

### Post by baltadt on 2009-12-20
> **kramer65 said:**
> :confused: I just tried again, and now it worked.. strrrange. Thanks a lot anyway..

One more question. I just want to put music in the music player. I see that the datacard in it now contains all sorts of things; backup, data, dcim, LOST.DIR, Motonav, an two files named device.nng and tfc.pn.

Can I simply add a folder named "music" and put music in it?

That's what I did with my Mytouch and it works fine.

---

### Post by jason10 on 2009-12-30
i just got a droid and when i plug it in ubuntu does nothing but the droid usb shows up in the phone menu.  just drag the notification thing on the droid down and click "select to copy files to/from your computer".  after that it mounts just fine.  for some reason it took me a couple minutes to figure that out..  
(9.10 karmic)

---

