---
title: "External USB (NTFS) drive not recognised"
date: 2010-04-01
forum: New to Ubuntu
---

### Post by johnfrith on 2010-04-01
Any ideas why my external NTFS USB drive should not be recognised?

fdisk -l  doesn't give any output

Nothing new shows under "Places"

Places > Network > Windows Network gives message "Unable to mount location - unable to retrieve share list from server"


"...for now I am bent to know
By the worst means the worst. For mine own good
All causes shall give way. I am in blood
Steeped so far that, should I wade no more,
Returning were as tedious as go o'er." ( Macbeth 3.4.137, W. Shakespeare) d:¬)=

---

### Post by halitech on 2010-04-01
unless its connected to a windows computer and being shared it shouldn't show up under Network - Windows Network

Was the drive last connected to a windows computer?

---

### Post by johnfrith on 2010-04-01
Hi Halitec,

I'm trying to transfer files from my old (Windows) laptop to my new (Ubuntu) laptop, so the drive was written to, and has last been used, under windows. It's not connected to the Windows machine while I'm trying to connect to Ubuntu machine, (though I've tried it whilst connected to both). 

The drive spins up ok, powered through the USB connection.

I only mentioned the Network Places think in case it was useful, I can't say I really know what I'm doing!

TIA. John

---

### Post by readycarpenter on 2010-04-01
I assume you are plugging the usb drive into the ubuntu pc, and it is not being recognized, 

in ubuntu, ntfs drives will not automatically mount if they were improperly removed from the last machine it was plugged into, (but windows will)

so either plug into a windows machine, then use "safely remove hardware"
or use force mount in ubuntu

```
sudo mkdir /media/usb-drive
sudo mount /dev/(yourdevice) /media/usb-drive -o force
```

hope this is what you were going for
cheers

---

### Post by halitech on 2010-04-01
ok, so it was last used on windows. is it win XP, 2000, 98, etc? when you removed it from the windows computer, did you use the safely eject method or did you simply unplug it?

---

### Post by johnfrith on 2010-04-01
Thanks readycarpenter, halitec.

> **readycarpenter said:**
> I assume you are plugging the usb drive into the ubuntu pc, and it is not being recognized, 

Yes

> **readycarpenter said:**
> in ubuntu, ntfs drives will not automatically mount if they were improperly removed from the last machine it was plugged into, (but windows will) so either plug into a windows machine, then use "safely remove hardware" or use force mount in ubuntu

I did just unplug it, and I think there was an error (which I just ignored). I'm using Windows XP. I've now connected and removed it in XP using the  "safely remove hardware" option, but it's still not recognised by Ubuntu.

> **readycarpenter said:**
> ```
sudo mkdir /media/usb-drive
sudo mount /dev/(yourdevice) /media/usb-drive -o force
```

Sorry to sound ignorant, but how do I find out what (yourdevice) is? There's a directory in Dev called "dri", could that be it?

Don't know if it's relevant but the drive has a FAT32 partition on it, as well as the NTFS one.

---

### Post by johnfrith on 2010-04-02
bump

---

### Post by kaizokuroof on 2010-04-02
Hey dude try this.
```
sudo mkdir /media/usb-drive
sudo mount /dev/sdb /media/usb-drive -o force
```

or insted of sdb try sdb1

Hope it helps.

Kaizoku roof.

---

### Post by johnfrith on 2010-04-02
Thanks kaizokuroof. Wasn't recognised.

```
john@jf:~$ sudo mount /dev/sdb /media/usb-drive -o force
[sudo] password for john: 
mount: special device /dev/sdb does not exist
john@jf:~$ sudo mount /dev/sdb1 /media/usb-drive -o force
mount: special device /dev/sdb1 does not exist
john@jf:~$ 
```

Anyone have any more ideas? Have been researching online storage as a way round (seems FilesAnywhere is the most suitable), but this external drive is my normal backup medium, so I do need to sort it out. TIA.

Regards, John

---

### Post by kaizokuroof on 2010-04-02
Errrm, Sorry John, still new to Ubuntu. Give this a go It's for mounting HDD but maybe it'll work the same?:

```
sudo fdisk -l
``` to list your drives and there partitions. Look for the one you want.

make a folder to mount it to

```
sudo mkdir /media/windows
```

then mount

```
sudo mount /dev/hda5 /media/windows -t ntfs
```

note: replace /dev/hda5 with what ever fdisk says is your ntfs partition is

Hope this works, if not check the Ubuntu Guide, or wait for someone more capable then me :( Sorry.

---

### Post by johnfrith on 2010-04-02
Thanks kaizokuroof.

fdisk just showed the main disc partitions, so no progress unfortunately. Appreciate you tried though!

Anyone else have any ideas, or do I have to throw the drive away?

---

### Post by srs5694 on 2010-04-02
Try this:


[list=1]
[*]Unplug the drive.
[*]In a console, type "dmesg | tail -20"
[*]Plug the drive in and wait about 10 seconds.
[*]Type "dmesg | tail -20" again and note any additional entries.
[/list]


The "dmesg" command displays messages from the kernel. These will normally include information about devices when they are detected (USB devices plugged in, etc.), including errors. (The "tail -20" command says to display only the last 20 lines of the dmesg output.) Normally when you plug in an external drive, you'll see something. For instance, when I plug in a USB flash drive, this is what I see:

```

[840816.654043] usb 2-4: new high speed USB device using ehci_hcd and address 8
[840816.771300] usb 2-4: configuration #1 chosen from 1 choice
[840816.771713] scsi10 : SCSI emulation for USB Mass Storage devices
[840816.771947] usb-storage: device found at 8
[840816.771949] usb-storage: waiting for device to settle before scanning
[840821.771830] scsi 10:0:0:0: Direct-Access              USB_DRIVE        1.00 PQ: 0 ANSI: 2
[840821.772022] sd 10:0:0:0: Attached scsi generic sg2 type 0
[840821.772358] usb-storage: device scan complete
[840821.774308] sd 10:0:0:0: [sdb] 31576064 512-byte logical blocks: (16.1 GB/15.0 GiB)
[840821.774804] sd 10:0:0:0: [sdb] Write Protect is off
[840821.774807] sd 10:0:0:0: [sdb] Mode Sense: 23 00 00 00
[840821.774809] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[840821.776803] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[840821.776806]  sdb: sdb1
[840824.120221] sd 10:0:0:0: [sdb] Assuming drive cache: write through
[840824.120226] sd 10:0:0:0: [sdb] Attached SCSI removable disk

```

These messages may contain important debugging information. If you see no messages at all, it's possible you've got a bad cable or a bad USB port; or perhaps you're using a USB hub that's incompatible with the drive or your computer. If you do see something, though, peruse it yourself and post it here.

---

### Post by johnfrith on 2010-04-02
Ureka!

Thanks srs5694 for your post. fdisk didn't show any change after connecting the drive so I started to check the cables as you suggested. To cut a long story short, it turned out to be a power issue. A blue light comes on to indicate that the drive is ready, which I assumed meant everything was hunkydory with the drive powered by the USB connection. But it does seem to need a further power supply (in this case a 2nd USB to power did it), for it to be picked up.

Many many thanks to halitech, readycarpenter, kaizokuroof and srs5694, and thanks to the forum for being such a good resource!

__

---

### Post by kaizokuroof on 2010-04-03
No problems, seeing as your problem was fixed, you should mark your thread as solved, that way people can search for solutions easier. :D

WOOPS my bad, should open my eyes. :P Glad your problem was fixed, best of luck with Linux.

---

