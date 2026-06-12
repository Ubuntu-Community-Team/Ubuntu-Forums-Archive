---
title: "Random &quot;Cannot read from resource&quot; and unmounts of USB stick"
date: 2009-02-04
forum: New to Ubuntu
---

### Post by meindian523 on 2009-02-04
So I have a USB Stick Transcend JF V30 4 GB and I copy stuff to it.Just to check out whether everything got copied all right,I tried opening a song in Totem,which plays all right,but at random positions errors out with "Resource not found" or "Cannot read from Resource".Similarly,I open a few pictures in Eye of Gnome,the image viewer,while some files display fine,others jump out with "Input/Output error"

I can't think of this being the fault of the USB stick,because it's brand new,and it's a replacement for another stick under warranty,which displayed similar behavior and even more exceptional behavior like GParted not being able to delete partitions on it,formatting via GParted[it gives an Input/Output error] and Nautilus scripts not working,and randomly turning to read only on Ubuntu,Vista and XP on different machines.Even zeroing out the entire stick with **dd** [!!] didn't work on the previous stick,and I could listen to tracks on the previous stick **after** zeroing completed,albeit with errors mentioned above.(I haven't tried formatting or deleting partitions on the new stick.)

I can't imagine that a flash drive can be Windows-only,because it's simply another storage medium.I may be wrong though.Therefore I'm suspecting DBus and HAL not being able to handle USB sticks,and somehow affecting them to give errors.

The file system is FAT32,and I would like a solution to this problem.Thanks for reading this long winded post,and hoping for a solution.

---

### Post by apjone on 2009-02-04
Anything usefull in dmesg?

---

### Post by meindian523 on 2009-02-04
Thanks for replying.:)
About dmesg,I didn't check it as soon as the errors occurred.I'll try and get back.

---

### Post by meindian523 on 2009-02-04
```
[15407.096040] usb 3-7: reset high speed USB device using ehci_hcd and address 4
[15407.229869] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[15407.229883] end_request: I/O error, dev sdb, sector 11129
[15407.230846] end_request: I/O error, dev sdb, sector 11218
[15407.233347] FAT: FAT read failed (blocknr 2937)
[15407.260376] FAT: FAT read failed (blocknr 2937)
[15407.936713] sd 7:0:0:0: [sdb] 7843840 512-byte hardware sectors (4016 MB)
[15407.937991] sd 7:0:0:0: [sdb] Write Protect is off
[15407.937999] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[15407.938003] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[15421.935103] sd 7:0:0:0: [sdb] 7843840 512-byte hardware sectors (4016 MB)
[15421.937849] sd 7:0:0:0: [sdb] Write Protect is off
[15421.937861] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[15421.937865] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[15421.940040]  sdb: sdb1

```
That's dmesg when I mount it.Somehow two folders I copied into the flash drive are completely empty when I checked now.The following is,I guess,the relevant dmesg
```
[15200.389867] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[15200.390314] sd 7:0:0:0: Attached scsi generic sg2 type 0
[15270.336038] usb 3-7: reset high speed USB device using ehci_hcd and address 4
[15270.469781] sd 7:0:0:0: [sdb] Result: hostbyte=DID_ERROR driverbyte=DRIVER_OK,SUGGEST_OK
[15270.469793] end_request: I/O error, dev sdb, sector 11001
[15270.473407] end_request: I/O error, dev sdb, sector 11129
[15270.855902] FAT: FAT read failed (blocknr 2810)
[15270.964402] FAT: Directory bread(block 1647056) failed
[15270.964912] FAT: Directory bread(block 1647057) failed
[15270.965848] FAT: Directory bread(block 1647058) failed
[15270.966776] FAT: Directory bread(block 1647059) failed
[15270.967706] FAT: Directory bread(block 1647060) failed
[15270.968655] FAT: Directory bread(block 1647061) failed
[15270.969593] FAT: Directory bread(block 1647062) failed
[15270.970521] FAT: Directory bread(block 1647063) failed
[15270.977764] FAT: FAT read failed (blocknr 4297)
[15270.978002] FAT: FAT read failed (blocknr 4297)
[15270.978201] FAT: FAT read failed (blocknr 4297)
[15270.978398] FAT: FAT read failed (blocknr 4297)
[15270.978593] FAT: FAT read failed (blocknr 4297)
[15270.978788] FAT: FAT read failed (blocknr 4297)
[15270.978983] FAT: FAT read failed (blocknr 4297)
[15270.979178] FAT: FAT read failed (blocknr 4297)
[15270.979379] FAT: FAT read failed (blocknr 4297)
[15270.979400] FAT: FAT read failed (blocknr 4297)
[15270.979415] FAT: FAT read failed (blocknr 4297)
[15270.979429] FAT: FAT read failed (blocknr 4297)
[15270.979443] FAT: FAT read failed (blocknr 4297)
[15270.979456] FAT: FAT read failed (blocknr 4297)
[15270.979469] FAT: FAT read failed (blocknr 4297)
[15270.979482] FAT: FAT read failed (blocknr 4297)
[15270.979494] FAT: FAT read failed (blocknr 4297)
[15270.979507] FAT: FAT read failed (blocknr 4297)
[15270.979525] FAT: FAT read failed (blocknr 4297)
[15270.979558] FAT: FAT read failed (blocknr 4297)
[15270.979573] FAT: FAT read failed (blocknr 4297)
[15270.979586] FAT: FAT read failed (blocknr 4297)
[15270.979599] FAT: FAT read failed (blocknr 4297)
[15270.979612] FAT: FAT read failed (blocknr 4297)
[15270.979625] FAT: FAT read failed (blocknr 4297)
[15270.979638] FAT: FAT read failed (blocknr 4297)
[15270.979651] FAT: FAT read failed (blocknr 4297)
[15271.135122] FAT: FAT read failed (blocknr 2810)
[15271.165078] FAT: FAT read failed (blocknr 2810)
[15271.933881] sd 7:0:0:0: [sdb] 7843840 512-byte hardware sectors (4016 MB)
[15271.934761] sd 7:0:0:0: [sdb] Write Protect is off
[15271.934765] sd 7:0:0:0: [sdb] Mode Sense: 03 00 00 00
[15271.934768] sd 7:0:0:0: [sdb] Assuming drive cache: write through
[15281.945047] FAT: Corrupted directory (i_pos 42774787)
[15285.388449] FAT: Corrupted directory (i_pos 42774787)
[15286.462495] FAT: Corrupted directory (i_pos 42774787)
[15311.310072] FAT: Corrupted directory (i_pos 42774787)
[15322.132295] FAT: Corrupted directory (i_pos 42774787)

```
For the record,directories didn't corrupt on the previous stick.

---

### Post by meindian523 on 2009-02-04
Also,I cant delete(in the sense,move to Trash) any files.a dialog pops up saying > Unable to create trashing info file: Input/output error with Cancel,Skip,and Delete.Delete does the requivalent of Shoft+Delete,that is permanent deletion.

---

### Post by meindian523 on 2009-02-04
looks like directory ```
i_pos 42774787
``` is the .Trash/info directory,because the same entry occurred when trying to delete another file for the purposes of posting the error.

---

### Post by apjone on 2009-02-04
Hey sorry for slow reply still in work. Saw this thread [http://ubuntuforums.org/showthread.php?t=666292](http://ubuntuforums.org/showthread.php?t=666292) that suggests formating the Drive as FAT32 from a Windows install may help. Strange problem...................

---

### Post by meindian523 on 2009-02-04
It apparently seems the OP in the thread you linked to had filesystem panic.I don't seem to have that problem.And I haven't formatted this stick ever,it's the FAT32 it came formatted with.Also,I'm using Ubuntu 8.10 64 bit,if that's of any help.

And,unfortunately in this case,I've long deleted my Windows XP partition. :( :P

---

