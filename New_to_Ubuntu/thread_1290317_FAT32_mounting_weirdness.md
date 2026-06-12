---
title: "FAT32 mounting weirdness"
date: 2009-10-13
forum: New to Ubuntu
---

### Post by Ndyanabo on 2009-10-13
I just pulled two IDE drives from an old Windows ME box.

First drive: I plugged it into a USB - SATA/IDE adapter (one of those unenclosed things), fired it up. Mounted automatically in Ubuntu. Conclusion: my adapter is working fine.

Second drive was the primary system disk for the old computer. Plug it in, fire it up. No mount. **sudo fdisk -l **, **sudo lshw -C disk** and also Gparted can't see it.

I put it back into the old box and started it. It boots up fine, which shows that the drive is working. I didn't have a mouse handy and I don't know what sort of diagnostic to do in Windows ME anyway, but I could open a few files. I have to assume that it's FAT 32, since that was the standard for ME. So, I shut down the computer properly and tried the drive again in Ubuntu. Again, nothing.

any ideas?

---

### Post by gali98 on 2009-10-13
Perhaps the drive is too old to work with the adapter and/or the adapter does not support FAT32. What adapter do you have? (model/brand.)
Kory

---

### Post by the.phantom on 2009-10-13
did you check jumpers on the hard drive? ( master/slave)

in me double click my computer and then right click that drive, then tools, error checking ( if you can boot it up in me)

---

### Post by lavinog on 2009-10-13
+1 on checking the jumpers.  Some computers have the drives set for "cable select" where a notch in the ide cable determines the master/slave status.

---

### Post by az on 2009-10-13
> **Ndyanabo said:**
> So, I shut down the computer properly and tried the drive again in Ubuntu. Again, nothing.

any ideas?

Run

tail -f /var/log/messages

and then plug in the drive.

Wait a minute and then cut, copy and post the results here.

---

### Post by Ndyanabo on 2009-10-13
not sure what to do with the jumpers, since there isnt a key. It's a Maxtor. 

Looks like this, if anyone is familiar with 8 year old maxtors. Bold is where jumper is : : **:** . :

My adapter is a Vantec. Not sure of the model. Perhaps the disk is too old, but I did establish that it does work with IDE, since I pulled a second drive.

az, I'll run that now. thanks

---

### Post by lavinog on 2009-10-13
> **Ndyanabo said:**
> 
Looks like this, if anyone is familiar with 8 year old maxtors. Bold is where jumper is : : **:** . :


looks like it is setup as a slave
[img]http://www.seagate.com/staticfiles/images/support/en/us/mxo_ata_jumpers_rev.jpg[/img]

---

### Post by Ndyanabo on 2009-10-13
az, that command is hanging. Should it take a while?

edit: OK, realized that I have to plug in after I run the command. duh.

lavinog. thanks a lot. the jumper position isn't actually listed, so that's odd. 

EDIT: wait, misread the key. Looks like I have slave wiht CLJ, although I don't have the second, horizontal jumper as in that image, but it looks like that's doesn't matter, since there's no pin, right?

Should I put it into master?

---

### Post by Mark Phelps on 2009-10-13
When you plugin the drive via USB, it's a completely connection -- master/slave don't apply anymore.  

Just remove the jumper and it should work fine.  You only need the master/slave jumpers set when (1) you're connecting multiple drives, and (2) you're connecting through an IDE controller.

---

### Post by az on 2009-10-13
> **Ndyanabo said:**
> az, that command is hanging. Should it take a while?

Well, it should display what the kernel is seeing when you plug in the drive.  It is seeing nothing.


> **Ndyanabo said:**
> 
lavinog. thanks a lot. the jumper position isn't actually listed, so that's odd. 

EDIT: wait, misread the key. Looks like I have slave wiht CLJ, although I don't have the second, horizontal jumper as in that image, but it looks like that's doesn't matter, since there's no pin, right?

Should I put it into master?

Yes, put it into master.  You won't damage anything.

---

### Post by Ndyanabo on 2009-10-13
anyway, az, I run the command, then power up the drive. No message!

---

### Post by lavinog on 2009-10-13
what is the order that you are connecting everything?
adapter to drive, turn on power, then plug in usb?

---

### Post by Ndyanabo on 2009-10-13
lavinog, good point. Was plugging everything in, then powering up.

here's what I got when I disconnected, powered up, reconnected:

> Oct 13 10:52:01 pemba kernel: [ 9281.868911] usb 1-9.5: USB disconnect, address 8
Oct 13 10:52:28 pemba kernel: [ 9308.948706] usb 1-9.5: new high speed USB device using ehci_hcd and address 9
Oct 13 10:52:28 pemba kernel: [ 9309.043457] usb 1-9.5: configuration #1 chosen from 1 choice
Oct 13 10:52:28 pemba kernel: [ 9309.054099] scsi14 : SCSI emulation for USB Mass Storage devices
Oct 13 10:52:33 pemba kernel: [ 9314.059839] scsi 14:0:0:0: Direct-Access     Maxtor 3 1024H1           14Y0 PQ: 0 ANSI: 2 CCS
Oct 13 10:52:33 pemba kernel: [ 9314.066065] sd 14:0:0:0: [sdm] 19531250 512-byte hardware sectors: (10.0 GB/9.31 GiB)
Oct 13 10:52:33 pemba kernel: [ 9314.067678] sd 14:0:0:0: [sdm] Write Protect is off
Oct 13 10:52:33 pemba kernel: [ 9314.068426] sd 14:0:0:0: [sdm] 19531250 512-byte hardware sectors: (10.0 GB/9.31 GiB)
Oct 13 10:52:33 pemba kernel: [ 9314.070686] sd 14:0:0:0: [sdm] Write Protect is off
Oct 13 10:52:33 pemba kernel: [ 9314.070701]  sdm: sdm1
Oct 13 10:52:33 pemba kernel: [ 9314.132531] sd 14:0:0:0: [sdm] Attached SCSI disk
Oct 13 10:52:33 pemba kernel: [ 9314.132691] sd 14:0:0:0: Attached scsi generic sg13 type 0


---

### Post by Ndyanabo on 2009-10-13
SOLVED!
not sure why, but I got it to mount. I did remove the jumper, but that shouldn't matter. I guess plugging it in powered up helped too. Is that standard operating procedure?

thanks everyone for the help! Helping my step mother get away from ME. Another win for the good guys!

---

### Post by lavinog on 2009-10-13
My usb adapter needs the drive connected and powered up before connecting the usb connector.

---

### Post by az on 2009-10-13
> **Ndyanabo said:**
> SOLVED!
not sure why, but I got it to mount. I did remove the jumper, but that shouldn't matter. 

Your usb cable needed the drive to be in a certain mode for it to be able to use it.  Removing the jumper put it into a mode that it could use.

---

