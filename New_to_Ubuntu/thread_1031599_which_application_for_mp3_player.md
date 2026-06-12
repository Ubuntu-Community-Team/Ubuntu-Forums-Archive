---
title: "which application for mp3 player?"
date: 2009-01-05
forum: New to Ubuntu
---

### Post by sanderella on 2009-01-05
Sorry to ask such a stupid question. Which application should I use to download music from my Ubuntu computer to my mp3 player? :confused:

---

### Post by HotShotDJ on 2009-01-05
That would entirely depend upon your mp3 player.  If you're lucky, when you plug it in via the USB port, it will be recognized by your computer automatically.  Let us know what model mp3 player you have and we will be better equipped to help you.

---

### Post by sanderella on 2009-01-05
Thank you. It's an old one. The writing says: Creative MuVo 64MB. Creative Labs Model DAP-TD0001 made in china. And when I plug it in, Ubuntu doesn't recognise it.

---

### Post by Paqman on 2009-01-05
> **sanderella said:**
> Thank you. It's an old one. The writing says: Creative MuVo 64MB. Creative Labs Model DAP-TD0001 made in china. And when I plug it in, Ubuntu doesn't recognise it.

Do you know if it's an MTP device?

I have a Creative Zen, which is definitely MTP. I use Amarok to transfer music onto it. Alternatively, you can try Gnomad2. It's a bit more basic, but has the advantage of requiring absolutely no setup.

---

### Post by sanderella on 2009-01-05
I don't know if its an MTP device, but I'll try those applications, thanks.

---

### Post by HotShotDJ on 2009-01-05
Ok... I did a little research.  Check out this page and see if it applies to you:  [http://linux.highsphere.net/howtos/muvo.php](http://linux.highsphere.net/howtos/muvo.php)

---

### Post by halitech on 2009-01-05
with the device not plugged in, open a terminal and run
```
lsusb
```
then plug in the mp3 player, wait a minute and run the same command and post the output here

---

### Post by sanderella on 2009-01-06
sandra@sandra-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04d9:0420 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
sandra@sandra-laptop:~$ lsusb
Bus 005 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 004: ID 04d9:0420 Holtek Semiconductor, Inc. 
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 001 Device 002: ID 041e:4106 Creative Technology, Ltd Nomad MuVo
Bus 001 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


I just found another number on the device; NH00144024003058.

---

### Post by halitech on 2009-01-06
ok, so the device is 
[color="red"]Bus 001 Device 002: ID 041e:4106 Creative Technology, Ltd Nomad MuVo[/color]

in the terminal, post the output of
```
sudo fdisk -l
```

---

### Post by sanderella on 2009-01-06
Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         611     4907826   83  Linux
/dev/sda2             612        4864    34162222+   5  Extended
/dev/sda5            4775        4864      722893+  82  Linux swap / Solaris
/dev/sda6             612        4597    32017482   83  Linux
/dev/sda7            4598        4774     1421721   82  Linux swap / Solaris

Partition table entries are not in disk order

Thank you.

---

### Post by sanderella on 2009-01-06
I tried Amorak and Gnomad2, but neither of them recognise my mp3 player.

---

### Post by halitech on 2009-01-07
> **sanderella said:**
> Disk /dev/sda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd0f4738c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         611     4907826   83  Linux
/dev/sda2             612        4864    34162222+   5  Extended
/dev/sda5            4775        4864      722893+  82  Linux swap / Solaris
/dev/sda6             612        4597    32017482   83  Linux
/dev/sda7            4598        4774     1421721   82  Linux swap / Solaris

Partition table entries are not in disk order

Thank you.

> **sanderella said:**
> I tried Amorak and Gnomad2, but neither of them recognise my mp3 player.


not surprising as ubuntu does not see the mp3 player as connected to the computer. Just out of curiousity, is there a reason why you have 2 swap partitions?

---

### Post by sanderella on 2009-01-07
*not surprising as ubuntu does not see the mp3 player as connected to the computer*

Is there anything I can do about it?

[I]Just out of curiousity, is there a reason why you have 2 swap partitions?
[/I]
Probably because I installed an extra RAM card.

:confused:

---

### Post by halitech on 2009-01-07
I'm not familiar with your mp3 player, did you check out the link someone posted earlier?

swap partitions and ram are not the same. swap partitions are physical partitions on your hard drive that linux can use if ram is full and would need to be setup in order to exist

---

### Post by sanderella on 2009-01-07
Thanks for all your help. I'm giving up on this one. :(

I really need a new mp3 player, I guess.

---

### Post by halitech on 2009-01-07
did some checking and it looks like there is a firmware upgrade that others had to get before it would work under linux. 

[http://support.creative.com/Products/ProductDetails.aspx?catID=213&subCatID=215&prodID=110&prodName=MuVo&subCatName=MuVo&CatName=MP3+Players](http://support.creative.com/Products/ProductDetails.aspx?catID=213&subCatID=215&prodID=110&prodName=MuVo&subCatName=MuVo&CatName=MP3+Players)

---

### Post by sanderella on 2009-01-08
The download is for Windows only. Is there anything I can do. I'm not a geek, just a little old lady who loves ubuntu, but doesn't know much. Thanks.

---

### Post by Junkieman on 2009-01-08
Hello all. After doing some digging, i came across [this Launchpad dicussion]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/240211") with other muvo users who also can't see their mp3 players after connecting, however the discussion hasn't reached a conclusion yet.

Furthermore, I found [this article]("http://linux.highsphere.net/howtos/muvo.php") that details that the muvo actually is detected as a scsi device, and can be mounted using the instruction given in that article.

The procedure is a little bit techie-fied, and im not at my Ubuntu pc right now to double-check the commands i would ask you to enter, sanderella.

Can anyone else use any of these links, maybe we can get the muvo working... :)

---

### Post by sanderella on 2009-01-15
Thank you Junkieman and all others who tried to help. 

(No thanks buttons found today!)

---

### Post by hyper_ch on 2009-01-15
with regard of that webpage, open a terminal and try this:

(1) create mount point
```

sudo mkdir /media/muvo

```

(2) then run
```

sudo mount -t vfat /devices/scsi/host0/bus0/target0/lun0/part1 /media/muvo/

```

Post the output here.

---

### Post by sanderella on 2009-01-17
mount: special device /devices/scsi/host0/bus0/target0/lun0/part1 does not exist

---

### Post by Junkieman on 2009-01-22
@hyper thanks for those :)

@sanderalla maybe your mp3 player points to a different mount point. if you feel brave and delve into some more techy commands, we can find your mp3 player details using the **dmesg** command. 

When you connect a USB device to your pc, the system logs details about that device. Right after connecting your player, open a terminal and enter this command:

```
dmesg
```

you should see those log files, but the lines you are looking for mention "Muvo", similiar to this

```
Nov 16 00:12:19 poppy kernel: scsi0 : SCSI emulation for USB Mass Storage devices
Nov 16 00:12:19 poppy kernel: Vendor: CREATIVE Model: **NOMAD_MUVO** Rev: 0001
Nov 16 00:12:19 poppy kernel: Type: Direct-Access ANSI SCSI revision: 02
Nov 16 00:12:19 poppy kernel: Attached scsi removable disk sda at scsi0, channel 0, id 0, lun 0
Nov 16 00:12:19 poppy kernel: SCSI device sda: 256001 512-byte hdwr sectors (131 MB)
Nov 16 00:12:19 poppy kernel: sda: Write Protect is off
Nov 16 00:12:19 poppy kernel: /dev/scsi/host0/bus0/target0/lun0: p1
```

using your mouse to highlight those few lines in your terminal window, and copy/paste them here. :)

---

