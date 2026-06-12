---
title: "recover files after unsafe usb unmount?"
date: 2008-12-06
forum: New to Ubuntu
---

### Post by minsf on 2008-12-06
hi,

please forgive my being such a newbie- first time i use my usb stick in linux.

i did not unmount the usb stick safely-is there any way to recover my file?

more details:
i moved a file from one folder to the other on the usb stick using the ctrl-x ctrl-v in Nautilus. i forgot to unmount the usb safely- i just pulled it out. how silly. i didn't even realised that this is a problem, so i restarted the computer... now the file appears back in the original folder but has 0KB. so sad...
any chance something like sync or fsck can still help?

also, just out of curiosity, if i had not restarted, could i have restored the file?

thanks in advance for ur advice

---

### Post by taseedorf on 2008-12-10
hmm...weird, ive never had that problem......but there MAY be some files left over in your HD...check wherever your computer mounts your usb drive...

probably in a folder in /media/

---

### Post by theozzlives on 2008-12-10
> **minsf said:**
> hi,

please forgive my being such a newbie- first time i use my usb stick in linux.

i did not unmount the usb stick safely-is there any way to recover my file?

more details:
i moved a file from one folder to the other on the usb stick using the ctrl-x ctrl-v in Nautilus. i forgot to unmount the usb safely- i just pulled it out. how silly. i didn't even realised that this is a problem, so i restarted the computer... now the file appears back in the original folder but has 0KB. so sad...
any chance something like sync or fsck can still help?

also, just out of curiosity, if i had not restarted, could i have restored the file?

thanks in advance for ur advice

fsck might take care of the lost clusters for you but you can't use it on a mounted filesystem... try the live CD.

---

### Post by carusoswi on 2008-12-10
> **minsf said:**
> hi,

please forgive my being such a newbie- first time i use my usb stick in linux.

i did not unmount the usb stick safely-is there any way to recover my file?

more details:
i moved a file from one folder to the other on the usb stick using the ctrl-x ctrl-v in Nautilus. i forgot to unmount the usb safely- i just pulled it out. how silly. i didn't even realised that this is a problem, so i restarted the computer... now the file appears back in the original folder but has 0KB. so sad...
any chance something like sync or fsck can still help?

also, just out of curiosity, if i had not restarted, could i have restored the file?

thanks in advance for ur advice

So, when you mount the usb stick, what shows up?  Can you mount it?
If not, I would try mounting it on a Windows machine.  Frequently, crashes or other unclean shutdowns cause this problem with my usb external hard drives.  Starting XP and mounting them there generally clears up the problem, and data remains in tact.

Good luck.

Caruso

---

### Post by madverb on 2008-12-10
Never hurts to use testdisk
It may be possible that the file is on the usb drive. I've used testdisk to recover many usb drives lost filesystems or just recovering files.

---

### Post by philinux on 2008-12-10
What's the file system type on the stick, ext3 or ntfs etc?

---

### Post by minsf on 2008-12-13
First, thank you all for replying; after a week with no reply i almost gave up on this thread :)
The usb stick seems to be mounted properly at media/disk.
Its file system seems to be FAT16...
(I should probably change it as soon as i can to ext3, right? how do i do it- backup the files and format it?)
here's what lshw gave me:
           *-volume
                description: Windows FAT volume
                vendor: *rIVMIHC
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sdb1
                logical name: /media/disk
                version: FAT16
                serial: ----------
                size: 125MiB
                capacity: 125MiB
                capabilities: primary bootable fat initialized
                configuration: FATs=2 filesystem=fat mount.fstype=vfat mount.options=rw,nosuid,nodev,uid=1000,fmask=0077,dmask=0077,codepage=cp437,iocharset=iso8859-1,shortname=mixed,utf8,flush state=mounted

---

